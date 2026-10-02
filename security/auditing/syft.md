# syft

syft writes a software bill of materials: the packages and libraries inside a directory or an image.

```bash
$ sudo pacman -S syft
$ syft dir:.
$ syft dir:. -o spdx-json=sbom.json
$ syft <image>
```

`dir:.` scans the current directory. `-o spdx-json=sbom.json` writes that list to a file instead of the table. `<image>` is a local image name from `docker images`, or one syft can pull because you already use it.

The SBOM is an inventory, not a vulnerability report. Feeding it to a scanner is `trivy`, in `security/auditing/trivy.md`.
