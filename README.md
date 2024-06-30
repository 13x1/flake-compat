# flake-compat

## About

This is a compatibility layer for flakes, allowing users to use your
flake without having flakes enabled, and also allows the older commands
like `nix-build` or `nix-shell` to work with a flake.

## Usage

To use, create a Nix file file containing the following code:

```nix
import (fetchGit {
  url = "https://github.com/13x1/flake-compat";
  rev = "da05cf0205cc3cea9785a17c0a3c1a1bf9784302";
}) ./default.nix # replace with current filename
```

You can choose any name (and the file can be in any directory in your flake).
`default.nix` should be used for `nix-build`, and `shell.nix` for `nix-shell`.
If you only want to support inputs from non-flakes, any name is fine.

## Changes in this fork

- *Less boilerplate*: The `default.nix` files you have to put in your repo are not 9 lines
  of boilerplate anymore.
- *Remove the empty flake*: You don't have to add an empty input from DetSys anymore.
  Reading the lockfile manually was a hack and required you to depend on FlakeHub,
  and yet edolstra's repo was still hardcoded in the default.nix boilerplate.
  Updating doesn't make sense either, because the default.nix would have to be changed too.