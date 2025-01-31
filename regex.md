# Regex

Regular expressions are a core skill for any half decent programmer.

I use them extensively in languages from Python and Perl to Java/Scala/Groovy and even in shell scripts in Bash
for grep, sed & awk.

<!-- INDEX_START -->

- [Online Regex Testing](#online-regex-testing)
  - [Sed Regex Testing](#sed-regex-testing)
- [PCRE vs BRE vs ERE](#pcre-vs-bre-vs-ere)
  - [PCRE - Perl Compatible Regular Expressions](#pcre---perl-compatible-regular-expressions)
- [BRE - Basic Regular Expression](#bre---basic-regular-expression)
- [ERE - Extended Regular Expressions](#ere---extended-regular-expressions)
- [Core Reading](#core-reading)
- [Library of Regex in Perl](#library-of-regex-in-perl)
- [Library of Regex in Python](#library-of-regex-in-python)
- [Library of Regex in Bash](#library-of-regex-in-bash)
- [Examples of Real-world Regex Used Extensively](#examples-of-real-world-regex-used-extensively)

<!-- INDEX_END -->

## Online Regex Testing

<https://regex101.com/>

<https://regexr.com/>

### Sed Regex Testing

Test your sed regex here:

<https://sed.js.org/>

## PCRE vs BRE vs ERE

### PCRE - Perl Compatible Regular Expressions

The gold standard from [Perl](perl.md) which most popular languages aspire to

GNU grep has a `grep -P` switch to use PCRE but beware it's not portable. It won't work on BSD based systems like macOS.

On Mac you can install coreutils to get the better GNU Grep

```shell
brew install coreutils
```

but then you'll have to use the `ggrep` command instead.

Your shell scripts will have to figure our if they're on Mac and override the grep command (examples in
[DevOps-Bash-tools](https://github.com/nholuongut/devops-bash-tools) repo).

## BRE - Basic Regular Expression

This is the neutered regex that old grep uses.

## ERE - Extended Regular Expressions

Slightly better than BRE but still weak & awkward compared to PCRE.

Don't support back references.

Grep on most systems can support EREs via the `grep -E` switch.

Awk also uses EREs.

## Core Reading

[Master Regular Expressions](https://www.amazon.com/Mastering-Regular-Expressions-Jeffrey-Friedl/dp/0596528124/)

## Library of Regex in Perl

PCRE regex:

[nholuongut/lib](https://github.com/nholuongut/lib)

## Library of Regex in Python

PCRE regex:

[nholuongut/pylib](https://github.com/nholuongut/pylib)

## Library of Regex in Bash

BRE / ERE Regex:

[nholuongut/devops-bash-tools](https://github.com/nholuongut/devops-bash-tools)

## Examples of Real-world Regex Used Extensively

PCRE regex - see especially anonymize.py / anonymize.pl in these repos among many other scripts:

[nholuongut/DevOps-Python-tools](https://github.com/nholuongut/DevOps-Python-tools)

[nholuongut/DevOps-Perl-tools](https://github.com/nholuongut/DevOps-Perl-tools)

[nholuongut/Nagios-Plugins](https://github.com/nholuongut/Nagios-Plugins)

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=nholuongut&repo=DevOps-Python-tools&theme=ambient_gradient&description_lines_count=3)](https://github.com/nholuongut/DevOps-Python-tools)

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=nholuongut&repo=DevOps-Perl-tools&theme=ambient_gradient&description_lines_count=3)](https://github.com/nholuongut/DevOps-Perl-tools)

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=nholuongut&repo=Nagios-Plugins&theme=ambient_gradient&description_lines_count=3)](https://github.com/nholuongut/Nagios-Plugins)
