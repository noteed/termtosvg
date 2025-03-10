Note: the original termtosvg is no longer maintained since June 2020.

About this fork:

For live presentation, using the following command on my laptop (with a
2560x1440 screen) results in a 91x24 terminal with nice borders:

```
$ kitty -o font_size=14 -o window_padding_width=45.0 -o enable_audio_bell=no
```

I have adapted termtosvg to generate similarly looking SVGs, i.e. 2560x1440
frames with a border and big characters. The resulting PNGs or MP4s are almost
pixel-perfect when compared to the above command. So this requires using `-g
91x24`.

I have added a new template based on the Spiderman color scheme that comes with
Kitty.

When writing individual frames, this also generates a file for ffmpeg `-f
concat` feature: this allows to generate a video with accurate frame durations.


# termtosvg
termtosvg is a Unix terminal recorder written in Python that renders your command
line sessions as standalone SVG animations.

![Example](./docs/examples/awesome_window_frame_powershell.svg)

* [Gallery of examples](https://nbedos.github.io/termtosvg/pages/examples.html)
* [Gallery of templates](https://nbedos.github.io/termtosvg/pages/templates.html)

## Features
* Produce lightweight and clean looking animations or still frames embeddable on a project page
* Custom color themes, terminal UI and animation controls via user-defined [SVG templates](man/termtosvg-templates.md)
* Rendering of recordings in asciicast format made with asciinema
    
## Installation
termtosvg is compatible with Linux, macOS and BSD OSes, requires Python >= 3.5 and can be installed as follows using pip:
```shell
# Create virtualenv named '.venv'
python3 -m venv .venv
# Activate virtualenv
source .venv/bin/activate
pip3 install termtosvg
```
Then run termtosvg by calling either `termtosvg` or `python3 -m termtosvg`.

Various independently maintained, OS specific packages have been made available by the community:

| OS       | Repository  | Installation command  |
|----------|-------------|---|
| Archlinux  | [Arch](https://www.archlinux.org/packages/community/any/termtosvg/)  |`pacman -S termtosvg`   |
| FreeBSD | [ports](https://www.freshports.org/graphics/py-termtosvg) | |
| Gentoo | [media-gfx/termtosvg](https://packages.gentoo.org/packages/media-gfx/termtosvg) | `emerge media-gfx/termtosvg`|
| macOS  | [Homebrew](https://formulae.brew.sh/formula/termtosvg)  |`brew install termtosvg`   |
| OpenBSD  | [ports](https://github.com/openbsd/ports/tree/master/graphics/termtosvg)  |   |
| NixOS | [nixpkgs](https://github.com/NixOS/nixpkgs/blob/master/pkgs/tools/misc/termtosvg/) | |


## Basic usage
Start recording with:

```
$ termtosvg
Recording started, enter "exit" command or Control-D to end
```

You are now in a subshell where you can type your commands as usual.
Once you are done, exit the shell to end the recording:

```
$ exit
Recording ended, file is /tmp/termtosvg_exp5nsr4.svg
```
Then, use your favorite web browser to play the animation:
```
$ firefox /tmp/termtosvg_exp5nsr4.svg
```

Finally, embedding the animation in e.g. a [README.md](README.md) file on GitHub can
be achieved with a relative link to the animation:
```markdown
![Example](./docs/examples/awesome_window_frame.svg)
```

See the [manual page](man/termtosvg.md) for more details.

## Dependencies
termtosvg uses:
* [pyte](https://github.com/selectel/pyte) to render the terminal screen
* [lxml](https://github.com/lxml/lxml) to work with SVG data
