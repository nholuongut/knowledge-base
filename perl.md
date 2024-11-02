# Perl

Perl is a legend of programming languages.

Easily one of the fastest easiest most powerful imperative scripting languages, and legendary
for text processing and regular expressions.

It's the language of elite unix sysadmins, and much of unix tooling is built on it, including [Git](git.md).

<!-- INDEX_START -->

- [PCRE - Perl Compatible Regular Expressions](#pcre---perl-compatible-regular-expressions)
- [Core Reading](#core-reading)
- [Perl in-place fast file editing (like sed but more powerful)](#perl-in-place-fast-file-editing-like-sed-but-more-powerful)
- [DevOps Perl tools](#devops-perl-tools)
- [Shell scripts with Perl](#shell-scripts-with-perl)
- [Nagios Plugins in Perl](#nagios-plugins-in-perl)
- [Perl Library with Unit Tests](#perl-library-with-unit-tests)

<!-- INDEX_END -->

## PCRE - Perl Compatible Regular Expressions

PCRE has the gold standard of regex for decades and is the standard by which other languages are judged.

It's regex engine is faster and more advanced than Python's. You can see many examples where both are used in the
following GitHub repos:

- [DevOps-Perl-tools](https://github.com/nholuongut/DevOps-Perl-tools)
- [DevOps-Python-tools](https://github.com/nholuongut/DevOps-Python-tools)
- [Advanced Nagios Plugins Collection](https://github.com/nholuongut/Nagios-Plugins)

Bash / Grep style BRE / ERE - basic regular expressions / extended regular expressions are the poor man's version, and
awkward for serious usage. Still, you can see many examples of Bash / Grep BRE/ERE format regex usage in:

- [DevOps-Bash-tools](https://github.com/nholuongut/devops-bash-tools)

Even if you don't know Perl programming you should at least in-place editing of files as it's even more powerful than `sed`.

## Core Reading

[Programming Perl](https://www.amazon.com/Programming-Perl-Unmatched-processing-scripting/dp/0596004923/)

## Perl in-place fast file editing (like sed but more powerful)

```shell
perl -pi -e 's/OLD/NEW/g' *.txt *.yaml ...
```

## DevOps Perl tools

[nholuongut/DevOps-Perl-tools](https://github.com/nholuongut/DevOps-Perl-tools)

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=nholuongut&repo=DevOps-Perl-tools&theme=ambient_gradient&description_lines_count=3)](https://github.com/nholuongut/DevOps-Perl-tools)

## Shell scripts with Perl

Shell scripts using Perl and making it easier to install Perl libraries from CPAN.

[nholuongut/devops-bash-tools](https://github.com/nholuongut/devops-bash-tools)

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=nholuongut&repo=DevOps-Bash-tools&theme=ambient_gradient&description_lines_count=3)](https://github.com/nholuongut/devops-bash-tools)

## Nagios Plugins in Perl

[nholuongut/Nagios-Plugins](https://github.com/nholuongut/Nagios-Plugins)

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=nholuongut&repo=Nagios-Plugins&theme=ambient_gradient&description_lines_count=3)](https://github.com/nholuongut/Nagios-Plugins)

## Perl Library with Unit Tests

[nholuongut/lib](https://github.com/nholuongut/lib)

**Partial port from private Knowledge Base page 2009+**
