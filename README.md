# DDEV-cypress <!-- omit in toc -->

- [Introduction](#introduction)
- [Requirements](#requirements)
- [Steps](#steps)
- [Commands](#commands)
  - [`cypress-open`](#cypress-open)
  - [`cypress-run`](#cypress-run)

## Introduction

[Cypress](https://www.cypress.io/) is a "complete end-to-end testing experience". It allows you to write Javascript test files that automate real browsers.  For more details, see the [Cypress Overview](https://docs.cypress.io/guides/overview/why-cypress) page.

This recipe integrates a Cypress docker image with your DDEV project.

## Requirements

- DDEV >= 1.19
- Modern OS
  - macOS 10.9 and above (Intel or Apple Silicon 64-bit (x64 or arm64))
  - Linux Ubuntu 12.04 and above, Fedora 21 and Debian 8 (x86_64 or Arm 64-bit (x64 or arm64))
  - Windows 7 and above (64-bit only)
- Interactive mode requires a X11 server running on the host machine.

## Steps

- Install service

  ```shell
  ddev get msuthars/ddev-cypress
  ddev restart
  ```

- Run cypress via `ddev cypress-open` or `ddev cypress-run` (headless).

It is recommended to run `ddev cypress-open` first to create configuration and support files.
This addon sets `CYPRESS_baseUrl` to DDEV's primary URL in the `docker-compose.cypress.yaml`.

## Commands

Cypress can run into 2 different modes: interactive and runner.
This recipe includes 2 alias commands to help you use Cypress.

To see Cypress in interactive mode, Cypress forward XVFB messages out of the Cypress container into an X11 server running on the host machine. There are many options depending on your OS. User have reported success with the following:

- Windows 10 / WSL users:
  - [GWSL](https://opticos.github.io/gwsl/tutorials/manual.html) (via [Microsoft store](ms-windows-store://pdp/?productid=9NL6KD1H33V3))
  - [VcXsrv](https://sourceforge.net/projects/vcxsrv/) (via [chocolatey](https://community.chocolatey.org/packages/vcxsrv#versionhistory)).
- Mac users:
  - [XQuartz](https://www.xquartz.org/). See [Running GUI applications using Docker for Mac](https://sourabhbajaj.com/blog/2017/02/07/gui-applications-docker-mac/).

### `cypress-open`

To open cypress in "interactive" mode, run the following command:

```shell
ddev cypress-open
```

This command also accepts arguments. Refer to the ["#cypress open" documentation](https://docs.cypress.io/guides/guides/command-line#cypress-open) for further details.

Example: To open Cypress in interactive mode, and specify a config file

```shell
ddev cypress-open --config cypress.json
```

### `cypress-run`

To run Cypress in "runner" mode, run the following command:

```shell
ddev cypress-run
```

This command also accepts arguments. Refer to [#cypress run](https://docs.cypress.io/guides/guides/command-line#cypress-run) page for a full list of available arguments.

Example: To run all Cypress tests, using Chrome in headless mode

```shell
ddev cypress-run --browser chrome
```
