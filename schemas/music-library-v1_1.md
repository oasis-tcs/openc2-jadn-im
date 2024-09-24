         title: "Music Library"
       package: "http://fake-audio.org/music-lib"
       version: "1.1"
   description: "This information model defines a library of audio tracks, organized by album, with associated metadata regarding each track. It is modeled on the types of library data maintained by common websites and music file tag editors."
       license: "CC0-1.0"
       exports: ["Library"]

| Type Name   | Type Definition             | Description                                         |
|-------------|-----------------------------|-----------------------------------------------------|
| **Library** | MapOf(Barcode, Album){1..*} | Top level of the library is a map of CDs by barcode |

**********

| Type Name   | Type Definition            | Description                  |
|-------------|----------------------------|------------------------------|
| **Barcode** | String{pattern="^\d{12}$"} | A UPC-A barcode is 12 digits |

**********

model for the album

**Type: Album (Record)**

| ID | Name             | Type             | \#    | Description                               |
|----|------------------|------------------|-------|-------------------------------------------|
| 1  | **album_artist** | Artist           | 1     | primary artist associated with this album |
| 2  | **album_title**  | String           | 1     | publisher's title for this album          |
| 3  | **pub_data**     | Publication-Data | 1     | metadata about the album's publication    |
| 4  | **tracks**       | Track            | 1..\* | individual track descriptions and content |
| 5  | **total_tracks** | Integer{1..\*}   | 1     | total track count                         |
| 6  | **cover_art**    | Image            | 0..1  | cover art image for this album            |

**********

who and when of publication

**Type: Publication-Data (Record)**

| ID | Name             | Type         | \# | Description                           |
|----|------------------|--------------|----|---------------------------------------|
| 1  | **publisher**    | String       | 1  | record label that released this album |
| 2  | **release_date** | String /date | 1  | and when did they let this drop       |

**********

pretty picture for the album or track

**Type: Image (Record)**

| ID | Name              | Type         | \# | Description                             |
|----|-------------------|--------------|----|-----------------------------------------|
| 1  | **image_format**  | Image-Format | 1  | what type of image file?                |
| 2  | **image_content** | Binary       | 1  | the image data in the identified format |

**********

can only be one, but can extend list

**Type: Image-Format (Enumerated)**

| ID | Item    | Description |
|----|---------|-------------|
| 1  | **PNG** |             |
| 2  | **JPG** |             |
| 3  | **GIF** |             |

**********

interesting information about a performer

**Type: Artist (Record)**

| ID | Name            | Type              | \#    | Description           |
|----|-----------------|-------------------|-------|-----------------------|
| 1  | **artist_name** | String            | 1     | who is this person    |
| 2  | **instruments** | Instrument unique | 1..\* | and what do they play |

**********

collection of instruments (non-exhaustive)

**Type: Instrument (Enumerated)**

| ID | Item           | Description |
|----|----------------|-------------|
| 1  | **vocals**     |             |
| 2  | **guitar**     |             |
| 3  | **bass**       |             |
| 4  | **drums**      |             |
| 5  | **keyboards**  |             |
| 6  | **percussion** |             |
| 7  | **brass**      |             |
| 8  | **woodwinds**  |             |
| 9  | **harmonica**  |             |

**********

for each track there's a file with the audio and a metadata record

**Type: Track (Record)**

| ID | Name         | Type       | \# | Description                                      |
|----|--------------|------------|----|--------------------------------------------------|
| 1  | **location** | File-Path  | 1  | path to the audio file location in local storage |
| 2  | **metadata** | Track-Info | 1  | description of the track                         |

**********

information about the individual audio tracks

**Type: Track-Info (Record)**

| ID | Name                | Type           | \#    | Description                                                                               |
|----|---------------------|----------------|-------|-------------------------------------------------------------------------------------------|
| 1  | **track_number**    | Integer        | 1     | track sequence number                                                                     |
| 2  | **title**           | String         | 1     | track title                                                                               |
| 3  | **length**          | Integer{1..\*} | 1     | length of track in seconds; anticipated user display is mm:ss; minimum length is 1 second |
| 4  | **audio_format**    | Audio-Format   | 1     | format of the digital audio                                                               |
| 5  | **featured_artist** | Artist unique  | 0..\* | notable guest performers                                                                  |
| 6  | **track_art**       | Image          | 0..1  | each track can have optionally have individual artwork                                    |
| 7  | **genre**           | Genre          | 1     |                                                                                           |

**********

can only be one, but can extend list

**Type: Audio-Format (Enumerated)**

| ID | Item     | Description |
|----|----------|-------------|
| 1  | **MP3**  |             |
| 2  | **OGG**  |             |
| 3  | **FLAC** |             |
| 4  | **MP4**  |             |
| 5  | **AAC**  |             |
| 6  | **WMA**  |             |
| 7  | **WAV**  |             |

**********

Enumeration of common genres

**Type: Genre (Enumerated)**

| ID | Item                   | Description |
|----|------------------------|-------------|
| 1  | **rock**               |             |
| 2  | **jazz**               |             |
| 3  | **hip_hop**            |             |
| 4  | **electronic**         |             |
| 5  | **folk_country_world** |             |
| 6  | **classical**          |             |
| 7  | **spoken_word**        |             |

**********

| Type Name     | Type Definition | Description                                                                           |
|---------------|-----------------|---------------------------------------------------------------------------------------|
| **File-Path** | String          | local storage location of file with directory path from root, filename, and extension |

**********
