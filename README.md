# LBRY Batch Upload - WIP

Automate uploading entire folders to [lbry.tv] using [selenium] and [pyautogui].

Made mostly to practice Selenium, it is designed for music albums, still rough around
the edges and neither well thought nor complete.

## User Requirements

- Fill [upload_settings.json] before running the script
- Provide an absolute folder path
- Available thumbnail url
- Song titles must match the format `{number} - {title}.{format}`
- Folder structure as follows

```bash
.
└── Red Hot Chili Peppers
    └── Californication
        ├── 01 - Around the World.flac
        ├── 02 - Parallel Universe.flac
        ├── 03 - Scar Tissue.flac
        ├── 04 - Otherside.flac
        ├── 05 - Get on Top.flac
        ├── 06 - Californication.flac
        ├── 07 - Easily.flac
        ├── 08 - Porcelain.flac
        ├── 09 - Emit Remmus.flac
        ├── 10 - I Like Dirt.flac
        ├── 11 - This Velvet Glove.flac
        ├── 12 - Savior.flac
        ├── 13 - Purple Stain.flac
        ├── 14 - Right on Time.flac
        ├── 15 - Road Trippin.flac
        ├── album_info.txt
        └── Californication.jpg
```

> Files should be in a folder which is named after the album, which should be located
> inside another folder that is named after the artist.

## Usage

- Create a virtual enviroment and activate it

    ```sh
    python3 -m virtualenv venv && source venv/bin/activate
    ```

- Install the requirements

    ```sh
    pip install -r requirements.txt
    ```

- Fill `upload_settings.json`

- Run the script

    ```sh
    python batch_upload.py
    ```

### Changelog

- 2020-06-12:
  - Change webdriver yo improve speed: `Firefox -> Chrome`
  - Change settings file name: `settings.json -> upload_settings.json`
  - Move credentials from `.env` to `upload_settings.json`
  - Remove `python-dotenv` requirement
  - Apply PageObject pattern
  - Remove `price` from settings until i manage to circunvent an obstructing lable
  - Bump wait time before and after file selection to 1s

### TODO

- [x] Implement PageObject pattern
- [x] Keep the upload page on sight when uploading the last file
- [x] Better explanation of usage and capabilities _(not good enough)_
- [ ] Add configuration guide to `README.md` with all valid values for `upload_settings.json`
- [ ] Add example credentials file or move them to `upload_settings.json`
- [ ] Validate `upload_settings.json` before uploading any file
- [ ] Warn about naming issues before uploading any file (mainly punctuation)
- [ ] Prepend artist, album and title info to description string
- [ ] Better way of setting a description than a string in `upload_settings.json`
- [ ] Follow prefered selector order (`id > name > links text > css > xpath`)
- [ ] Add argument to enable dark mode on the webpage
- [ ] Prevent or react to "failed to fetch" error on login
- [ ] Handle price option
- [ ] Implement waits
- [ ] Type hints
- [ ] Unit tests

[lbry.tv]: https://lbry.tv/
[selenium]: https://github.com/SeleniumHQ/selenium
[pyautogui]: https://github.com/asweigart/pyautogui
[upload_settings.json]: upload_settings.json
