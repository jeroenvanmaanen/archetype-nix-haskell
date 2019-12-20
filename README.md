# Test Haskell with Nix

```
$ docker build --tag jeroenvm/nix .
$ docker run -ti -v "${HOME}:${HOME}" -w "$(pwd)" jeroenvm/nix
$ nix-shell -p "haskellPackages.ghcWithPackages (pkgs: [pkgs.http2-grpc-proto-lens])"
[nix-shell:~/.nix-defexpr]# ghci
Prelude> import Network.GRPC.HTTP2.ProtoLens

$ nix-shell --pure shell.nix
Prelude> import Network.HTTP2.Client
```

## Scratch

```
NIX_PATH='/nix/var/nix/profiles/per-user/root/channels' nix-env -f "<nixpkgs>" -iA haskellPackages."http2-grpc-proto-lens"
```
