# Sunstack security patch

This fork starts from `micromatch/braces` commit
`e53730e6f935498326c72d768889ac194eedc0e0` (`3.0.3`) and applies the
reviewed depth-limit changes from the closed upstream pull request
[`micromatch/braces#72`](https://github.com/micromatch/braces/pull/72), head
`28d440b5dd449dbf1fe6f3506cf94ecca4d02660`.

The `3.0.4-sunstack.1` version identifies the patched source. It is not an
official upstream release. The patch bounds nested brace and parenthesis
parsing and recursive AST processing at 100 levels, while retaining caller
options that choose a smaller limit. The upstream pull request also guards
cyclic parent chains in expansion and adds regression coverage for normal
patterns and `escapeInvalid` behavior.

The Recovery Platform pins a Git commit of this fork as a transitive npm
override. Re-run this fork's test suite and the platform's mobile tests and
dependency audit before changing that pin. Replace the override with an
official maintained release once it includes equivalent protections and the
platform's compatibility checks pass.
