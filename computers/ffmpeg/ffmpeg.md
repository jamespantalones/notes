## useful ffmpeg stuff

### Extract first frame as image
`ffmpeg -ss 0 -i input.mp4 -t 1 -f image2 poster.jpg`

### convert mp4 to webm
`ffmpeg -i input.mp4 -c:v libvpx -crf 10 -b:v 1M -c:a libvorbis output.webm`


### convert ape to mp3

- First make sure to get `avconv`
- `brew install libavcodec-extra-53`


```bash
avconv -i 'input.ape' -id3v2_version 3 -codec:a libmp3lame -b 320k 'output.mp3'
```


### convert entire ape folder to mp3

```bash
for d in *; do
  ## get ext
  ext="${d#*.}"
  ## get name without filetype
  pre="${d%%.*}"
  if [ "$ext" = "ape" ]; then
    avconv -i "$d" -id3v2_version 3 -codec:a libmp3lame -b 320 "${pre}.mp3"
  fi
done
```

### gif to mp4
```bash
ffmpeg -f gif -i FOO.gif -pix_fmt yuv420p -c:v libx264 -movflags +faststart -filter:v crop='floor(in_w/2)*2:floor(in_h/2)*2' BAR.mp4
```


### youtube-dl
```bash
# Download single entry
youtube-dl -i --extract-audio --audio-format mp3 --audio-quality 0 YT_URL

# Download playlist
youtube-dl -ict --yes-playlist --extract-audio --audio-format mp3 --audio-quality 0 https://www.youtube.com/playlist?list=UUCvVpbYRgYjMN7mG7qQN0Pg
```
