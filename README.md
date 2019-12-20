# Archetype of a Haskell project built with Nix

```
$ docker build --tag jeroenvm/nix .
$ docker run -ti -v "${HOME}:${HOME}" -w "$(pwd)" jeroenvm/nix
$ nix-shell -p "haskellPackages.ghcWithPackages (pkgs: [pkgs.http2-grpc-proto-lens])"
[nix-shell:~/.nix-defexpr]# ghci
Prelude> import Network.GRPC.HTTP2.ProtoLens

$ nix-shell --pure shell.nix
Prelude> import Network.HTTP2.Client

$ nix-shell --pure -p cabal2nix --run "cabal2nix ." > default.nix
$ nix-build release.nix
$ result/bin/archetype-nix-haskell
```

## Scratch

```
NIX_PATH='/nix/var/nix/profiles/per-user/root/channels' nix-env -f "<nixpkgs>" -iA haskellPackages."http2-grpc-proto-lens"
```
