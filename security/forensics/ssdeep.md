# ssdeep

ssdeep computes a fuzzy hash. Two files that are not byte-for-byte identical can still score as similar. Kali lists it with the forensics hashing tools.

```bash
$ sudo pacman -S ssdeep
$ ssdeep file
$ ssdeep -r directory > hashes.ssdeep
$ ssdeep -m hashes.ssdeep suspect
```

The hash is printed next to the filename. `-r` walks a directory. `-m` compares `suspect` to every hash in the file. The match line ends with a score from 0 to 100. 100 is the same content. 0 is no similarity.
