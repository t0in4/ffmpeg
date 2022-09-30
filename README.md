# ffmpeg
# using ffmpeg to bulk convert mp4 files to divx directly from command line

### $ for file in *.mp4 ; do ffmpeg -i "$file" -c:v mpeg4 -q:v 5 -tag:v DIVX -s 640x480 -c:a libmp3lame -q:a 5 -ac 2 -ar 44100 "converted${file}.avi" ; done

# using ffmpeg to cut part of streaming video 
### $ffmpeg $(python3 $(which youtube-dl) -g 'https://www./watch?v=' | sed "s/.*/-ss 02:38:22 -i &/") -t 06:28 -c copy out.mkv

# using ffmpeg to convert webm to mp4
### $ffmpeg -fflags +genpts -i 1.webm -r 24 1.mp4

