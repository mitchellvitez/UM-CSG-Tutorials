# Airbus Maintenance

This tutorial is intended for webmasters. If you'd like to update airbus but aren't the webmaster, please contact the [CSG Webmaster](mailto:csg.webmaster@umich.edu)

This example will go over the fall break update period, so please adjust accordingly for other times

## Getting the username and password

First, ftp into the Airbus server at `/afs/umich.edu/group/a/airbus`. From now on, we'll refer to this as the `airbus` directory

Take a look at `airbus/Private/html/orms/lib`. There, you'll find a config file. Open it up, and poke around to find the username and password for the next step.

## phpMyAdmin

Use `dbHost`, `dbUser`, and `dbPass` to get into [https://webapps.itcs.umich.edu/phpmyadmin/](https://webapps.itcs.umich.edu/phpmyadmin/)

Go to the `seasons` table and insert a row. Its id should be the last two digits of the year plus the season id. For example, for fall break (200) in 2015, we use `15200`. The name should be something like `Fall Break 2015`. `open` should be the date CSG wants to open bus reservations, in this case it's `2015-10-01 00:00:00`. Close should likewise be whenever CSG wants to close the reservation system. Take note of the `id` here, and of the previous year's `id`, since those will be helpful in the nest step.

> Note: while you won't need to edit all of the tables in this db, looking over them and having a decent level of familiarity will help if issues arise



