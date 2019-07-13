# javascript-srt-to-speech
Subtitles (SRT) to speech using Javascript

A single page application (SPA) that will play an MP4 and speak the Subtitle file using text-to-speech

Tested and working on FireFox
 				Supported video:     MP4
 				Supported subtitles: SRT
				ajax access to file:// allowed
```
FireFox update no longer allows ajax to fetch file:///  Reason: CORS request not HTTP
```

Google Chrome: 
       speechsynthesis no longer works
       ajax access to file:// not allowed

How this works in brief:

1. Place this file index.html into a movie directory e.g. /my.movie.2019
2. there must be a movie inside this directory with the same name e.g. /my.movie.2019.mp4
3. set video.src = current_directory_name/current_directory_name.mp4
4. use ajax to load subtitle file current_directory_name/current_directory_name.srt
5. parsing SRT file:
   srtBuffer['00:00:20'] = 'This is a line in the subtitle file'
   srtBuffer['00:00:25'] = 'This is another line in the subtitle file'
6. setInterval:
   videoTimeToLocalTime( video.currentTime ) to give you 'hh:mm:ss'
7. srtBuffer[ local_time ] to give you the subtitle text at video.currentTime
8. speak the text:
   speechSynthesis.speak( new SpeechSynthesisUtterance( subtitle_text ) );

![Interface](https://github.com/wilwad/javascript-srt-to-speech/blob/master/screen.png)

How to use

Place index.html into your movie folder. It will auto detect the movie name and SRT file by using window.location.href.
Meaning the directory and movie names must match.
