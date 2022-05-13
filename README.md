# ffmpeg
# using ffmpeg to bulk convert mp4 files to divx directly from command line

# $ for file in *.mp4 ; do ffmpeg -i "$file" -c:v mpeg4 -q:v 5 -tag:v DIVX -s 640x480 -c:a libmp3lame -q:a 5 -ac 2 -ar 44100 "converted${file}.avi" ; done
