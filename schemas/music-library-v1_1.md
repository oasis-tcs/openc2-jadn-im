## Schema
|                . | .                                                                                                                                                                                                                                 |
|-----------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **package:** | http://fake-audio.org/music-lib                                                                                                                                                                                                   |
|     **version:** | 1.1                                                                                                                                                                                                                               |
|       **title:** | Music Library                                                                                                                                                                                                                     |
| **description:** | This information model defines a library of audio tracks, organized by album, with associated metadata regarding each track. It is modeled on the types of library data maintained by common websites and music file tag editors. |
|     **license:** | CC0-1.0                                                                                                                                                                                                                           |
|     **exports:** | Library                                                                                                                                                                                                                           |


| Type Name   | Type Definition             | Description                                         |
|:------------|:----------------------------|:----------------------------------------------------|
| **Library** | MapOf(Barcode, Album){1..*} | Top level of the library is a map of CDs by barcode |


| Type Name   | Type Definition     | Description                  |
|:------------|:--------------------|:-----------------------------|
| **Barcode** | String (%^\d{12}$%) | A UPC-A barcode is 12 digits |

**_Type: Album (Record)_**

| ID | Name             | Type             | # | Description                         |
|---:|:-----------------|:-----------------|--:|:------------------------------------|
|  1 | **artist**       | Artist           | 1 | artist associated with this album   |
|  2 | **title**        | String           | 1 | commonly known title for this album |
|  3 | **pub_data**     | Publication-Data | 1 | metadata about album publication    |
|  4 | **tracks**       | Track            | 1 | individual track descriptions       |
|  5 | **total_tracks** | Integer{1..*}    | 1 |                                     |
|  6 | **cover_art**    | Image            | 1 | cover art image for this album      |

**_Type: Publication-Data (Record)_**

| ID | Name             | Type         | # | Description                           |
|---:|:-----------------|:-------------|--:|:--------------------------------------|
|  1 | **publisher**    | String       | 1 | record label that released this album |
|  2 | **release_date** | String /date | 1 | and when did they let this drop       |

**_Type: Image (Record)_**

| ID | Name              | Type         | # | Description                             |
|---:|:------------------|:-------------|--:|:----------------------------------------|
|  1 | **image_format**  | Image-Format | 1 | what type of image file?                |
|  2 | **image_content** | Binary       | 1 | the image data in the identified format |

**_Type: Image-Format (Enumerated)_**

| ID | Name    | Description |
|---:|:--------|:------------|
|  1 | **PNG** |             |
|  2 | **JPG** |             |
|  3 | **GIF** |             |

**_Type: Artist (Record)_**

| ID | Name            | Type              | # | Description           |
|---:|:----------------|:------------------|--:|:----------------------|
|  1 | **artist_name** | String            | 1 | who is this person    |
|  2 | **instruments** | Instrument unique | 1 | and what do they play |

**_Type: Instrument (Enumerated)_**

| ID | Name           | Description |
|---:|:---------------|:------------|
|  1 | **vocals**     |             |
|  2 | **guitar**     |             |
|  3 | **bass**       |             |
|  4 | **drums**      |             |
|  5 | **keyboards**  |             |
|  6 | **percussion** |             |
|  7 | **brass**      |             |
|  8 | **woodwinds**  |             |
|  9 | **harmonica**  |             |

**_Type: Track (Record)_**

| ID | Name         | Type      | # | Description                                      |
|---:|:-------------|:----------|--:|:-------------------------------------------------|
|  1 | **location** | File-Path | 1 | path to the audio file location in local storage |
|  2 | **metadata** | TrackInfo | 1 | description of the track                         |

**_Type: TrackInfo (Record)_**

| ID | Name             | Type          | # | Description                                                   |
|---:|:-----------------|:--------------|--:|:--------------------------------------------------------------|
|  1 | **t_number**     | Number{0..*}  | 1 | track sequence number                                         |
|  2 | **title**        | String        | 1 | track title                                                   |
|  3 | **length**       | Integer{1..*} | 1 | length of track in seconds; anticipated user display is mm:ss |
|  4 | **audio_format** | Audio-Format  | 1 | the all important content                                     |
|  5 | **featured**     | Artist unique | 1 | important guest performers                                    |
|  6 | **track_art**    | Image         | 1 | track can have individual artwork                             |
|  7 | **genre**        | Genre         | 1 |                                                               |

**_Type: Audio-Format (Enumerated)_**

| ID | Name     | Description |
|---:|:---------|:------------|
|  1 | **MP3**  |             |
|  2 | **OGG**  |             |
|  3 | **FLAC** |             |
|  4 | **MP4**  |             |
|  5 | **AAC**  |             |
|  6 | **WMA**  |             |
|  7 | **WAV**  |             |

**_Type: Genre (Enumerated)_**

| ID | Name                   | Description |
|---:|:-----------------------|:------------|
|  1 | **rock**               |             |
|  2 | **jazz**               |             |
|  3 | **hip_hop**            |             |
|  4 | **electronic**         |             |
|  5 | **folk_country_world** |             |
|  6 | **classical**          |             |


| Type Name     | Type Definition | Description                                                                           |
|:--------------|:----------------|:--------------------------------------------------------------------------------------|
| **File-Path** | String          | local storage location of file with directory path from root, filename, and extension |
