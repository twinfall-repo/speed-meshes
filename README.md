# speed-meshes

The meshes of the SPEED runs of [speed-simu](https://github.com/twinfall-repo/speed-simu),
compressed with zstd and stored in Git LFS. speed-simu has this repository as
the submodule `data/meshes`; its `run_case.sh` unpacks `<name>.mesh.zst` into
`<name>.mesh` next to it (ignored here) the first time a case uses it, and
again whenever the `.zst` is newer.

Cloning needs `git-lfs` (`git lfs install` once); without it the `.zst` files
are LFS pointers of a few bytes.

## A new mesh

```bash
zstd -T0 -19 my_mesh.mesh -o my_mesh.mesh.zst
git add my_mesh.mesh.zst && git commit -m "Add my_mesh" && git push
```

then, in speed-simu, `git -C data/meshes pull` and commit the new submodule
commit.
