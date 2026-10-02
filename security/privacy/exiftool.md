# exiftool

exiftool prints the metadata stored inside a photo, video, or PDF: camera, timestamps, author, and GPS when the file has them. Stripping that metadata before you send a file is the other half. `mat2` does the strip with less control. This is the read and the precise delete.

```bash
$ sudo pacman -S perl-image-exiftool
$ exiftool photo.jpg
$ exiftool -gps:all -time:all photo.jpg
```

`-gps:all` is only the location tags. `-time:all` is only the timestamps. No flags prints every tag. Nothing is written.

Write a copy with the metadata removed. The original stays.

```bash
$ exiftool -all= -o clean.jpg photo.jpg
```

`-all=` deletes the tags. `-o` is the new file. Do not point `-o` at the original. Open `clean.jpg` and run `exiftool` on it. The GPS and camera tags should be gone.
