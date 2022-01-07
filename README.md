#### Deprecated

This repo is deprecated, replaced by a Golang version of the same thing which is easier
to maintain and release binaries of. See here for more details: https://github.com/sourcekris/unnsk

See here for binary releases:
 - https://github.com/sourcekris/unnsk/releases/latest

## unnsk - extractor for NaShrinK NSK files

Probably a proprietary format by Nashsoft Systems of Bangalore, India. These files are DCL 
imploded with some basic header.

#### Requires

- Python 3
- Deark Archiver: https://github.com/jsummers/deark

#### Usage

```shell
usage: unnsk.py [-h] -e FILENAME [-d PATH] [-p PATH]

Extract NaShrinK Files.

optional arguments:
  -h, --help            show this help message and exit
  -e FILENAME, --extract FILENAME
                        The NSK file to extract.
  -d PATH, --destination PATH
                        An optional output folder.
  -p PATH, --deark PATH
                        Path to deark archiver in case it is not in $PATH

Please file bugs on the GitHub Issues. Thanks
```

#### Format Info

Reverse engineering of the format I found:

- 3 byte file signature: "NSK"
- 4 byte integer - Compressed data size
- 5 bytes unknown, usually:
  - '\x20\x??\x??\x26\x54'
- 4 byte integer - Uncompressed data size
- 1 byte filename length
- n bytes Filename 
- remainder - DCL Imploded payload

#### References

- Archive format information: http://fileformats.archiveteam.org/wiki/NaShrinK
- DOS Archiver: https://www.sac.sk/download/pack/nsk50.zip

#### Author

- Kris Hunt (@ctfkris)
