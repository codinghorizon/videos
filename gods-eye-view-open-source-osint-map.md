---
layout: default
title: "This Open Source AI Map Feels Like A Command Room"
permalink: /gods-eye-view-open-source-osint-map/
date: 2026-08-26
---

# This Open Source AI Map Feels Like A Command Room

{% raw %}
Every figure, name and mark this video puts on screen, chased to a primary source.
Checked 26 August 2026.

## The repository

**God's Eye View, by Bilawal Sidhu, at `github.com/bilawalsidhu/gods-eye-view`.**
Described by its author as "A spy satellite simulator in your browser, except the data is
real. Live open source spatial intelligence on a photorealistic 3D globe."

- Source: https://github.com/bilawalsidhu/gods-eye-view
- Source: https://api.github.com/repos/bilawalsidhu/gods-eye-view

| On screen | Value | Where it comes from |
|---|---|---|
| stars | 5,031 | GitHub API, `stargazers_count`, 26 August 2026 |
| forks | 1,277 | GitHub API, `forks_count`, 26 August 2026 |
| licence | MIT | The repository's `LICENSE` file and its README |
| language | JavaScript | GitHub API, `language` |
| first commit | June 2026 | GitHub API, `created_at`, 22 June 2026 |
| topics | geospatial-intelligence, osint, cesium, 3d-globe, flight-tracking, webgl | GitHub API, `topics` |

Stars and forks move. They are shown as the count on the date above and the shot carries
that date in its source line.

**On the licence.** The `LICENSE` file is the MIT licence, with a note that the
third party data and assets the app reaches for are not covered by it and stay under their
own terms. GitHub's own licence detector reports `NOASSERTION` for the repository because
of that added note, so the API field and the file disagree. The file is what governs the
code, so the shot says MIT.

- Source: https://api.github.com/repos/bilawalsidhu/gods-eye-view/license

## What it puts on the map

**Thirteen live layers**, per the repository's README:

| Layer | Provider named by the repo | Access |
|---|---|---|
| Map stack | Google Photorealistic 3D Tiles, Bing aerial, OpenStreetMap | Google key required, metered billing |
| Live flights | OpenSky, adsb.lol | anonymous, credits optional |
| Military flights | adsb.lol | open |
| Live vessels | AISStream | free key |
| Satellites | CelesTrak | open |
| Earthquakes | USGS | open |
| Traffic | TomTom, OpenStreetMap | approximate without TomTom |
| CCTV mesh | city APIs | open |
| Radio | Radio Browser and broadcasters | open |
| Bikeshare | GBFS | open |
| Active fires | NASA FIRMS | free key |
| Space missions | Launch Library 2 | open, token optional |
| Mapped installations | OpenStreetMap | open |

**Bundled static datasets**, per the same README:

| On screen | Value |
|---|---|
| datacentres | 4,351 |
| dams | 704 |
| submarine cables | 712 |
| public cameras | about 800, across Austin, California and London |

- Source: https://github.com/bilawalsidhu/gods-eye-view/blob/main/README.md

## What it is built out of

- Vanilla JavaScript with Vite.
- CesiumJS, with Google Photorealistic 3D Tiles.
- The OpenAI Realtime API for hands free control, exposing 28 tools across four job
  categories: camera control, annotation, analysis queries and console operations.
- Node.js 24.14.x or 26.x to develop against.

- Source: https://github.com/bilawalsidhu/gods-eye-view/blob/main/README.md

## What it costs to run

The README separates the keys three ways, and the video's gate diagrams follow it exactly:

- **Required, metered:** a Google Maps API key, for the photorealistic 3D tiles.
- **Recommended, metered:** an OpenAI API key, for voice control and the AI readouts.
- **Free keys:** AISStream, NASA FIRMS, Launch Library 2, Cesium ion, OpenSky.
- **Premium, optional:** TomTom, for real time traffic rather than an approximation.

- Source: https://github.com/bilawalsidhu/gods-eye-view/blob/main/README.md

## What the project says it will not do

The repository states that it models events, assets, infrastructure and systems, and that
it does not build features for named person search, face recognition or tracking
individuals. It also carries a data disclaimer that its data may be delayed, incomplete,
modelled, inferred or wrong, and is not for navigation, emergency response, medical,
or investment decisions.

That is why the video's OSINT chapter draws vessels, aircraft, cameras and weather rather
than people, and says so in the narration.

- Source: https://github.com/bilawalsidhu/gods-eye-view/blob/main/README.md

## Marks used on screen

Every product named on screen carries its own published mark, taken as geometry from the
`simple-icons` package: GitHub, Google Earth, Google Maps, OpenStreetMap, NASA, TomTom,
Cesium, ESRI. The OpenAI mark is not in `simple-icons` any more and is carried as the
published blossom geometry rather than approximated.

## Not checked

- **Star and fork counts move.** Both are the figure on 26 August 2026 and are labelled
  with that date on screen.
- **The author's background.** The narration names Bilawal Sidhu and nothing else about
  him, and nothing about his history is stated on screen or in the voiceover.
- **Every readout inside the drawn map interface** — the latitude, longitude, zoom,
  bearing, feature counts, fleet sizes, job distances and rate limit gauges — is the
  video's own illustration of what such an interface shows, for a place the video does not
  name. None of them is a measurement of anything, and none of them is presented as one.
- **The freshness dials** in the source quality chapter describe what a good interface
  ought to display rather than what any particular feed currently reports.
- **Provider quality and coverage by region** are described in the narration in general
  terms. The repository says coverage varies; the video does not quantify it.
- **Weather is not one of the repository's thirteen layers**, and neither is search. The
  narration lists both among the kinds of signal a spatial tool should carry, and the video
  draws them, but no provider mark is put beside either, because the repository names none.
- **The nine layer names in the layer stack shot** are the ones the supplied narration
  lists, not the thirteen the README enumerates. Both are recorded above; the shot follows
  the words that were recorded.
- **Satellite imagery carries the Google Maps mark**, because that is the platform the
  repository's imagery is billed through. The Google Earth mark appears only where the
  narration itself says Google Earth.
{% endraw %}
