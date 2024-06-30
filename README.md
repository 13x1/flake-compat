# flake-compat

## About

This is a compatibility layer for flakes, allowing users to use your
flake without having flakes enabled, and also allows the older commands
like `nix-build` or `nix-shell` to work with a flake.

## Usage

To use, create a `default.nix` or `shell.nix` file containing the following:

```nix
import (fetchGit {
  url = "https://github.com/13x1/flake-compat";
  rev = "2dc53c70e0b2f1345c87de4721852914c32b777e";
}) ./default.nix # or ./shell.nix
```

## Changes in this fork

- *Less boilerplate*: The `default.nix` files you have to put in your repo are not 9 lines
  of boilerplate anymore.
- *Remove the empty flake*: You don't have to add an empty input from DetSys anymore.
  Reading the lockfile manually was a hack and required you to depend on FlakeHub,
  and yet edolstra's repo was still hardcoded in the default.nix boilerplate.
  Updating doesn't make sense either, because the default.nix would have to be changed too.