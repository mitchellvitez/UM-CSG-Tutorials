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

Next, open the `trips` table. I recommend you export this table as some sort of file to be reuploaded later, so you don't have to deal with editing tables in phpMyAdmin. I exported as `trips.csv` and opened in LibreOffice Calc, but you should use what you're comfortable with.

The next part is very straightforward, if a little tedious. Basically, now you transform the sheets CSG gives you into db-ready data. You only have to account for eastbound trips (AA to Detroit) since Airbus on the way back acts in a more open shuttle style. Make sure you have unique ids on each element, that the season number is correct, that you've only added Eastbound trips, that the trip dates are correct, and that the open time matches the reservation open time, and the close time is 6pm the day before the bus leaves (e.g. `2015-10-10 17:59:59`). Bus capacity is 48 unless decided otherwise.

Once you've made the changes, import the file back into the `trips` table.
