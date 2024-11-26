A script to sanitise titles in EmulationStation gamelist.xml files. Should work with any setup using EmulationStation (Batocera, RetroPie, ES-DE, RetroBat)

Sometimes, after scraping, you still have some iffy-looking game names in EmulationStation; mix of hyphens and colons, bad capitalisation etc. If, like me, your OCD balks at this situation and the idea of manually tidying the mess is daunting... then this script may be of use.

## Usage ##

```
cd romdir
sanitisegl
```

This will search for gamelist.xml files under the current directory and change the contents of the `<name>` field to use *Title: Subtitle* instead of *Title - Subtitle* or *Title : Subtitle* (The French style used on ScreenScraper.fr)

You can adjust the script and change `SEARCH_DIR=` if you want to run it against a directory other than the current.

For safety the script will run in a non-destructive test-mode by default which won't change your gamelists. To update the gamelists change `TEST_MODE=true` to `TEST_MODE=false` after verifying it hasn't done anything you didn't want it to do.

> [!CAUTION]
> Any changes this makes to your gamelist will be lost if you rescrape your games and haven't set your scraper to not update name data. In this case you will need to re-run this program after each scrape.

> [!NOTE]
> This doesn't touch sortname fields. Those are safe.

## Future Plans ##

- [ ] Sanitise title-case
- [ ] Option to backup gamelist.xml
- [ ] Return articles to the start of names (eg "Dungeon, The" to "The Dungeon")
