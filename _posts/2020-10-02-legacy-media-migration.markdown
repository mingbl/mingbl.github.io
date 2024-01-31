---
layout: post
title: "Legacy Media Data Migration Project"
featured: "/assets/flash-project/legacy-heading.png"
categories: project
---

A data migration project: transforming multiple separate datasets of legacy media into an organised collection for archival purposes.

# Adobe Flash media archival project

![Representation of before and after data migration](/assets/flash-project/legacy-heading.png)
_Representation of before and after data migration_

From the early 2000s to late 2010s, Adobe Flash was a popular software platform used by web developers to create multimedia and interactive content. In 2020, support for Adobe Flash was discontinued and the ‘SWF’ format used by Adobe Flash programs became defunct. As a result, much of the content created during this era is inaccessible to consumers. This created an opportunity for a project to migrate this data to a format that is universally supported by modern computers and preserve an important part of internet history.

Using the now-defunct popular online game platform _Club Penguin_ as an example, I set about constructing an archive of the platform’s library of music. The platform’s audio tracks were contained in Adobe Flash ‘SWF’ files, and the discontinuation of support for Adobe Flash resulted in the inability to access or play music stored in this codec.

Multiple community-run websites maintained datasets throughout the life of the platform, recording metadata about each music track released by the platform, and a copy of the SWF containing the audio. However, these datasets were maintained independently of each other, and each have data quality issues, such as missing tracks, duplicate tracks, or different titles for the same track.

![Screenshot of the initial separate datasets with inconsistencies](/assets/flash-project/01-initial-separate-datasets.png)
_Screenshot of the initial separate datasets with inconsistencies (Excerpt)_

These datasets were web scraped, joined together, and ordered by ID in a CSV file. A Python script was written to bulk download the associated SWFs grouped by ID.

![Table of tracks joined and ordered by ID (Excerpt)](/assets/flash-project/02-compiled-data-set-with-links.png)
_Table of tracks grouped by ID (Excerpt)_

![Local archive of SWF files grouped by ID (Excerpt)](/assets/flash-project/03a-downloaded-swfs.png)
_Local archive of SWF files grouped by ID (Excerpt)_

While some tracks were identical across datasets, some tracks featured multiple versions due to IDs being reused when certain tracks were replaced throughout the life of the platform.

![Multiple versions of a track sharing the same ID (Excerpt)](/assets/flash-project/03c-downloaded-swfs-and-organised-swfs-based-on-cp-id.png)

_Multiple versions of a track sharing the same ID (Excerpt)_

Additionally, some tracks were unnamed in either dataset, or had multiple names when the datasets were combined.

![Multiple instances of a single track, with one lacking a name (Excerpt)](/assets/flash-project/03b-downloaded-swfs-and-organised-swfs-based-on-cp-id.png)
_Multiple instances of a single track, with one lacking a name (Excerpt)_

To remove unnecessary duplicate files, a script was written to compare the hashes of all files, record the aliases of tracks, and retain only one copy of a unique file. The result was a JSON dataset of all unique tracks accompanied by their respective title(s) and track ID(s).

![A JSON file including the hashes and aliases of tracks (Excerpt)](/assets/flash-project/04a-remove-duplicates-by-checking-hash.png)
_A JSON file including the hashes and aliases of tracks_

A Python script was written to carry out OS commands and utilise the following external tools via the command line. JPEXS FFDec was used to extract the audio streams of every SWF file. Due to how the SWF codec is designed, some music tracks are split into multiple audio streams. FFmpeg was used to concatenate the separate audio streams into a single MP3 file.

![A single SWF file consisting of multiple audio streams [JPEXS FFDec GUI] ](/assets/flash-project/05a-extract-mp3s-from-swfs.png)

_A single SWF file consisting of multiple audio streams [JPEXS FFDec GUI]_

![A single track split into multiple audio segments ](/assets/flash-project/05b-separate-mp3-tracks-each.png)
_A single track split into multiple audio segments_

![A collection of unique music tracks, after duplicate files are removed and separated audio segments are concatenated (Excerpt)](/assets/flash-project/06-removed-duplicate-mp3s.png)
_A collection of unique music tracks, after duplicate files are removed and separated audio segments are concatenated (Excerpt)_

![JSON dataset of the collection of unique music tracks (Excerpt)](/assets/flash-project/07-matched-with-original-cp-ids.png)
_JSON dataset of the collection of unique music tracks (Excerpt)_

A third dataset containing information on the usage of each track was restructured into JSON.
Each 'party' has a list of tracks used. Using the track ID, the respective audio file can be retrieved.

![Final datasets: tracks and parties (Excerpts)](/assets/flash-project/tracks_parties.webp)
_Final datasets: tracks and parties (Excerpts)_

## Summary

This project involved web scraping and merging incomplete datasets, and data cleaning, to produce a complete dataset of information about music tracks used by an online platform. Through writing scripts in Python and batch, utilising JPEXS FFDec and ffmpeg, an archive of Adobe Flash ‘SWF’ files was transformed into a catalogued collection of MP3s and metadata.
