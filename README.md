Example run parameters:
==============
-f  Z:\_\googleplay\comments.csv

-u ((android login))

-p ((android password))

-e

-fu

-s

-eto email1@blinkbox.com email2@blinkbox.com

-r 4


HELP:
==============
-e,--excel                  Use EXCEL format
 
 -f,--filename <arg>         File name to save comments to, will append
 
 -fa,--all                   Fetch all available comments, One of fx is
                             required
                             
 -fd,--date <arg>            Fetch by date (takes a timestamp, One of fx
                             is required)
                             
 -fn,--number <arg>          Fetch specified number comments, One of fx is
                             required
                             
 -fr,--range <arg>           Fetch range example "1 20" will return the
                             first 20 records, use -1 to go to the end.
                             One of fx is required
                             
 -fu,--update                Fetch latest, use this to update the file,
                             One of fx is required
                             
 -h,--help                   Display usage
 
 -i,--package <arg>          Package name of the app, default is
                             com.we7.player
                             
 -m,--recovery <arg>         Time to wait before another request when a
                             429 has been issued
                             
 -p,--password <arg>         Password of the google account
 
 -s,--sort                   Sort on multiple columns (takes a comma
                             delimited string of zero based numbers e.g.
                             2,1,3)
                             
 -t,--throttle <arg>         Throttle time between requests, necessary
 
 -u,--username <arg>         Username of the google account
 
 -eto,--emailTo <arg(s)>     Email to. Multiple email addresses should be
                             separated by a space
                             
 -r,--ratingBoundary <arg>   Send email alert comprising of all star
                             ratings at this number or below (default is
                             2)

CRON JOB:
==============
00 03 * * 1-7 cd ~/commentFetcher && { java -jar comments.jar -f comments.csv -u androidwe7@gmail.com -p we7monday -e -fu -s -eto ((emails)) -r 4 > commentFetcherLog.stdout 2> commentFetcherErrors.stderr; }

30 03 * 1-7 cd ~/commentFetcher && { cp -r comments.csv /mnt/hestia/andrewb/drop/commentFetcher/ 2> copyingErrors.stderr; }

00 04 * 1-7 cd ~/commentFetcher && { cp -r comments.csv /mnt/hestia/louise/drop 2> copyingErrors.stderr; }
