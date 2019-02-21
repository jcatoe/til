# Import A New Theme For iTerm2
>I seem to forget _every single time_ I try to install a new theme for iTerm.

[This](https://github.com/mbadolato/iTerm2-Color-Schemes) is a good repo full of themes (in the `/schemes` directory) and screenshots.

Once you find a theme you like, navigate to the directory where you will save the `.itermcolors` files. All of my styling files are saved together.

```
$ cd ~/.styling/
```

You need to get the "**Raw**" format of the the `.itermcolors` file, so click that button and copy the new link.

```
$ curl -LJO <link-you-just-copied>
```

Now that you have the **raw** file downloaded, in iTerm2, click `CMD+i` to open the `Preferences` dialog. Navigate to "Colors" and in the "Color Presets" dropdown, choose "Import...".

Navigate to where you store your `.itermcolors` files and select the one you want to import. Then you have to click "Color Presets" again and select the one you just imported. If you've imported any before, they should also show up in the list.
