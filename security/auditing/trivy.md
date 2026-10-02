# Trivy

Trivy compares a project or an image you have locally with a vulnerability database. The first run downloads that database.

```bash
$ sudo pacman -S trivy
$ trivy fs .
```

`fs` scans the directory you name. `.` is the current one. It reports dependency and config findings in that tree.

An image already present in the local Docker store:

```bash
$ trivy image <image>
```

`<image>` is a name from `docker images`, such as one you built or pulled for your own use. Trivy does not patch the finding. Upgrading the dependency or the base image is the fix.

Configuration files in the tree, such as a Dockerfile or a Kubernetes manifest:

```bash
$ trivy config .
```

The cluster in your current kubeconfig:

```bash
$ trivy k8s --report summary
```

`k8s` reads the same context `kubectl` is using. See `linux/kubernetes.md`. `--report summary` counts findings instead of printing every object.
