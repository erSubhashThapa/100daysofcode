## Day 55, R3
### 9/12/19

- ## Node
  ### Where I left Off
  I'm trying to figure out how the timestamp should be saved to the database, what datatype it should be.

  ## MySQL Integer Range

  I kept getting this error when trying to add a unix timestamp in milliseconds to my database.
  ```bash
  ER_WARN_DATA_OUT_OF_RANGE: Out of range value for column 'time' at row 1
  ```
  I thought it was because I had my length of the datatype set wrong, but no matter how I set it, MySQL gave me an error. 

  I found out MySQL has a range limit on integers.

  >The value 3172978990 is greater than 2147483647 – the maximum value for INT – hence the error. MySQL integer types and their ranges are [listed here.](https://dev.mysql.com/doc/refman/8.0/en/integer-types.html)

  -*from [MySQL Error 1264: out of range value for column](https://stackoverflow.com/questions/14284494/mysql-error-1264-out-of-range-value-for-column)*

  [MySQl Docs Integer Types](https://dev.mysql.com/doc/refman/8.0/en/integer-types.html)

  So I could divide the milliseconds by 1000 to get seconds and round it and use that with INT(11). Or I could use BIGINT(13) which is what I did and set it to unsigned which makes the positive range higher.

  ## Storing Location
  I have the app storing a location, time, and user_id for each reality check. However the longitude and latitude are not saving the numbers after the decimals. I just realized why! Because ints don't have decimals.

  [Link To Work](https://github.com/DashBarkHuss/express_proj/commit/2ac67e2af5cdc82f4658ee20f97d8d2a57dad061)

  ## Storing Decimals
  >Use DECIMAL(8,6) for latitude (90 to -90 degrees) and DECIMAL(9,6) for longitude (180 to -180 degrees). 6 decimal places is fine for most applications. Both should be "signed" to allow for negative values.

  -*from [What is the ideal data type to use when storing latitude / longitude in a MySQL database?](https://stackoverflow.com/questions/159255/what-is-the-ideal-data-type-to-use-when-storing-latitude-longitude-in-a-mysql/27926894)*

  I changed the type and it saves correctly now, but it isn't getting all the decimals, so I might want to add more.

  ## Where I Left Off:
  I want to change the datatype for longitude and latitude to include more decimals. I need to see what happens when the user doesn't send a position.