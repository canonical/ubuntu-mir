# Allowed Words

The `*.txt` files contained in this directory extend the dictonary provided by 
[`check-spelling`](https://github.com/check-spelling/check-spelling).

Add new words to the respective categories. Feel free to recategorize the words 
if you come up with a better system.

## Files

**Note:** The file entries are sorted alphabetically (this makes it easier to see if an entry is present/missing). The default minimum word size is 3 characters and the only characters it considers are `a-z` and `'` (as a regular expression `^[a-z']{3,}$`). *This may change in future versions.*

| File | Description |
| ---- | ----------- |
| [architectures](architectures.txt) | architecture identifiers like `riscv`  |
| [canonical](canonical.txt) | words/terms related to Canonical, like internal systems or products |
| [contributors](contributors.txt) | usernames of contributors (that show up in the [`README.md`](../../../../README.md))  |
| [debian](debian.txt) | debian related terms like `sid` |
| [formats](formats.txt) | names of programming languages, file formats and protocols (e.g. `http`, `golang`, `jpeg`) |
| [linux](linux.txt) | general `linux` related terms (e.g. directory names of [FHS](https://refspecs.linuxfoundation.org/fhs.shtml)) |
| [misc](misc.txt) | actual\* words/terms that do not fit in the other category |
| [software](software.txt) | names of applications / binaries / services (e.g. `sbuild`, `libjpeg`, `jira`) |
| [ubuntu-codenames](ubuntu-codenames.txt) | Ubuntu codenames (e.g. `mantic`) |
| [ubuntu-flavors](ubuntu-flavors.txt) | Ubuntu flavor names (e.g. `edubuntu`) |
| [ubuntu-misc](ubuntu-misc.txt) | other Ubuntu related words/terms that do not fit in the other categories |

\* **Note:** There also exists the [`expect.txt`](../expect.txt) file for words that have to be accepted to pass the spell-checker but are no actual words/terms. Words/Terms contained in this file will get suggested for removal as soon as they are no longer used in the repository.

See more information on how to use the `allow` files in the [official documentation](https://github.com/check-spelling/check-spelling/wiki/Configuration#allow) of the [`check-spelling`](https://github.com/check-spelling/check-spelling) action.
