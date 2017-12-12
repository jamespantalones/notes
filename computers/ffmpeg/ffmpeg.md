## useful ffmpeg stuff

### Extract first frame as image
`ffmpeg -ss 0 -i input.mp4 -t 1 -f image2 poster.jpg`

### convert mp4 to webm
`ffmpeg -i input.mp4 -c:v libvpx -crf 10 -b:v 1M -c:a libvorbis output.webm`


### convert ape to mp3

- First make sure to get `avconv`
- `brew install libavcodec-extra-53`


`avconv -i 'input.ape' -id3v2_version 3 -codec:a libmp3lame -b 320k 'output.mp3'`
