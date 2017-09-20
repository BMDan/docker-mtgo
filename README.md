# MTGO docker image

This image provides a ready-to-play Magic The Gathering Online (MTGO) for Linux
and Mac OS X.

Join the "WineHQ Players" clan!

It is based on [i386/debian:stretch-slim](https://hub.docker.com/r/i386/debian/) and wine-staging with patches by Anton Romanov to better support MTGO:
- https://github.com/theli-ua/wine/tree/mtgo

See https://appdb.winehq.org/objectManager.php?sClass=version&iId=32007 for more information.

### Note for Mac OS X users

Mac OS X support is still under test.
Using [Homebrew](https://brew.sh/), install XQuartz, socat, and the GNU version of getopt:

```
brew cask install xquartz 
brew install socat gnu-getopt 
```
Then follow the standard usage.
Please give us feedback on https://github.com/pauleve/docker-mtgo/issues/3 (being positive or negative, with the full output of the `run-mtgo` script).

## Usage

Pull latest docker image:
```
docker pull panard/mtgo
```

Run the docker image using [run-mtgo](./run-mtgo?raw=true) helper script
```
./run-mtgo
```

The script `run-mtgo` can be installed and upgraded as follows:
```
wget -O run-mtgo https://raw.githubusercontent.com/pauleve/docker-mtgo/master/run-mtgo
chmod +x run-mtgo
```

If you want to customize wine (notably the graphics), you can use
```
./run-mtgo --winecfg
```

See
```
./run-mtgo --help
```
for other options.

## Troubleshoot

* `run-mtgo` asks me to install dotnet.

First, exits with <kbd>CTRL</kbd>+<kbd>C</kbd>
```
./run-mtgo --reset
```

* `run-mtgo` never exits, even after <kbd>CTRL</kbd>+<kbd>C</kbd>
```
docker kill mtgo_running
```


## Docker image building

```
make -C docker-wine
make
```


