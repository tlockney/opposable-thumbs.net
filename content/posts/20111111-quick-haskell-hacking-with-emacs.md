---
title: "Quick Haskell Hacking with Emacs"
date: 2011-11-11
slug: "quick-haskell-hacking-with-emacs"
tags: 
 - Haskell
 - Emacs
draft: false
---
A couple days ago I was playing around with my Emacs configuration a bit and decided to see if I could find ways to make it a more direct part of my *flow* (whatever the hell that means). For a quick sample of sorts, I threw together this little hack that let's me popup a quick Emacs window with a buffer that's already running [haskell-mode][] (I assume here that you already have it installed, if not, you can find info on the haskell-mode page). This is really a pretty silly hack and it lacks some niceties, but it has already proven handy in the last day or two.

You'll want to add the following Elisp code somewhere in your Emacs config (I have mine in a file called `~/.emacs.d/customizations/haskell.el`):

{{<highlight lisp>}}
    (defun make-quick-haskell-frame ()
      "Creates a new frame running haskell-mode."
      (make-frame '((name . "Quick Haskell")
                    (width . 120)
                    (height . 40)))
      (select-frame-by-name "Quick Haskell")
      (switch-to-buffer "Haskell")
      (haskell-mode))
{{</highlight>}}

You can test this by running `M-x make-quick-haskell-frame` within Emacs. If you see a new window with a buffer that is already in haskell-mode, you're all set. From here you can use the all the nice keybindings of this mode to play around as much as you want (e.g., type in some Haskell fragment and then hit `C-c C-l` to run load it into GHCi).

Next you'll probably want to set up a global hotkey so you can bring up this window from anywhere. I personally use [Alfred][] with the Powerpack option that gives me the ability to set up hotkeys, but I'm sure something similar will work for other options.

You'll first need to create an Applescript file with contents similar to this (you'll need to adjust the path to the `emacsclient` binary you use):

{{<highlight applescript>}}
    do shell script "/usr/local/Cellar/emacs/HEAD/Emacs.app/Contents/MacOS/bin/emacsclient \
      -n -e '(make-quick-haskell-frame)'"
{{</highlight>}}

From there you can open up Alfred, go to Features > System > Global Hotkeys and click the plus sign to create a new hotkey. I used `Ctrl-Shift-h` for mine, but use whatever you think makes sense and is unlikely to interfere with other applications or system utilities. In the "Action:" field, click on Browse and navigate to wherever you stored the Applescript file you created earlier.

Enjoy!

[haskell-mode]: http://www.haskell.org/haskellwiki/Haskell_mode_for_Emacs "Haskell Mode"
[Alfred]: http://www.alfredapp.com/ "Alfred App"