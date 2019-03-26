# State Space, Tooling
This repository contains the operability tooling for the State Space implementation of the IAB PrivacyChain Reference Design.
This is tooling for State Space Implementation of the IAB PrivacyChain Reference Design.
It comprises loaders, dumpers and debugging machinery, nearly all of which are cli-oriented and script-kid focused.

![banner](logo.png)

More detailed information can be found at the following locations
about the scope and purpose of the State Space implementation of the IAB PrivacyChain Reference Design.
* [State Space](https://github.com/yahoo/statespace)
* [IAB PrivacyChain](https://github.com/InteractiveAdvertisingBureau/PrivacyChain/blob/master/README.md) Reference Design.

[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)

## Table of Contents

- [Background](#background)
- [Install](#install)
- [Configuration](#configuration)
- [Usage](#usage)
- [Security](#security)
- [Contribute](#contribute)
- [License](#license)

## Background

This project contains the offline and batch tools necesary to maintain the PrivacyChain database replicas.  These are at least:
* backing the ledger
* dumping the ledger
* ad hoc database maintenance

## Install

This project is not independent. It expects to be configured as a submodule of [State Space](https://github.com/yahoo/statespace).  This should happen naturally in the course of the git submodule activation procedure.

To install the test code independently of its status as a submodule of State Space, run the following command:

```
git clone https://github.com/yahoo/statespace-tooling.git
```

This will create a directory called `statespace-tooling` and download the contents of this repo to it.

## Configuration

The following commands will configure the respository.  Individual test scenarios may have further configuration to operate them.

```
./buildconf &&
./configure &&
make all &&
make check &&
make install
```

## Usage

The command line tools produced in the build process each have their own `--help` options and an associated manual page which is created by `help2man`.  For example the tool privacy chain database query tool `pct` has `pct --help`.

## Security

This project does not have any security concerns directly.  The tools produced by this project provide the means to interact with the PrivacyChain database.  For those having access to the database replicas directly, access to these tools will allow individuals to manipulate the database structures (the ledger) directly.  Care should be taken to provide such access only to the appropriate operational roles.

## Contribute

Please refer to [the contributing.md file](Contributing.md) for information about how to get involved. We welcome issues, questions, and pull requests. Pull Requests are welcome.

## Maintainers
Wendell Baker <wbaker@verizonmedia.com>

## License

This project is licensed under the terms of the [Apache 2.0](LICENSE-Apache-2.0) open source license. Please refer to [LICENSE](LICENSE) for the full terms.
