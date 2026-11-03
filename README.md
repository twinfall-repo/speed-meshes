# speed-meshes

Meshes of [speed-simu](https://github.com/twinfall-repo/speed-simu), its
submodule `data/meshes`: zstd-compressed, in Git LFS (needs `git-lfs`).
`run_case.sh` of speed-simu unpacks `<name>.mesh.zst` next to it when a run
needs it.

## Add a mesh

```bash
zstd -T0 -19 my_mesh.mesh -o my_mesh.mesh.zst
git add my_mesh.mesh.zst && git commit -m "Add my_mesh" && git push
```

then in speed-simu:

```bash
git -C data/meshes pull
git add data/meshes && git commit -m "Add my_mesh" && git push
```
