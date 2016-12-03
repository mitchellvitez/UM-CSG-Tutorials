# Airbus Maintenance

This tutorial is intended for webmasters. If you'd like to update airbus but aren't the webmaster, please contact the [CSG Webmaster](mailto:csg.webmaster@umich.edu)

This example will go over the fall break update period, so please adjust accordingly for other times

## Getting the username and password

First, ftp into the Airbus server at `/afs/umich.edu/group/a/airbus`. From now on, we'll refer to this as the `airbus` directory

Take a look at `airbus/Private/html/orms/lib`. There, you'll find a config file. Open it up, and poke around to find the username and password for the next step.

## phpMyAdmin

Use `dbHost`, `dbUser`, and `dbPass` to get into [https://webapps.itcs.umich.edu/phpmyadmin/](https://webapps.itcs.umich.edu/phpmyadmin/)

Go to the `seasons` table and insert a row. Its id should be the last two digits of the year plus the season id. For example, for fall break (200) in 2015, we use `15200`. The name should be something like `Fall Break 2015`. `open` should be the date CSG wants to open bus reservations, in this case it's `2015-10-01 00:00:00`. `close` should likewise be whenever CSG wants to close the reservation system. Take note of the `id` here, and of the previous year's `id`, since those will be helpful in the next step.

> Note: while you won't need to edit all of the tables in this db, looking over them and having a decent level of familiarity will help if issues arise

Now you transform the schedules the Airbus team gives you into db-ready data. Use [csg-airbus](https://github.com/mitchellvitez/csg-airbus) to convert from the PDF schedules to SQL `INSERT` statements. Make sure your input files are formatted the same way as `sample_eastbound.txt` and `sample_westbound.txt`. You can get the text data for each day by copying and pasting from the PDF.

Next, open the `trips` table. Paste and run the generated SQL. Do the same for westbound trips, in the `westbound` table.

Once you've made the changes, you can test them out. To check that everything is working successfully up to this point, check `https://csg.umich.edu/airbus/orms/reserve.php?trip=<TRIPID>`).

## Back to the Site

Look at `config.php` and edit its values accordingly. Airbus is now ready for business!


