# gedit-icing

 Because icing on gedit tastes so much better.
 
 * Inconsolata
 * GMate
 * JSLint
 * Markup Preview
 * Zoom
 
 **Wishlist:**
 
 * [gist4gedit](https://github.com/niftylettuce/nifty-web-requests#gist4gedit)
 
## Inconsolata

 **Author:** Raph Linus ([@raphlinus](http://twitter.com/#!/raphlinus)) |
 **Source:** [http://www.levien.com/type/myfonts/inconsolata.html](http://www.levien.com/type/myfonts/inconsolata.html)

 **Description:** Best font evarrr.

 1. Install the Inconsolata font
 
        sudo apt-get install ttf-inconsolata
    
 2. Set `Editor Font` to **Inconsolata Medium 13** under the `Fonts & Colors` tab in `gedit Preferences`.

## GMate

 **Authors:** Andrey "A.I." Sitnik ([@andrey_sitnik](http://twitter.com/#!/andrey_sitnik)),
 Andrew Liu ([@WyndWarrior](http://twitter.com/#!/WyndWarrior)), and Sergey Rublev ([@narmaru](http://twitter.com/#!/narmaru)) |
 **Source:** [https://github.com/gmate/gmate](https://github.com/gmate/gmate)
 
 **Description:** Set of plugins and improvements to make Gedit a powerfull programmer text editor.
 
 Visit link for more information and setup.

## JSLint

 **Author:** Uwe Jugel ([@ubunatic](http://twitter.com/#!/ubunatic)) |
 **Source:** [http://open-juve.blogspot.com/2011/04/make-jslint-working-nicely-with-gedit.html](http://open-juve.blogspot.com/2011/04/make-jslint-working-nicely-with-gedit.html)

 **Description:** Run JSLint using the hotkey `CTRL+J` in gedit.  Should we make this into a repo called `gedit-jslint`?

 1. Install Rhino JavaScript command line engine and download Rhino version of JSLint:

        sudo apt-get install rhino
        wget https://github.com/cjohansen/juicer/raw/master/lib/jslint/jslint-rhino.js $HOME/.gnome2/gedit/plugins/

 2. Enable the External Tools plugin:
 
    ![Enable the External Tools plugin](http://i.imgur.com/HuOOy.png)
    
 3. Add the following entry under `Manage External Tools` in `Tools`:
 
        #!/bin/sh
        echo "/*jslint onevar: true, undef: true, newcap: true, nomen: true, regexp: true, plusplus: true, bitwise: true, browser: true, maxerr: 50, indent: 4, white: false */" > /tmp/jslint-me.js
        cat $1 >> /tmp/jslint-me.js
        result=$(js $HOME/.gnome2/gedit/plugins/jslint-rhino.js /tmp/jslint-me.js)
        rm /tmp/jslint-me.js
        js $HOME/.gnome2/gedit/plugins/jslint-rhino-text-replace.js "$GEDIT_CURRENT_DOCUMENT_NAME" $result > /dev/stdout

 4. Select a shortcut (e.g. `CTRL+J`)
  
 5. Set `Save: Nothing` and `Input: Current Selection (default to document)`
  
 6. Copy `jslint-rhino-text-replace.js` to gedit's plugin folder:
 
        wget https://github.com/niftylettuce/gedit-icing/raw/master/jslint-rhino-text-replace.js $HOME/.gnome2/gedit/plugins/jslint-rhino-text-replace.js

 7. Use the hotkey `CTRL+J` and view `Bottom Pane`'s `Shell Output` window to achieve JS perfection.
 
    ![Achieve JS perfection](http://1.bp.blogspot.com/-aMOhOhPAFbA/TZca6h19kkI/AAAAAAAAAKs/coFncF__INA/s1600/gedit-jslint.png)

## Markup Preview

 **Authors:** Isman Firmansyah ([@iromli](http://twitter.com/#!/iromli))
 and Mihail Szabolcs ([@theicebreaker](http://twitter.com/#!/theicebreaker)) |
 **Source:** [https://github.com/iromli/gedit-markup_preview](https://github.com/iromli/gedit-markup_preview)
 
 **Description:**
 
 Preview your favorite markup using the `Bottom Pane` in gedit by using the hotkey `ALT+SHIFT+M` in gedit.
 
 We have a [feature request](https://github.com/iromli/gedit-markup_preview/issues/2) in for `File Save` event.

 1. Install Python libraries `webkit`, `markdown`, `textile`, and `docutils`:
 
        sudo apt-get install python-webkit python-markdown python-textile python-docutils
        
 2. Clone the repository and copy files using shell script:
 
        git clone git://github.com/iromli/gedit-markup_preview.git $HOME/.gnome2/gedit/plugins/gedit-markup-preview
        sh $HOME/.gnome2/gedit/plugins/gedit-markup-preview/install.sh

 3. Activate the Markup Preview plugin 

    ![Activate the Markup Preview plugin](http://i.imgur.com/zMAbr.png)
    
## Zoom

 **Author:** Christian Luginb&uuml;hl | **Source:** [https://github.com/dinkel/gedit-zoom](https://github.com/dinkel/gedit-zoom)
  
 **Description:** Gedit plugin that adds the ability to change the font size (e.g. for presentations).
  
 1. Clone the repository and run make target.
  
          git clone git://github.com/dinkel/gedit-zoom.git $HOME/.gnome2/gedit/plugins/gedit-zoom
          cd $HOME/.gnome2/gedit/plugins/gedit-zoom
          make install-dev
      
 2. Enable the plugin through `Edit -> Preferences -> Plugins` and make your next presentation kickin'.
 
