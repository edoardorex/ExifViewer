# EXIF Viewer

A Qt desktop application for browsing JPEG photographs and inspecting their
embedded EXIF metadata, including camera information, capture settings, and
GPS coordinates when present.

![Application interface](Cattura.PNG)

## Features

- Folder-based image browsing with previous/next navigation.
- Image preview and 90-degree preview rotation.
- EXIF fields displayed alongside the image.
- A browser link to Google Maps for available GPS metadata.
- Keyboard shortcuts and an Italian translation source.

Rotation changes the preview; the application is not an EXIF editor or a
photo-export tool.

## Build and launch

Install [Qt](https://www.qt.io/) with **Widgets** and **LinguistTools**, a
compatible C++ compiler, and CMake. Open
[ExifViewer/CMakeLists.txt](ExifViewer/CMakeLists.txt) in Qt Creator, select a
desktop kit, then build and run.

The build definition selects Qt 5 or Qt 6 and requests C++11. Qt 6 installations
have their own newer compiler requirements; follow the selected Qt kit rather
than assuming C++11 is sufficient for every Qt version.

For a command-line build with CMake 3.13 or newer and Qt discoverable:

```sh
cmake -S ExifViewer -B build
cmake --build build
```

If discovery fails, configure `CMAKE_PREFIX_PATH` for your Qt installation.
Build artifacts committed from an older development machine should not be
reused as a fresh build directory.

## Using the viewer

Choose a directory containing at least one readable **`.jpg` or `.JPG`** file
before navigating. Those are the extension filters implemented in the source;
the original description's broader `.jpeg` wording is not the current filter.

| Shortcut | Action |
| --- | --- |
| `Ctrl+O` | Select an image folder |
| `A` | Previous image |
| `D` | Next image |
| `R` | Rotate the current preview |

Google Maps navigation opens an external browser. Images without EXIF or GPS
data cannot display fields they do not contain.

## Repository guide

| Path | Purpose |
| --- | --- |
| [ExifViewer/mainwindow.cpp](ExifViewer/mainwindow.cpp) | Folder selection, preview, shortcuts, and metadata display |
| [ExifViewer/mainwindow.ui](ExifViewer/mainwindow.ui) | Qt Designer interface |
| [ExifViewer/exif.h](ExifViewer/exif.h) | Embedded easyexif parser interface and license notice |
| [ExifViewer/ExifViewer_it_IT.ts](ExifViewer/ExifViewer_it_IT.ts) | Italian translation source |

## Attribution

The original README credits **Edoardo Re, 2021**.
The embedded easyexif parser credits **Mayank Lahiri, 2010-2016**, and retains
its redistribution terms in the source.
This repository is a fork of
[edoardore/ExifViewer](https://github.com/edoardore/ExifViewer).
Original authorship and component licenses are preserved.

Discuss major changes in an issue and include appropriate tests.
