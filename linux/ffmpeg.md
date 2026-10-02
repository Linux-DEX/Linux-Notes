# ffmpeg

ffmpeg reads and writes audio and video. `-i` is the input. With no output file, it only prints what is in the file.

```bash
$ sudo pacman -S ffmpeg
$ ffmpeg -i input.mp4
```

The banner lists each stream: video codec, audio codec, duration.

Copy the streams into a new container without re-encoding:

```bash
$ ffmpeg -i input.mp4 -c copy output.mkv
```

Re-encode audio to MP3:

```bash
$ ffmpeg -i input.wav output.mp3
```

ffmpeg picks the encoder from the output filename. Add `-y` only when you mean to overwrite `output.mp3`.
