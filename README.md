# IPFS video plugin for Kodi  - ***Crypticwizardry Kubo IPFS/IPNS added, IPLD support coming soon, need to configure Crypticwizardry IPFS API to support this application, otherwise working!***

Plugin to browse and play video media from IPFS.

It has a configurable gateway and a configurable root CID that you can browse.

# Installation

Currently the plugin is not part of any repository. You will have to upload a zip and in the add-ons menu choose to install from zip.

- Download the `plugin_video_ipfs.zip` file from the latest release on the [releases page](https://github.com/bneijt/ipfs-video-kodi/releases)
- Upload the zip file to your media center
- From the add-ons menu in Kodi choose "install from zip" and point kodi to the plugin_video_ipfs zip file

# Build from source

To build the package from the source seen here, I used Ubuntu 18.04.* (* meaning any version you want, I happen to have used .6) LTS (LTS meaning Lite Server edition) typed the following commands in, pressing the enter key after each one, once logged into the desired user in which I plan to build the package:
- `cd ~` or `cd`
- `sudo apt-get install python3.8 pip3 zip make build-essential git`
- `git clone https://github.com/rvnminers-A-and-N/ipfs-video-kodi.git`
- `cd ~/ipfs-video-kodi` or `cd ipfs-video-kodi`
- `pip3 install poetry setuptools_rust`
- `pip3 install --upgrade pip`
- `make package`
- `cd ~/ipfs-video-kodi/build` or `cd build`

If you wish to make a new user account for this you can do the following from your general user account on the given version of Ubuntu:
-`sudo adduser inser_your_new_username_here`
-`sudo usermod -aG sudo insert_the_new_username_from_above_here`

This will allow you to make the user, and give it sudo permissions upon password entry; from there, you can follow the rest of the command instructions as listed above in the start of this section!

Finally, from here (`~/ipfs-video-kodi/build/`), one can copy the `plugin_video_ipfs.zip` file (within the `~/ipfs-video-kodi/build/` path) to wherever you plan to access it from using the file searcher from the section within Kodi to add in add-ons by ZIP file, and you are good to go! This method can be used to make your own necessary changes to the scripts seen here; for example adding your own IPFS host like I am doing with Crypticwizardry!

The reasoning behind this is that the main branch in github is _not_ installable as a kodi package, please use the [zip from the releases](https://github.com/bneijt/ipfs-video-kodi/releases) if you want to install a zip directly from github. I will add some to this git soon with updates!

# Viewing your own content

- Install IPFS on your media player
- Use `ipfs add -r -w yourdirectory` to insert your directory, remember the resulting CID
- Configure plugin to have gateway point to `http://localhost:8080`
- Enter the CID of the directory as the root CID in the plugin configuration
- Optionally:
    - Use `ipfs name publish <cid>` to create an [IPNS](https://docs.ipfs.io/concepts/ipns/#example-ipns-setup-with-cli) record
    - Enter `ipfs/<resulting ipns url>` as the root CID in the plugin configuration

# Develop

- Create venv for development: `poetry install`
- Run the tests: `poetry run pytest`
- Build a release package: `make build`

# License information

Source code license: [GPL v.3](http://www.gnu.org/copyleft/gpl.html)

Fanart is based upon https://pixabay.com/nl/beaded-spinneweb-raagbol-web-dauw-1630493/
