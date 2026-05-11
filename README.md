# music-oyakodon

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

A simple, self-hosted web music player for a playlist of AI-generated songs about Oyakodon, created with Suno AI.

## Demo

A live demo can be viewed on GitHub Pages.

The player interface displays the playlist, album art, song information, and lyrics in a three-panel layout against a blurred background of the current track's artwork.


![A screenshot of the music player interface. On the left is a playlist titled "親子丼". In the center is the album art for a song, with audio controls and song metadata below. On the right are the song's lyrics. The background is a blurred version of the album art.](https://user-images.githubusercontent.com/593814/293214515-5c120464-325b-402e-9d8c-572793610931.png)


## Features
- **Three-Panel UI**: Displays the playlist, main player controls, and lyrics simultaneously.
- **Dynamic Background**: Uses the current song's album art for a blurred, full-screen background.
- **Media Session API**: Integrates with native OS media controls for playback management from the lock screen, notification center, or connected devices.
- **Self-Hosted**: Runs as a static webpage with no server-side dependencies. All assets are local.
- **Customizable Playlist**: Easily adaptable for any playlist exported from Suno AI.
- **Multiple Sort Orders**: Includes several JavaScript functions to sort or shuffle the playlist, such as `riffleShuffle` and `likeSort`.

## Usage
To use this player with your own Suno AI playlist:

1.  **Download Assets**: From Suno, download your playlist's JSON file and all associated audio (`.mp3`) and large image (`.jpeg`) files.
2.  **Organize Files**:
    - Place all `.mp3` files into the `audio/` directory.
    - Place all large image files into the `image_large/` directory.
3.  **Configure Playlist**:
    - Create a copy of your downloaded JSON file and name it `playlist.json` in the root directory.
    - Open `playlist.json` and edit the `audio_url` and `image_large_url` paths for each track to be relative paths pointing to the local files.
    - Example:
      ```json
      "audio_url": "audio/a5d20ca2-0542-4df9-be56-97f711a81cc7.mp3",
      "image_large_url": "image_large/image_large_a5d20ca2-0542-4df9-be56-97f711a81cc7.jpeg",
      ```
4.  **Deploy**: Host the entire project folder on a static web server or deploy it using GitHub Pages.

## Playlist Data
The player is driven by the `playlist.json` file, which is an adapted version of a playlist export from Suno AI. The player uses the following fields:
- `name`: The title of the playlist/album.
- `playlist_clips`: An array of song objects.
  - `clip.title`: The song title.
  - `clip.audio_url`: The relative path to the audio file.
  - `clip.image_large_url`: The relative path to the album art.
  - `clip.metadata.prompt`: The full lyrics of the song.
  - `clip.metadata.gpt_description_prompt`: The prompt used for generation, also used to create the song title.

## Acknowledgements
This project is based on the [music-handaduke](https://github.com/code4fukui/music-handaduke/) player.

## License
MIT License