# spotify-m3u-import

A small python script to create a Spotify playlist from a m3u playlist file.

It will:

  - Read each entry in the playlist file
  - Read the IDv3 tags from each MP3 file
  - If there are no IDv3 tags it will attempt guess the artist and title from the file name
  - Use this data to find a track on Spotify
  - Create a Spotify playlist using the results

## Installation and requirements

Create virtual environment for python 2.7

Example using virtualenv wrapper
```
mkvirtualenv spotify-m3u-import -p python2.7
```

Install python modules:

```
pip install -r requirements.txt
```

Take 5 mins to register an app to get access to the Spotify API:

https://developer.spotify.com/my-applications/#!/

The Redirect URI doesn't need to be valid, it can be a non-existant domain.

## Example

```
$ ./read-id3-tags.py --help
usage: read-id3-tags.py [-h] -f FILE -u USERNAME [-d]

A script to import a m3u playlist into Spotify

optional arguments:
  -h, --help            show this help message and exit
  -f FILE, --file FILE  Path to m3u playlist file
  -u USERNAME, --username USERNAME
                        Spotify username
  -c CLIENT_ID, --client_id CLIENT_ID
                        Spotify client id
  -s CLIENT_SECRET, --client_secret CLIENT_SECRET
                        Spotify client secret
  -r REDIRECT_URI, --redirect_uri REDIRECT_URI
                        Spotify redirect url
  -d, --debug           Debug mode
$ 
$ ./read-id3-tags.py -f my_playlist.m3u -u my_username -c 5345235325 -s 5435345345 -r http://asdasfsdafsdafd.com
Parsed 3 tracks from my_playlist.m3u

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

3/3 of tracks matched on Spotify, creating playlist "my_playlist.m3u" on Spotify... done
```

## TODO
- Parse remixes to download originals if can not find the remix.


