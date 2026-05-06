# Keystone Tool Index Stack Walkthrough

I use this file as a small checklist before changing the Python implementation.

| Case | Focus | Score | Lane |
| --- | --- | ---: | --- |
| baseline | file span | 158 | ship |
| stress | terminal width | 218 | ship |
| edge | argument risk | 149 | ship |
| recovery | report density | 214 | ship |
| stale | file span | 190 | ship |

Start with `stress` and `edge`. They create the widest contrast in this repository's fixture set, which makes them better review anchors than the middle cases.

The next useful expansion would be a malformed fixture around terminal width and report density.
