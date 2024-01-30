---
layout: post
title: "Legacy Media Data Migration Project"
featured: "/assets/flash-project/01-initial-separate-datasets.png"
categories: project
---

A data migration project: transforming multiple separate data sets of legacy media into an organised collection for archival purposes.

# Adobe Flash media archival project

![Screenshot of the initial separate datasets with inconsistencies](/assets/flash-project/01-initial-separate-datasets.png)

From 2005 to 2017, the library of music for a now-defunct popular online game platform was encoded as Adobe Flash ‘SWF’ files. In 2020, support for Adobe Flash was discontinued, resulting in the inability to access or play music stored in this codec.

This project aimed to preserve media previously stored in the defunct codec ‘SWF’ by converting the archive into a universally supported codec ‘MP3’.

Multiple data sets exist containing links to the archived media online as ‘SWF’ files, along with metadata such as when and where it was used. However, these data sets were maintained independently of each other, resulting in inconsistencies such as missing values in either data set or various titles for the same music track.

![Screenshot of the initial separate datasets with inconsistencies](/assets/flash-project/01-initial-separate-datasets.png)
_Screenshot of the initial separate datasets with inconsistencies (Excerpt)_

These data sets were copied into a CSV through web scraping, and were joined together by the ‘ID’ column. The archived SWF files were downloaded and compiled into a single collection of SWF files grouped by ‘ID’ using a Python script.

![Table of tracks joined and ordered by ID (Excerpt)](/assets/flash-project/02-compiled-data-set-with-links.png)
_Table of tracks grouped by ID (Excerpt)_

![Local archive of SWF files grouped by ID (Excerpt)](/assets/flash-project/03a-downloaded-swfs.png)
_Local archive of SWF files grouped by ID (Excerpt)_

While some tracks were identical across data sets, some tracks featured multiple versions due to IDs being reused when certain tracks were replaced over the 12 year period.

_Multiple versions of a track sharing the same ID (Excerpt)_
![Multiple versions of a track sharing the same ID (Excerpt)](/assets/flash-project/03c-downloaded-swfs-and-organised-swfs-based-on-cp-id.png)

Additionally, some tracks were unnamed in either data set, or had multiple names when the data sets were combined.

![Multiple instances of a single track, with one lacking a name (Excerpt)](/assets/flash-project/03b-downloaded-swfs-and-organised-swfs-based-on-cp-id.png)
_Multiple instances of a single track, with one lacking a name (Excerpt)_

To remove unnecessary duplicate files, a script was written to compare the hashes of all files, record the aliases of tracks, and retain only one copy of a unique file. The result was a JSON data set of all unique tracks accompanied by their respective title(s) and track ID(s).

![A JSON file including the hashes and aliases of tracks (Excerpt)](/assets/flash-project/04a-remove-duplicates-by-checking-hash.png)
_A JSON file including the hashes and aliases of tracks_

A Python script was written to carry out OS commands and utilise the following external tools via the command line. JPEXS FFDec was used to extract the audio streams of every SWF file. Due to how the SWF codec is designed, some music tracks are split into multiple audio streams. FFmpeg was used to concatenate the separate audio streams into a single MP3 file.

_A single SWF file consisting of multiple audio streams [JPEXS FFDec GUI version]_
![A single SWF file consisting of multiple audio streams [JPEXS FFDec GUI version] ](/assets/flash-project/05a-extract-mp3s-from-swfs.png)

![A single track split into multiple audio segments ](/assets/flash-project/05b-separate-mp3-tracks-each.png)
_A single track split into multiple audio segments_

![A collection of unique music tracks, after duplicate files are removed and separated audio segments are concatenated (Excerpt)](/assets/flash-project/06-removed-duplicate-mp3s.png)
_A collection of unique music tracks, after duplicate files are removed and separated audio segments are concatenated (Excerpt)_

![JSON data set of the collection of unique music tracks (Excerpt)](/assets/flash-project/07-matched-with-original-cp-ids.png)
_JSON data set of the collection of unique music tracks (Excerpt)_

A third data set containing information on the usage of each track was incorporated into the final resulting data set containing music track information and MP3 files.

## Summary

This project involved web scraping and merging incomplete data sets, and data cleaning, to produce a complete data set of information about music tracks used by an online platform. Through writing scripts in Python and batch, utilising JPEXS FFDec and ffmpeg, an archive of Adobe Flash ‘SWF’ files was transformed into a catalogued collection of MP3s and metadata.
