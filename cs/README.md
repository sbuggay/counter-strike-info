# Counter-Strike 1.6

## Setting up a server

### Installation

Currently there seems to be a bug with `steamcmd` that doesn't allow the installation of cstrike (app 90) while logged in anonymously. You can log in with a real steam account in order to work around this.

```
login <username>
force_install_dir <install_dir>
app_update 90 validate
quit
```

If the install was successful, you can then run the server with this command:

```
./hlds_run -game cstrike -strictportbind +ip 0.0.0.0 -port 27015 +clientport 27005 +map de_dust2 -maxplayers 32
```

I like to put this into something like `start.sh` and have it running in a `tmux` session.

```
tmux new -s cstrike
```

[tmux cheatsheet](https://gist.github.com/henrik/1967800)

### Configuration

## Client

Counter-Strike forces mouse accel unless turned off as a launch option. Here are my launch options:

```
-noforcemparms -noforcemaccel -noforcemspd -freq 165
```

And here are a few command commands I use :

```
hud_fastswitch 1
fps_max 999
fps_override 1
```

### Commands
```
rate "100000"
cl_updaterate "102"
ex_interp "0"
fps_max	"300"
fps_override "1"
hud_fastswitch "2"
m_customaccel "0"
m_customaccel_exponent "0"
m_customaccel_max "0"
m_customaccel_scale "0"
m_rawinput "1"
cl_mousegrab "0"
gl_vsync "0" (turns off vertical sync)
gl_ansio "0" (turns off anisotrophic filtering)
```

### Launch options
- -nofbo (makes rendering similar to how it used to be and removes anti-aliasing)
- -nomsaa (only removes anti-aliasing; not needed if you use -nofbo)
- -noforcemparms (if not used, windows will uncheck "enhanced pointer precision every time you load CS)
- -freq X or possibly -refresh X (sets your refresh rate to X; command was brought back)
- -stretchaspect removes blackbars so you can use a 4:3 aspect ratio resolution in widescreen
