Service Unavailability
Incident report for Site Outage
Issue Summary
On June 9th, 2024 from 10:05 AM to 10:15 AM WAT, the company's website was down for 10 minutes. 100% of users experienced a 500 internal server error caused by a misspelled filename in a configuration file.
Timeline
10:05 AM Sitewide update deployed; outage begins
10:07 AM Error logs checked by DevOps team
10:09 AM Configuration updated to log extra errors
10:11 AM Filename error caught in config file
10:13 AM Execute Puppet manifest across all company servers
10:15 AM 100% restored and back online
Root Cause and Resolution
After a small sitewide update was deployed without first being tested, an outage to the site began. When no errors were found in our 'error.log' files we modified our configuration file to allow for more error logging. With the help of 'strace', it appeared to be that an accidental filename misspelling triggered errors when the site was requested. The server was attempting to locate the file as normal procedure but failed to find the file ending in ".phpp", when it should be looking for ".php". After changing this line in the '/var/www/html/wp-settings.php' file, tests succeeded to show the site. A puppet manifest was written and executed across all company servers immediately after to restore service.
Corrective and Preventative Measures
After a discussion it has been decided we can prevent this in the future by:
Modifying configuration files for more error logging to quicken response times
Test before deploying on all servers no matter how small an update This is only a small incident so we are doing great! Thanks for your patience and your continued confidence in us.

