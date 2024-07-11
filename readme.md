# Slide Show

Presents random pictures from a given Google Drive folder.

The application requires read access to your Google Drive. It will ask for it during first run or if it expired.

This does work with shared Drives.

Starting with the root folder, recursively select a random folder (or itself, if it contains at least one file). Once we hit a folder with only files, pick a random file. Validate it to be of supported image type and not respect the `MAX_FILE_SIZE` parameter. If we ever run into an issue (unsopported file, empty folder, etc.) try again from the root.

## Setup

You need to create a Google Cloud project, enable the API `drive.readonly`, Configure OAuth, and create access credentials. Make sure the Google account you are using has access to the files you want for the slideshow.

[Quick Start by Google](https://developers.google.com/workspace/guides/get-started). You need to enable `drive.readonly` API and provide the application with a credentials `credentials.json` file.

Furthermore, setup a `.env` file containing at least the following parameters:

- `DRIVE_ID='your-drive-id'`
- `ROOT_FOLDER_ID='your-folder-id'` (folder needs to be on that drive)
- `CREDENTIALS_FILE='credentials.json'`
- `SLIDESHOW_SPEED=30`: How fast the slideshow is going in seconds. More precisely, it will be this time plus the time to find and download a new image.

Optional parameters:

- `MAX_FILE_SIZE`: Maximum allowable file size in MB. Larger files are skipped.
- `PICTURE_KEEP_NR`: How many pictures are kept before they are deleted again. This can be useful, if you want to have another look at a past but recent picture.

There are a few more technical options, which you can find in the `Slideshow` class in the `__readEnv` method. (for advanced users)

## Usage

Run with `./slideshow.py`.

## Dependencies

You need Python 3 and pip.

Install dependencies from `requirements.txt` with `pip install -r requirements.txt`.

## License

This software is licensed under GPL 3.0 or later, see license file.

## Trivia

This project was created to show off pictures of [EESTEC LC Zurich](https://eestec.ethz.ch) by Michael Heider in January 2023, then Chairman of EESTEC LC Zurich.

## Developper

Help for the developer of this software and his random notes.

[Michael's Google Cloud Console project](https://console.cloud.google.com/home/dashboard?authuser=1&project=eestec-lc-zurich-slideshow&supportedpurview=project)

Tkinter: `pip install tk-tools` should be enough? Else `apt install python3-tk`.

`apt install python3-pil python3-pil.imagetk`

check supported image formats of Pillow: `python3 -m PIL`
