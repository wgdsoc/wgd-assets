# The WGD Asset Repository

This repository is an asset storage, contribution, and retrieval location for the Warwick Game Design Society. This should future-proof the inevitable WGD website redesigns (or perhaps third time's the charm... or more, we haven't really kept track). It acts as a framework-agnostic asset directory and can be added, without caveats, as a git submodule to any relevant repository.

## Organisation

This repository is organised in a slightly unusual way:

- `lfs/` tracks all 'binary' files (.png, .pdf, etc.)
- `src/` tracks all 'plaintext' files (.tex, .typ, .bib, etc.)

If you are familiar with [git-lfs](https://git-lfs.com/), you might have guessed the advantages of organising the repository in this way. Everything in `lfs/` is tracked by git-lfs (large file storage) which tracks pointers to files which git is incapable of compressing. Git-lfs ensures that you only keep one version of the files on your computer to avoid massive bloat.

Meanwhile, git tracks the `src/` directory. File type gatekeeping in the `src/.gitignore` ensures that only compressible (usually plaintext) files are stored here. Any change to `src/.gitignore` to include a new type, like .md or .txt will be scrutinised.

## Development

You will need [git-lfs](https://git-lfs.com/); install as per the website's instructions. PRs are encouraged from any member or executive in the society. You may add as many untracked auxiliary and binary files to `src/` as you wish while developing a new asset.

Make sure to commit any relevant binary file as infrequently as possible to minimise cloud storage usage. PRs with commits containing excessively numerous binary file versions in `lfs/` are likely to be compressed into one commit when merged.

Directory reshuffles in `lfs/` will be heavily scrutinised and likely refused. This is because other repositories and `src/` itself will fundamentally depend on static file locations in `lfs/` (e.g., `src/tutorials/godot-basics/flappy-bird/main.tex` depends on `lfs/tutorials/godot-basics/*`). This policy is thus an unfortunate (but necessary) side effect of the tight coupling, which becomes hugely advantageous when used as a git submodule.

As with the above example, it is strongly encouraged to place binary files in `lfs/` where they are required by files in `src/`. If this is not done, other contributors will not be able to compile your `src/` files themselves. See further instructions for this in various `README.md` files in relevant `src/` subdirectories.

## Questions

For now, ask on our Discord server. If a bug is suspected, file an issue.
