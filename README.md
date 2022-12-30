# ffmpeg
# using ffmpeg to bulk convert mp4 files to divx directly from command line

### $ for file in *.mp4 ; do ffmpeg -i "$file" -c:v mpeg4 -q:v 5 -tag:v DIVX -s 640x480 -c:a libmp3lame -q:a 5 -ac 2 -ar 44100 "converted${file}.avi" ; done

# using ffmpeg to cut part of streaming video 
### $ffmpeg $(python3 $(which youtube-dl) -g 'https://www./watch?v=' | sed "s/.*/-ss 02:38:22 -i &/") -t 06:28 -c copy out.mkv

# using ffmpeg to convert webm to mp4
### $ffmpeg -fflags +genpts -i 1.webm -r 24 1.mp4

# using ffmpeg to add album cover to mp3
### $ffmpeg -i in.mp3 -i album_cover.png -map 0:0 -map 1:0 -c copy -id3v2_version 3 -metadata:s:v title="Album cover" -metadata:s:v comment="Cover (front)" out.mp3

# using ffmpeg to convert from webm to mp3
### $ffmpeg -i input.webm -vn -ab 128k -ar 44100 -y output.mp3

# using ffmpeg to concat files
### $ for i in *.mp4; do ffmpeg -i "$i" -acodec copy -vcodec copy -vbsf h264_mp4toannexb -f mpegts "converted${i}.ts"; done
### $ ffmpeg -i "concat:vid1.ts|vid2.ts" -vcodec copy -acodec copy out.mp4

# converting mkv to mp4
### $ for f in *.mkv; do ffmpeg -i "$f" -c copy "${f%.mkv}.mp4"; done

# convert mp4 to mp3
### $ ffmpeg -i out.mp4 -b:a 64K out.mp3

# convert mkv to mp3
####  it's best to use -q:a 0 for variable bit rate and it's good practice to specify -map a to exclude video/subtitles and only grab audio:
### $ ffmpeg -i sample.avi -q:a 0 -map a sample.mp3

# reduce size
### $ ffmpeg -i input.mp4 -vcodec libx265 -crf 28 output.mp4
