<img align="left" width="100" height="100" src="https://raw.githubusercontent.com/7x11x13/songs-to-youtube/master/image/icon.ico" alt="icon">

# songs-to-youtube

Convert audio files to videos and upload them to YouTube automatically.

![Example](/docs/example.png)

## Features
- Extracts album covers from audio files
- Extracts other metadata which can be used in template strings for the video title/description etc.
- Can concatenate songs to upload an album as a single video
- Can upload an album as a playlist of multiple videos
- Encode multiple videos in parallel
- Multi-user support
- Does not re-encode audio

## Pre-installation
- [FFmpeg](https://ffmpeg.org/download.html) binary is required to convert songs into videos
- [Firefox](https://www.mozilla.org/firefox/new/) and [geckodriver](https://github.com/mozilla/geckodriver/releases) binaries are required to upload to YouTube
- Make sure FFmpeg and geckodriver are both in your PATH environment variable

## Installation

There are two ways to install this program:

### PyInstaller

Download the latest release for your platform [here](https://github.com/7x11x13/songs-to-youtube/releases), unzip the archive, and run the songs-to-youtube executable.
Currently the Windows exectuable is flagged as a virus by Microsoft Defender, among others. If that is the case, you can just run from the source code.

### Run from source
If you have issues running the exectuable, you can try running the program from the source code:
1. Download the source code
2. Install required Python modules with `python3 -m pip install -r requirements.txt`
3. Run the program with `python3 main.py`

## Notes
- Before you upload any videos, you must sign in to a YouTube account (File > Settings > Add new user)
- You can drag and drop songs on the main window to add them to the queue. The order in which they are uploaded goes from top to bottom
- You can also drag and drop images onto a song's current album art to change it
- You probably shouldn't change the output file extension from .avi
- If you get an error saying "Too large number of skipped frames XXXXX > 60000" try increasing the input frame rate to 2

### Template strings
Write `~{key}` in any text field and it will be replaced with an appropriate value. To see the available metadata values, right click on an album or song and select "View metadata."
Here are some useful values:
#### Song metadata
- `~{song_dir}` - directory of the input audio file
- `~{song_file}` - file name of the input audio
- `~{tags.album}` - name of the song's album
- `~{tags.artist}` - name of the song's artist
- `~{tags.title}` - name of the song
- `~{tags.comment.text}` - comment; used by bandcamp to link to the artist's page
#### Album metadata
- `~{album_dir}` - directory of the album
- `~{timestamps}` - special key that generates timestamps based on song lengths
- `~{song.tags.artist}` - name of the album's artist (usually)

The first song of an album can have its keys accessed by the album by prefixing the key with `song.`
