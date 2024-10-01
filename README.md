<!--README.md-->
<!--Author: D.A.Pelasgus-->

# Declerative Development Shells for Rust
## Nix & NixOS

 ```Nix
 let
    # Unstable Channel | Rolling Release
    pkgs = import (fetchTarball("channel:nixpkgs-unstable")) { };
    packages = with pkgs; [
      pkg-config
      webkitgtk_4_1
      libayatana-appindicator
      libappindicator-gtk3
    ];
  in
  pkgs.mkShell {
    buildInputs = packages;
  }
 ```

 > [!TIP]
 > A `shell.nix` is included in the subdirectory `etc/shells/nix`. Use as follows:
 ```sh
 nix-shell shell.nix
 ```

 ## Guix & GuixSD

 ```scheme
 (specifications->manifest
   '("pkg-config"                ; Helper tool used when compiling
     "webkitgtk"                 ; Web content engine fot GTK+
     "libappindicator"           ; Menu in Menu bar
     "gtk"
  ))
 ```

 > [!TIP]
 > A `manifest.scm` is included in the subdirectory `etc/shells/guix`. Use as follows:
 ```sh
 guix shell -m manifest.scm
 ```

 > [!WARNING]
 > Guix does not have the Ayatana package yet, so you need to use the GTK one, see the [feature flags documentation](https://docs.rs/wry/latest/wry/#feature-flags).
