# picom-allusive
A Fork of Pijulius picom by Allusive.

Want to support my work or just ask a personal question? DM me and let's chat.


[![Matrix](https://img.shields.io/badge/MATRIX-012121.svg?style=for-the-badge&logo=Matrix&logoColor=white)](https://matrix.to/#/@allusive_:matrix.org)
[![Discord](https://img.shields.io/badge/DISCORD-5865F2.svg?style=for-the-badge&logo=Discord&logoColor=white)](https://github.com/allusive-dev/allusive-dev#contact-me)
[![Email](https://img.shields.io/badge/EMAIL-160F33.svg?style=for-the-badge&logo=ProtonMail&logoColor=white)](mailto:jasper@allusive.dev)

## What Is This?
This is a fork of picom-pijulius which is avaliable on Nixpkgs and the Arch User Repository.

This is currently the best actively maintained fork of picom adding proper animations.


## Documentation can be found in the Wiki tab above.

The docs were moved back to Github Wiki because the documentation framework I was using is actually pretty slow and unoptimized so for now things are back to the way they were.

Can't find what you need in the wiki or have an problem? Open an Issue.

## Installation

### Building Manually
```
$ meson setup --buildtype=release . build
$ ninja -C build
$ ninja -C build install
```

### Arch Linux or other Arch based distros
```
$ paru -S picom-allusive
```
or
```
$ yay -S picom-allusive
```

### NixOS

picom-allusive is now avaliable on unstable(23.11)!

Keep in mind it can take up to a week after picom is updated before it wil be avaliable on NixOS.

Simply do one of the following
``` nix
environment.systemPackages = [ pkgs.picom-allusive ];
```
or for home-manager
``` nix
home.packages = [ pkgs.picom-allusive ];
```

The package will not be avaliable on NixOS 23.05 You will have to wait until the next stable update if you are on the stable branch.

If you still want to use picom and you are on 23.05 you can use this custom package in either `environment.systemPackages` or `home.packages` for home-manager users. Keep in mind this is considerably unstable so expect possible issues. 

``` nix
      (picom.overrideAttrs (oldAttrs: rec {
        pname = "picom-allusive";
        version = "0.3.2";
        src = pkgs.fetchFromGitHub {
          owner = "allusive-dev";
          repo = "picom-allusive";
          rev = version;
          hash = "sha256-1zWntz2QKp/O9ZuOUZy9NkCNXFsBqRRvcd0SAr+7G/o=";
        };
        postInstall =
          ''
            chmod +x $out/bin/picom-trans
          ''
          + oldAttrs.postInstall;
      }))
    ];
```

Thank you for your patience.
