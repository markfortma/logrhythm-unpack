# luca

## Description

This program is intended to unpack LogRhythm archive files (LUA and LCA) and
send them to a remote location for further review by a client.

## Usage

```
luca[.exe] [options] path/to/file.lua [path/to/file.lca path/to/ ...]

Extract matching logs from LCA and LUA files and send them to a .txt file,
directory containing .txt for each log source, or TCP/UDP/TLS endpoint.

This program does not interact with SQL Server, as such MSG-ID and HOST-ID must be
numerical.

Options:
       -h, --help
               Print this usage message
       -l, --log FILE     
               Write progress messages to FILE
       -i, --ids <FILE>
               Retrieve HOST-IDs and MSG-IDs from FILE
               
               Each line is either of the form:
               MSG-ID,MSG-ID,.. OR
               HOST-ID:MSG-ID,MSG-ID,.. OR
               HOST-ID:
       -g, --grep STRING
               Match substring within message
       -s, --start-from TIME-FMT
               TIME-FMT is of the form '1970-01-01T00:00:00', default is NOW
       -e, --end-at TIME-FMT
               TIME-FMT is of the form '2038-12-31T23:59:59', default is NOW
       -t, --threads N
               Process LUA/LCA files using N threads
       -U, --url URL
               A URL to send the matched content to, such as:
               
               file:///path/to/file.txt
               dir:///path/to/
               udp://HOST:PORT
               tcp://HOST:PORT
               tls://HOST:PORT
       -c, --confirm      
               Confirm reading of LUA files
               (Explanation: LUA files are considered hot storage. Prefer LCA, aka warm/cold)
```

## Language

Developed using Rust.

## Test Environments

### Windows

1. Windows 10
2. Windows Server 2022

### Linux

1. Fedora Server 37

## Author

[Matt Markfort](mailto:matthew.markfort@gmail.com)
