# build-ghc-no-omit-yields

Scripts for building binary distributions of GHC with -fno-omit-yields on `base` library

## Motivations

[The known bugs in GHC](https://downloads.haskell.org/~ghc/8.8.3/docs/html/users_guide/bugs.html#bugs-in-ghc)
states a potential case of deadlock, which could be resolved by compiling with `-fno-omit-yields`.

We want GHC to be terminated on programs like `last $ repeat 0` when a `SIGTERM` triggers, and thus
a recompiled `base` is required. However, since `base` is bundled with GHC, we have to recompile
GHC as a variant.

## References

- https://gitlab.haskell.org/ghc/ghc/-/wikis/building/preparation/linux#docker
- https://gitlab.haskell.org/ghc/ghc/-/wikis/building/hadrian
- https://gitlab.haskell.org/ghc/ghc/wikis/building/getting-the-sources