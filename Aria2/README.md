# Aria2

> aria2 is a lightweight multi-protocol & multi-source command-line download utility. It supports **HTTP/HTTPS**, **FTP**, **SFTP**, **BitTorrent** and **Metalink**. aria2 can be manipulated via built-in JSON-RPC and XML-RPC interfaces.
*<https://aria2.github.io/>*

## Installation

    brew install aria2

## Usage

```shell
# Download multiple file, you cloud specify the download directory:
aria2c [-d <your downloads dir>] "http://music.example1.com/music.mp3" "ftp://papers.example2.com/paper.pdf"
# Specify the number of connections per host:
aria2c -x <the number of connections per host> <uri | magent | torrent fiil | metalink file>
```

