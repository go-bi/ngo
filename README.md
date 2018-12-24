# Usage & examples
spawn bash connecting stdin stdout and stderr to 127.0.0.1
* ngo -e "bash -li" 127.0.0.1:1337

Transfering files
* ngo localhost:1337 < file.txt
<br>Other side (listen)
* ngo -l :1337 > file.txt
<br>
AES encrypted connections,
* ngo -a foobar localhost:1337
Where "foobar" is your encryption key<br>
* ngo -a foobar -l :1337
Same thing except listen instead of connect<br><br>

For the full help run
* ngo -h

# Installation
Download the binary for your system from the releases

# Building from source
First `go get github.com/UlisseMini/ngo` then cd into the directory and run `make`
<br>then the binaries will be installed into ngo/bin, to install into your $GOBIN do `make depends` then `go install`

# Bugs
* Using the -e option holds up the socket even after the process exits (windows)
* failure to resize pty (wants \*os.File)
* Listening as raw and sending with aes causes a panic on the listening side
* Listening with --ssl not supported yet.

# TODO
* Allow for giving port and ip in other format (besides ip:port)
* ssl options --ssl-key --ssl-cert --ssl etc (maybe create cert auth for ngo?)
* pty support for windows
* Better argument parsing
