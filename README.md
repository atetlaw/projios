
# projios - PROJ as an iOS framework

[![Carthage Compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![License](http://img.shields.io/:license-mit-blue.svg)](http://doge.mit-license.org)

Uses PROJ coordinate transformation software library; Open Source Geospatial Foundation; Version 6.2.0 - https://github.com/OSGeo/PROJ

## Build
Add this repository to your projects Cartfile
```
github "atetlaw/projios"
```
and run ```carthage update```

## Usage

* Include built proj.framework into xcode project and add header
```swift
import proj
```

## Requirements

Requires `libsqlite3` (linked)

Proj 6.2.0 requires `proj.db` at runtime. [proj.db](https://github.com/atetlaw/projios/blob/master/proj.db) is the generated db file.

What I did is:
* take the file add it to my main app project
* then define the environment variable `PROJ_LIB` with the path to the dir containing the db. Added this to AppDelegate: 

```swift
setenv("PROJ_LIB", Bundle.main.bundlePath, 1)
```

If you want to generate the db file yourself:

* `$ brew install autoconf automake libtool libtiff` (if you don't have them installed like me, also 7.0 requires `libtiff`)
* `cd` to the main `proj` directory (where the proj submodule code resides)
* run `$ ./autogen.sh`
* run `$ ./configure`
* Then `cd` to the `data` dir,  where you can run `make` to generate the `proj.db` file.


## Documentation
Full proj documentation can be found at https://proj.org

## License
[MIT](https://github.com/OSGeo/PROJ/blob/master/COPYING)
