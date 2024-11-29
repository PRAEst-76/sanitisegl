A script to sanitise titles in EmulationStation gamelist.xml files. Should work with any setup using EmulationStation (Batocera, RetroPie, ES-DE, RetroBat)

Sometimes, after scraping metadata from one of the popular databases (ScreenScraper, thegamesdb, IGDB, etc.), you still have some iffy-looking game names in EmulationStation; mix of hyphens and colons, bad capitalisation etc. If, like me, your OCD balks at this situation and the idea of manually tidying the mess is daunting... then this script may be of use.

## Usage ##

First you will probably need to make the script execuitable.

```
chmod +x sanitisegl
```

Then run the script as so, substituting the path for the path to your roms or gamelists folder.

```
sanitisegl -t -d romdir/roms/
```

This will search for gamelist.xml files under the current directory and change the contents of the `<name>` field to use *Title: Subtitle* instead of *Title - Subtitle* or *Title : Subtitle* (The French style used on ScreenScraper.fr)

For safety the script will run in a non-destructive test-mode by default which won't change your gamelists. To update the gamelists after verifying it hasn't done anything you didn't want it to do...

```
sanitisegl -l -d romdir/roms
```

I'm not responsible if this script borks your gamelist, causes your hair to fall out or sparks civil war in your country.

> [!CAUTION]
> Any changes this makes to your gamelist will be lost if you rescrape your games and haven't set your scraper to not update name data. In this case you will need to re-run this program after each scrape.

> [!NOTE]
> This doesn't touch `<sortname>` fields. Those are safe.

## Future Plans ##

- [ ] Sanitise title-case
- [ ] Option to backup gamelist.xml
- [ ] Return articles to the start of names (eg "Dungeon, The" to "The Dungeon")
