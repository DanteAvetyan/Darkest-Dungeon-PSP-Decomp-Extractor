Darkest Dungeon PSP Demake - Asset Extractor
=============================================

The demake's EBOOT.PBP contains no game data.  This tool builds the one file it needs,
assets.pak, from YOUR copy of Darkest Dungeon (Steam).  Nothing from the game is included here.

What you need
  * Darkest Dungeon (Steam) installed.
  * Python 3.9+ with Tk and Pillow   (Windows: python.org installer; then:  pip install pillow)
  * vgmstream-cli   https://github.com/vgmstream/vgmstream/releases   (download the CLI zip, unzip it)
  * ffmpeg (full build with libvorbis)   https://www.ffmpeg.org/download.html
  * SpineConverter2.1.27 (Python scripts that read the game's .skel animations); unzip it anywhere.

Run
  Windows:  double-click run.bat        Linux/macOS:  ./run.sh
  Pick the five items in the window and press Extract (about 5-10 minutes).
  Copy the resulting assets.pak into the same folder as EBOOT.PBP on the memory stick
  (ms0:/PSP/GAME/<game folder>/).

Command line (no window)
  python3 darkest/extractor/extractor.py --cli "<DarkestDungeon folder>" --vgmstream <vgmstream-cli> \
      --ffmpeg <ffmpeg> --spine <SpineConverter folder> --out assets.pak

If the PSP shows "The game data was not found in assets.pak" the pak is missing or was made by a
different version of this tool.

Menu art (optional)
  The PSP menu icon/background live inside EBOOT.PBP, not in a folder.  The window has an
  "own menu art" section: pick EBOOT.PBP, a 144x80 icon PNG and a 480x272 background PNG, press
  "Put art into EBOOT".  Command line:  python3 darkest/extractor/xmb_patch.py EBOOT.PBP --icon i.png --background b.png
