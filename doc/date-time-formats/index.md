
# Ways of Working for date time formats

We often work with teams across the world, and we often work with dates and times. When we want to do technical communication, we like ways of working that are effective worldwide and are also effective for computer users.

For date formats, prefer ISO standard sortable formats over unstandard unsortable formats. Example: prefer the date format "YYYY-MM-DD" over the U.S. convention of "M/D 'YY".

For time formats, prefer ISO standard 24-hour formats over over unstandard 12-hour formats. Example: prefer "14:00" over "2:00 p.m." or "2pm" or "two o'clock".

For timezone formats, prefer abbreviations over omitting them. Example: prefer "10:00 ET" (meaning Eastern Time Zone) over "10:00" (without a time zone).

For timezones that somestimes use daylight savings, prefer using the summary zone over using the daylight-zone or not-daylight-zone. Example: prefer "ET" (meaning Eastern Time) over "EDT" (meaning Eastern Daylight Time) or "EST" (meaning Eastern Standard Time).

For date-time log formats, prefer Zulu time over local time; for example prefer "10:00:00Z" over "10:00:00 ET". There are some exceptions to this, where it's important to using logging formats in local time.

