<p align="center">
<img
    src=".github/logo.png"
    width="260" border="0" alt="spotifydownload">
<br>
<a href="https://travis-ci.org/schollz/spotifydownload"><img
src="https://img.shields.io/travis/schollz/spotifydownload.svg?style=flat-square"
alt="Build Status"></a> 
<a href="https://gocover.io/github.com/schollz/getsong"><img src="https://img.shields.io/badge/coverage-82%25-brightgreen.svg?style=flat-square" alt="Coverage"></a> </p>

<p align="center">Automatically download your Spotify playlists.</p>

*spotifydownload* is an [open-source](https://github.com/schollz/spotifydownload) tool that makes it easy to download your Spotify playlists, using [getsong](https://github.com/schollz/getsong) to find the correct song and download it and convert it to an m4a.

![Example](.github/1.gif)

Unlike other downloaders, there are no dependencies (other than ffmpeg which will automatically be installed onto your system when running the first time).

**Disclaimer:** Downloading copyright songs may be illegal in your country. This tool is for educational purposes only and was created only to show how Spotify's API can be used to download music from YouTube. Please support the artists by buying their music.



# Install

Install by downloading [latest release](https://github.com/schollz/spotifydownload/releases/latest).

Or install with bash:

```
curl https://getspotifydownload.schollz.com | bash
```

Or install with `go get`:

```
go get github.com/schollz/spotifydownload
```

# Usage


To run simply do

```bash
$ spotifydownload
```

and you'll be prompted with instructions to get the Spotify URL link. To get the Spotify URL link you can right click on the playlist. If you are using the Desktop client, then you'll see a button "Shared > 🔗 Copy Playlist Link", or in the Web browser you'll see "Copy Playlist Link". Clicking that will copy the Spotify Playlist link to the clipboard.


If you already know your playlist URL you can enter it:

```bash
$ spotifydownload -playlist PLAYLIST_URL
```

Now you can easily schedule this to run using `crontab`, just edit it with `crontab -e` and add the line:

```
0 0 * * 0 cd /folder/to/spotifydownload &&  ./spotifydownload --playlist PLAYLIST_URL
```

which will execute it every 7 days so that you will never lose any songs in your Release Radar or Discover Weekly.

# Token Usage

**A Spotify access token is required.**

To use this tool, you must set the `SPOTIFY_TOKEN` environment variable with your own Spotify Bearer token. The app will not function without it.

How to extract your token:

1. Open [Spotify Web Player](https://open.spotify.com/) in your browser and log in.
2. Open Developer Tools (usually F12 or right-click → Inspect).
3. Go to the Network tab.
4. Play any song or interact with the page.
5. Click on any XHR request in the list (e.g. `playlist`, `search`, etc).
6. In the request headers, look for the `authorization` header. It will look like:
   
   ```
   authorization: Bearer BQ...your_token_here...
   ```
7. Copy the entire token (everything after `Bearer `).
8. Set it in your shell before running the app:

```bash
export SPOTIFY_TOKEN=your_token_here
spotifydownload -playlist PLAYLIST_URL
```

If the token expires, repeat the steps above to get a new one.

## Contributing

Pull requests are welcome. Feel free to...

- Revise documentation
- Add new features
- Fix bugs
- Suggest improvements


## License

MIT

