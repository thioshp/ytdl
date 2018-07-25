YOUTUBE-DL STUFF FOR BASH
==========

1. Get latest version of youtube-dl

# Add the following function to your <I>.bashrc file</I> 

---

`function ytdlnew()
{
	# path to save in
	cd /sdcard/codelab/shell/binaries
	
	# fetch with curl, save to filename with current date
	curl -L https://yt-dl.org/latest/youtube-dl -o youtube-dl_`date +%m-%d-%Y`
	echo "Done..."
}`

2. aliases for youtube-dl

Add the following aliases to ~/.aliases

>alias ytdl="youtube-dl --prefer-ffmpeg --user-agent \"Mozilla/5.0 (Windows NT 5.1; rv:10.0.2) Gecko/20100101 Firefox/10.0.2\" --referer https://www.google.com -i --restrict-filenames -o '/sdcard/Videos/%(title)s.%(ext)s' --console-title --no-check-certificate --all-subs --sub-format \"ass/srt/best\" " #download youtube videos

#
>alias ytdlsublist='youtube-dl --newline -i -k --restrict-filenames -o /sdcard/Videos/%(title)s.%(ext)s -f 18 --prefer-ffmpeg --console-title -t --no-check-certificate --all-subs --sub-format ass/srt/best -a "$1"'

>alias ytget="cd /sdcard/Videos/ && ytdl -g" #get video url then use other downloader to fetch it

>alias ytwget="cd /sdcard/Videos/ && ytdl -f 18 --external-downloader wget" #use wget to fetch video

>alias ytxdm="cd /sdcard/Videos/ && ytdl -f 18 --external-downloader xdm" #use xdm to get videos

>alias ytaria='cd /sdcard/Videos/ && ytdl -f 18 --external-downloader aria2c' #use aria2c to get 640x360 videos

>alias yt18='cd /sdcard/Videos/ && ytdl -f 18+18 --merge-output-format mkv' #download format 18 (640x360) video format (mp4) or add -f 18+18 to enable merging of video formats

>alias yt22='cd /sdcard/Videos/ && ytdl -f 22' #download format 18 (1280x7200) video format (mp4)

>alias ytdlf='ytdl -F' #show available video sizes

>alias ytdla='cd /sdcard/Music/ && ytdl -f 18 -x --audio-format mp3 --audio-quality 320K --add-metadata --embed-thumbnail -k' 

#extract high quality audio
>alias ytbest="cd /sdcard/Videos/ && ytdl -f bestvideo+bestaudio --merge-output-format mkv --embed-thumbnail -i" # get best quality video + audio

>alias ytdmpv="cd /sdcard/Videos/ && yt18 --exec 'mpv --profile=pseudo-gui --osd-level 3 --vf=eq --softvol=yes --softvol-max=300 --volume=80 {}'"

>alias ytdlma="ytdl -f 140" #get M4A audio

