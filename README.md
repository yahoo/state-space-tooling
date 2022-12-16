# State Space, Tooling

This repository contains the operability tooling for the State Space reference implementation of the IAB PrivacyChain Technology Specification.
It comprises loaders, dumpers and debugging machinery, nearly all of which are command-line interface (cli-oriented) and script-kid focused.

The main body of documentation for the State Space reference implementation of the IAB PrivacyChain Technology Specification can be found with the [packaging](https://github.com/yahoo/state-space-packaging]).  The overview and administrative declarations herein are necessarily summary in nature. The declarations and definitions in the packaging area are complete and should be interpreted as superceding these when the two are in conflict.

More detailed information can be found at the following locations
about the scope and purpose of the State Space implementation of the IAB PrivacyChain Reference Design.
* [State Space](https://github.com/yahoo/state-space-packaging)
* [IAB PrivacyChain](https://github.com/InteractiveAdvertisingBureau/PrivacyChain/blob/master/README.md) Reference Design.

[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)

## Table of Contents

- [Background](#background)
- [Dependencies](#dependencies)
- [Installation](#installation)
- [Configuration](#configuration)
- [Build](#build)
- [Usage](#usage)
- [Security](#security)
- [Contribute](#contribute)
- [Maintainers](#maintainers)
- [License](#license)

## Background

This project contains the offline and batch tools necesary to maintain the PrivacyChain database replicas.  These are at least:
* backing up the database (ledger).
* dumping out the database (ledger).
* various <em>ad hoc</em> database maintenance operations.

Further details about that system can be found with the [overview](https://github.com/yahoo/state-space-packaging]) of the State Space project.

## Dependencies

The [configuration](#configuration) step will check for many but not all required packages and operating system features.  There is a list of known [package-dependencies](https://github.com/yahoo/state-space-tooling/blob/master/PACKAGES.md) which you will need to install beyond your base operating system.

Generally, the dependencies are among:
- The Hyperledger Fabric database and its Public Key Infrastructure (PKI) services.
- Various components of the Tunitas system; <em>e.g.</em> the [Basic Components](https://github.com/yahoo/tunitas-basic).
- A modern C++ development environment, meaning C++20 or C++23, C++2b where available.
- A recent Fedora, <em>e.g.</em>, Fedora 35 will suffice but any recent Linux distro should suffice.

The State Space project was developed on Fedora 27 through Fedora 34 using GCC.  At this juncture, GCC 12 is preferred, though GCC 11 is the minimum requirement.  Because the development started with GCC 7 &amp; GCC 8 using `-fconcepts` and `-std=c++1z`, there are still remnants of older compilers and older versions of C++ throughout the code base..  More details on the expected development environment and the build system can be found in [temerarious-flagship](https://github.com/yahoo/temerarious-flagship/blob/master/README.md).

## Installation

You may install this repo and its dependents by running the following command:

``` bash
git clone https://github.com/yahoo/state-space-tooling.git
```

This will create a directory called `state-space-tooling` and download the contents of this repo to it.

The expected application for the `state-space-tooling` repo is as a submodule of a larger build of the State Space reference implementation of IAB PrivacyChain Technology Specification.  The configuration, build, and installation intructions herein pertain only to maintenance operations on this repository.  The [configuration](https://github.com/yahoo/state-space-packaging/blob/master/README.md#Configuration) steps for the full project are with the [State Space packaging](https://github.com/yahoo/state-space-packaging).

The customary installation location for State Space reference implementation of the IAB PrivacyChain Specification is `/opt/iab/privacychain` but you may configure the build to use some other location.

## Configuration

The build system is based upon [GNU Autotools](https://www.gnu.org/software/automake/manual/html_node/index.html).

The configuration of the repo consists of two steps which must be done once.
1. `./buildconf`
2. `./configure`

The first step performs some crude assessments of the build environment and creates the site-specific `configure'. Of course `configure --help` will explain the build options.  The general options to `configure` are widely [documented](https://www.gnu.org/prep/standards/html_node/Configuration.html).

The `buildconf` component is boilerplate and can be updated from [temerarious-flagship](https://github.com/yahoo/temerarious-flagship/blob/master/bc/template.autotools-buildconf) as needed.  The [Tunitas Build System](https://github.com/yahoo/temerarious-flagship) should be available in `/opt/tunitas` and the template at `/opt/tunitas/share/temerarious-flagship/bc/template.autotools-buildconf`

## Build

The simplest configure-compile-install recipe is:

``` bash
./buildconf &&
./configure &&
make all &&
make check &&
make install &&
echo OK DONE
```

## Usage

The command line tools produced in the build process each have their own `--help` options and an associated documentation.  These are frequently is maintaned through the use of `help2man`.  For example the tool privacy chain database query tool `pct` is self-explanatory via `pct --help`.


### Database Primary Key Construction

Use `pck --help`

### Database Dump

Use `pcd --help`

### Database Administration CRUD

Use `pct --help`

## Security

This repo offers operability tooling in support of the State Space reference implementation of the IAB PrivacyChain Technology Specification. As such, this project does not have any direct security concerns.  The tools produced by this project provide the means to interact with the PrivacyChain database.  For those having access to the database replicas directly, access to these tools will allow individuals to manipulate the database structures (the ledger) directly.  Care should be taken to provide such access only to the appropriate operational roles (presenting as persons).

Please refer to the overall [Security Notice](https://github.com/yahoo/state-space-packaging/blob/master/README.md#Security) in the [lead repo](https://github.com/yahoo/state-space-packaging) of the State Space Project.

## Contribute

Please refer to the [contribution instructions](Contributing.md) for information about how to get involved. We welcome issues, questions. Pull Requests are welcome.

Current work with modern-generation tooling, <em>e.g.</em> circa Fedora 36+ and GCC 12+, is occurring around the <em>v0.1-themed</em> feature branches.
## Maintainers
- Wendell Baker <wbaker@yahooinc.com>
- The State Space Team at Yahoo <state-space@yahooinc.com>
- <strike>The [IAB PrivacyChain Engineering Working Group](https://iabtechlab.com/working-groups/blockchain-working-group/)</strike> is no longer active.

You may contact us at least at <state-space@yahooinc.com>

## License

This project is licensed under the terms of the [Apache 2.0](LICENSE-Apache-2.0) open source license. Please refer to [LICENSE](LICENSE) for the full terms.
