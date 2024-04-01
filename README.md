# ffmpeg 📼
# using ffmpeg to bulk convert mp4 files to divx directly from command line

### $ for file in *.mp4 ; do ffmpeg -i "$file" -c:v mpeg4 -q:v 5 -tag:v DIVX -s 640x480 -c:a libmp3lame -q:a 5 -ac 2 -ar 44100 "converted${file}.avi" ; done

# using ffmpeg to cut part of streaming video 
### not working anymore 
$ ffmpeg $(python3 $(which youtube-dl) -g 'https://www./watch?v=' | sed "s/.*/-ss 02:38:22 -i &/") -t 06:28 -c copy out.mkv
### use yt-dlp to download file
### $ ffmpeg -i <file> -ss 00:31:38 -t 03:00 -c copy out.mp4
###                                 -to 00:34:38 -c copy out.mp4

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

# convert mjpeg to mp4 (type of video is mjpeg, .avi is just container)
### $ .\ffmpeg.exe -i input.avi -pix_fmt yuv420p -b:v 4000k -c:v libx264 output.mp4  

# error - ffmpeg height not divisible by 2 (656x465) or Could not find tag for codec vp8 in stream #0, codec not currently supported in container  
# or height not divisible by 2 (656x465)
### $ ffmpeg -i screenrecord.webm -vcodec libx264 -vf "pad=ceil(iw/2)*2:ceil(ih/2)*2" -r 24 -y -an video.mp4

# wav to mp3
### ffmpeg -i input.wav -vn -ar 44100 -ac 2 -b:a 192k output.mp3

# mp3 reduce size
### ffmpeg -i input.mp3 -map 0: a :0 -b:a 96k output.mp3

# change video resolution for instagram  
### ffmpeg -y -i output_srt.mp4 -vf "[in]scale=iw*min(1080/iw\,1350/ih):ih*min(1080/iw\,1350/ih)[scaled]; [scaled]pad=1080:1350:(1080-iw*min(1080/iw\,1350/ih))/2:(1350-ih*min(1080/iw\,1350/ih))/2[padded]; [padded]setsar=1:1[out]" -c:v libx264 -c:a copy insta_output.mp4
