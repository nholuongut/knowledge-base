# Dockerfile

NOT PORTED YET

The build file for a docker image.

<!-- INDEX_START -->

- [Template](#template)
- [nholuongut/dockerfiles](#nholuongutdockerfiles)
- [Amazing Cache Busting Trick](#amazing-cache-busting-trick)
- [Python - Create Smaller Docker Images Using the Builder Pattern](#python---create-smaller-docker-images-using-the-builder-pattern)

<!-- INDEX_END -->

## Template

[nholuongut/templates - Dockerfile](https://github.com/nholuongut/templates/blob/master/Dockerfile)

## nholuongut/dockerfiles

Large repo full of Dockerfiles for different open source technologies full of real world tricks like DockerHub auto-hook
scripts to do extra tags, cache busting upon new commits to GitHub repos etc.

:octocat: [nholuongut/dockerfiles](https://github.com/nholuongut/dockerfiles)

## Amazing Cache Busting Trick

If you're building from GitHub repos that you want to trigger rebuilds upon any change by busting the Docker build cache
you can put this in your Dockerfile:

```dockerfile
# Cache Bust upon new commits
ADD https://api.github.com/repos/nholuongut/devops-bash-tools/git/refs/heads/master /.git-hashref
```

I used this in my [nholuongut/dockerfiles](https://github.com/nholuongut/dockerfiles) repo for several of my major
GitHub repos like [DevOps-Bash-tools](devops-bash-tools.md) and [DevOps-Python-tools](devops-python-tools.md).

## Python - Create Smaller Docker Images Using the Builder Pattern

Use the Python builder pattern to make small Python docker images, see
this [Medium article](https://medium.com/@nholuongut/docker-python-builder-pattern-to-reduce-docker-image-size-e78feee68295).

The code for this is in the Dockerfile template above.
