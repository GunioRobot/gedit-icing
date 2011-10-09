# gedit-icing

 Because icing on gedit tastes so much better.

 * <a href="#split-view">Split View</a>
 * <a href="#ejs.lang">ejs.lang</a>
 * <a href="#json.lang">json.lang</a>
 * <a href="#styl.lang">styl.lang</a>
 * <a href="#gedit-gists">gedit-gists</a>
 * <a href="#Inconsolata">Inconsolata</a>
 * <a href="#GMate">GMate</a>
 * <a href="#JSLint">JSLint</a>
 * <a href="#JSHint">JSHint</a>
 * <a href="#Markup%20Preview">Markup Preview</a>
 * <a href="#Zoom">Zoom</a>

## <a name="split-view" href="#split-view">Split View</a>

Visit [this site](http://eldapo.lembobrothers.com/2008/07/16/gedit-plugins-split-screen/) to learn more and for the download link.

## <a name="ejs.lang" href="#ejs.lang">ejs.lang</a>

Thanks to [@logicplace](https://github.com/logicplace)'s original [Gist](https://gist.github.com/949556).

    wget https://raw.github.com/niftylettuce/gedit-icing/master/ejs.lang \
    -O ~/.local/share/gtksourceview-2.0/language-specs/ejs.lang

 Update the mime database and enjoy EJS syntax in gedit!

    cd ~/.local/share
    update-mime-database mime

 This is much more enjoyable than having gedit recognize your `.ejs` files as plain ol' HTML!

## <a name="json.lang" href="#json.lang">json.lang</a>

Thanks to [@creationix](https://github.com/creationix).

    wget https://github.com/creationix/gedit-stuff/raw/master/lang-specs/json.lang \
    -O ~/.local/share/gtksourceview-2.0/language-specs/json.lang

Update the mime database and enjoy JSON syntax in gedit!

    cd ~/.local/share
    update-mime-database mime

## <a name="styl.lang" href="#styl.lang">styl.lang</a>

 My fork (currently pending a pull to master) of [Stylus](https://github.com/LearnBoost/stylus) has a tmp version of `styl.lang` for [GtkSourceView](http://live.gnome.org/GtkSourceView), based off [Yanekk](https://github.com/yanekk)'s [work](https://github.com/gmate/gmate/blob/master/lang-specs/scss.lang) on `scss.lang`.

 ![Stylus Language Specification for GtkSourceView](http://i.imgur.com/uBppL.png))

 This is a start and provides a basic [language spec](http://live.gnome.org/Gedit/NewLanguage) for GtkSourceView editors such as [gedit](http://projects.gnome.org/gedit/).

 **Installation Steps**

 Download `styl.lang` to your local `language-specs` folder:

    wget https://raw.github.com/niftylettuce/stylus/master/editors/gedit/styl.lang ~/.local/share/gtksourceview-2.0/language-specs/styl.lang

 Update the mime database and enjoy Stylus syntax in gedit!

    cd ~/.local/share
    update-mime-database mime

 This is much more enjoyable than having gedit recognize your `.styl` files as Apache Confs!

## <a name="gedit-gists" href="#gedit-gists">gedit-gists</a>

[View repository for gedit-gists](http://github.com/niftylettuce/gedit-gists)

## <a name="Inconsolata" href="#Inconsolata">Inconsolata</a>

 **Author:** Raph Linus ([@raphlinus](http://twitter.com/#!/raphlinus)) |
 **Source:** [http://www.levien.com/type/myfonts/inconsolata.html](http://www.levien.com/type/myfonts/inconsolata.html)

 **Description:** Best font evarrr.

 1. Install the Inconsolata font

        sudo apt-get install ttf-inconsolata

 2. Set `Editor Font` to **Inconsolata Medium 13** under the `Fonts & Colors` tab in `gedit Preferences`.

## <a name="GMate" href="#GMate">GMate</a>

 **Authors:** Andrey "A.I." Sitnik ([@andrey_sitnik](http://twitter.com/#!/andrey_sitnik)),
 Andrew Liu ([@WyndWarrior](http://twitter.com/#!/WyndWarrior)), and Sergey Rublev ([@narmaru](http://twitter.com/#!/narmaru)) |
 **Source:** [https://github.com/gmate/gmate](https://github.com/gmate/gmate)

 **Description:** Set of plugins and improvements to make Gedit a powerfull programmer text editor.

 Visit link for more information and setup.

## <a name="JSLint" href="#JSLint">JSLint</a>

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

## <a name="JSHint" href="#JSHint">JSHint</a>

 1. Install [node](https://github.com/joyent/node) and [npm](https://github.com/isaacs/npm)

 2. Enable the External Tools plugin:

    ![Enable the External Tools plugin](http://i.imgur.com/HuOOy.png)

 3. Install JSHint: `npm install -g jshint`
 
 4. Modify the `$HOME/local/node/lib/node_modules/jshint/example/config.json` file to fulfill your needs (see [node-jshint](https://github.com/jshint/node-jshint/) to learn more). You can also copy this file to another directory and change the respective path in the script below.  Soon I will add my script in here that checks for the `config.json` config file in the root of your projects directory, given that all of your projects are in the ~/Public dir.

 5. Add the following entry under `Manage External Tools` in `Tools` as `jshint`:

        #!/bin/sh
        if [ -d "$HOME/bin" ] ; then
            PATH="$HOME/bin:$PATH"
        fi
        export PATH=$HOME/local/node/bin:$PATH
        REPORTER = "$HOME/local/node/lib/node_modules/jshint/example/reporter.js"
        CONFIG = "$HOME/local/node/lib/node_modules/jshint/example/config.json"
        cat $1 >> /tmp/jshint.js
        jshint /tmp/jshint.js --reporter $REPORTER --config $CONFIG > /dev/stdout
        rm /tmp/jshint.js

 6. Select a shortcut (e.g. `CTRL+J`)

 7. Set `Save: Nothing`, `Input: Current Selection (default to document)`, and `Output: Display in bottom pane`

 8. Use the hotkey `CTRL+J` and view `Bottom Pane`'s `Shell Output` window to make your JS rock!

## <a name="Markup%20Preview" href="#Markup%20Preview">Markup Preview</a>

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

## <a name="Zoom" href="#Zoom">Zoom</a>

 **Author:** Christian Luginb&uuml;hl | **Source:** [https://github.com/dinkel/gedit-zoom](https://github.com/dinkel/gedit-zoom)

 **Description:** Gedit plugin that adds the ability to change the font size (e.g. for presentations).

 1. Clone the repository and run make target.

          git clone git://github.com/dinkel/gedit-zoom.git $HOME/.gnome2/gedit/plugins/gedit-zoom
          cd $HOME/.gnome2/gedit/plugins/gedit-zoom
          make install-dev

 2. Enable the plugin through `Edit -> Preferences -> Plugins` and make your next presentation kickin'.
