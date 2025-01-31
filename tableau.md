# Tableau

Tableau is a widely used visualization tool.

<https://www.tableau.com/>

<!-- INDEX_START -->

- [Tableau User Authentication](#tableau-user-authentication)
- [SSH Config](#ssh-config)
- [On the Tableau Server](#on-the-tableau-server)
- [Troubleshooting](#troubleshooting)
  - [Disk Space](#disk-space)
  - [Unable to proceed because of an error from the data source / Unable to connect to the Tableau Data Extract Server ""](#unable-to-proceed-because-of-an-error-from-the-data-source--unable-to-connect-to-the-tableau-data-extract-server-)

<!-- INDEX_END -->

## Tableau User Authentication

Can use LDAP integration.

Often this will use your short form username of first letter of first name followed by surname,
all lower case eg. for nho nho the username will be `hnho`.

| Admin UI Port |
|---------------|
| 8850          |

## SSH Config

Add this SSH config block to your `~/.ssh/config` to make SSH connections easier:

```sshconfig
cat >> ~/.ssh/config <<EOF
Host tableau
  TCPKeepAlive yes
  ServerAliveInterval 300
  HostName x.x.x.x
  IdentityFile ~/.ssh/tableau-ec2-user.pem
  User ec2-user
EOF
```

then you can use the shortened SSH form of just:

```shell
ssh tableau
```

## Tableau Server Administration

```shell
sudo su - tableauadmin
```

```shell
tsm status
```

output should look like:

```none
Status: RUNNING
```

Edit the `tableauadmin` user's crontab:

```shell
crontab -e
```

and put this in it to clean up disk space every midnight:

```crontab
0 0 * * * tsm maintenance cleanup -a
```

## Troubleshooting

### Disk Space

#### Logs

Logs were taking up 134GB out of 200GB root disk space causing disk full errors even on `tsm maintenance cleanup -a`
and `du | sort` type commands.

`/tmp` was only a few KB but clearing that allowed the few KB for `du | sort` to work again:

```shell
sudo rm -fr /tmp/*
```

Found that this deeply embedded log path `/var/opt/tableau/tableau_server/data/tabsvc/logs` was taking up the space
with 5500 log files.

Cleared logs older than 7 days to free up space:

```shell
find /var/opt/tableau/tableau_server/data/tabsvc/logs -type f -mtime +7 -exec rm -f {} \;
```

and added this cron to prevent it recurring:

```shell
0 0 * * * find /var/opt/tableau/tableau_server/data/tabsvc/logs -type f -mtime +7 -exec rm -f {} \;
```

but Tableau was still gave this next error in the web UI: `Unable to proceed because of an error from the data
source` / `Unable to connect to the Tableau Data Extract Server ""` (which previously used to work).

### Unable to proceed because of an error from the data source / Unable to connect to the Tableau Data Extract Server ""

Web UI still giving this error (used to work before out of disk space issue):

```none
Unable to proceed because of an error from the data source

Try connecting again. If the problem persists, disconnect from the data source and contact the data source owner.

Try again

Could not find Hyper hosts to connect to.
Unable to connect to the Tableau Data Extract Server "". Check that the server is running and that you have access privileges to the requested database.
```

Tableau server still had error:

```shell
tsm status
```

```none
The server encountered an unexpected error processing the request. Look at the server logs for more information.

See '/home/tableauadmin/.tableau/tsm/tsm.log' for more information.
```

```shell
tsm restart
```

```none
Stopping service...

Service failed to stop properly.


See '/home/tableauadmin/.tableau/tsm/tsm.log' for more information.

500 - Server Error
```

Had to kill processes, but can't do this at `tableauadmin` since the processes are owned by `tableau` user switch to
it from `ec2-user`:

```shell
sudo su - tableau
```

Do not `kill -9`, just regular `kill` to allow graceful termination and avoid risking data loss:

```shell
ps -ef |
grep '/tableau/tableau_server/' |
grep -v 'pgsql' |
awk '{print $2}' |
xargs kill
```

```shell
tsm stop
```

```shell
tsm start
```

```none
Starting service...
Starting service...
The last successful run of StartServerJob took 11 minute(s).

Job id is '21', timeout is 30 minutes.
```
