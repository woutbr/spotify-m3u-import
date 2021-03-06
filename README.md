# spotify-m3u-import

A small python script to create a Spotify playlist from a m3u8 playlist file.

It will:

  - Read each entry in the playlist file
  - Read the tags from each file
  - If there are no tags it will attempt to guess the artist and title from the file name
  - Use this data to find a track on Spotify
  - Create a Spotify playlist using the results

Tags are read with [tinytag](https://github.com/devsnd/tinytag/) which supports MP3, OGG, OPUS, MP4, M4A, FLAC, WMA and Wave files.

Relative paths are read from the working directory. So you should run the script from the same directory as the playlist file.

## Installation and requirements

Create virtual environment

Example using virtualenv wrapper
```
mkvirtualenv spotify-m3u-import-env
```

Install python modules:

```
pip install -r requirements.txt
```

Take 5 mins to register an app to get access to the Spotify API:

https://developer.spotify.com/my-applications/#!/

The Redirect URI doesn't need to be valid, it can be a non-existant domain.

## Usage

```
$ ./read-id3-tags.py --help
usage: read-id3-tags.py [-h] -f FILE [-t TITLE] -u USERNAME -c CLIENT_ID -s CLIENT_SECRET -r REDIRECT_URI [-d]

A script to import a m3u8 playlist into Spotify

arguments:
  -f FILE, --file FILE  Path to m3u8 playlist file
  -u USERNAME, --username USERNAME
                        Spotify username
  -c CLIENT_ID, --client_id CLIENT_ID
                        Spotify client id
  -s CLIENT_SECRET, --client_secret CLIENT_SECRET
                        Spotify client secret
  -r REDIRECT_URI, --redirect_uri REDIRECT_URI
                        Spotify redirect url
optional arguments:
  -h, --help            show this help message and exit
  -t TITLE, --title TITLE 
                        Spotify playlist name
  -d, --debug           Debug mode
```

## Example

```
$ ./read-id3-tags.py -f my_playlist.m3u8 -u 2gar3ca9le -c q87ofe38ya -s 1z75hnff99 -r http://localhost/
Parsed 3 tracks from my_playlist.m3u8

tracks/inspectah deck - the movement - 12 - vendetta.mp3
IDv3 tag data: Inspectah Deck - Vendetta
Guess from filename: Not required
Spotify: Inspectah Deck - Vendetta, 23GoX2Usy1Ios5zCVRIIAO

tracks/darude-sandstorm.mp3
IDv3 tag data: None
Guess from filename: darude - sandstorm
Spotify: Darude - Sandstorm - Extended, 7ikiyBfgcVuAKAwZXXkWVT

tracks/dave spoon - at night (shadow child & t. williams re-vibe).mp3
IDv3 tag data: None
Guess from filename: dave spoon - at night (shadow child & t. williams re
Spotify: Dave Spoon - At Night - Shadow Child & T. Williams Re-vibe, 1JEA273o693GwuI39gayHk

3/3 of tracks matched on Spotify, creating playlist "my_playlist" on Spotify... done
```

## Acknowledgments

 - [FutureSharks](https://github.com/FutureSharks) for writing the original [spotify-m3u-import](https://github.com/FutureSharks/spotify-m3u-import)
 - [devsnd](https://github.com/devsnd) for writing [tinytag](https://github.com/devsnd/tinytag/) 

## TODO

- Write list of tracks not matched