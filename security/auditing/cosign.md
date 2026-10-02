# cosign

cosign signs a file or a container image and checks the signature later. The private key stays on the machine that signs.

```bash
$ sudo pacman -S cosign
$ cosign generate-key-pair
```

That writes `cosign.key` and `cosign.pub` in the current directory and asks for a password for the private key. `cosign.key` does not belong in Git.

Sign a file and check it:

```bash
$ cosign sign-blob --key cosign.key --output-signature sig secret.txt
$ cosign verify-blob --key cosign.pub --signature sig secret.txt
```

`verify-blob` prints the claims and exits 0 when the signature matches this file and this public key. Any change to the file makes verification fail.

Signing an image uses the same key pair, and the image has to already be in a registry:

```bash
$ cosign sign --key cosign.key <registry>/<name>:<tag>
$ cosign verify --key cosign.pub <registry>/<name>:<tag>
```

Push the image first. `docker push` is in `linux/docker.md`.
