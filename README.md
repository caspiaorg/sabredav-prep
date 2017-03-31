# Caspia instructions for setup of webdav/caldav/carddav server using sabre-dav

This repository contains instructions and files needed to prepare a VirtualBox server that runs sabre-dav, for use as an offline testing source for CARDDAV development.

## Caspia modifications pre-install (do this in a Windows sabredav-prep directory)

1. Create the directory sabredav-prep, change to it. Create this README.md and update as you do steps.

2. From a bash prompt, run:
   ```bash
   wget https://github.com/fruux/sabre-dav/releases/download/3.2.2/sabredav-3.2.2.zip
   unzip sabredav-3.2.2.zip
   mkdir caspiadav
   cp SabreDAV/examples/* caspiadav/
   # ignore errors about omitting directory
   mkdir caspiadav/sql
   cp SabreDAV/examples/sql/sqlite.* caspiadav/sql/
   ```

3. edit caspiadav/calendarserver.php as follows:
   From: date_default_timezone_set('Canada/Eastern');
   To: date_default_timezone_set('America/Los_Angeles');

   From: // $baseUri = '/';
   To: $baseUri = '/calendarserver.php';

4. edit caspiadav/addressbookserver.php as follows:
   From: date_default_timezone_set('Canada/Eastern');
   To: date_default_timezone_set('America/Los_Angeles');

   From: $baseUri = '/';
   To: $baseUri = '/addressbookserver.php';

5. edit caspiadav/fileserver.php as follows:
   From: date_default_timezone_set('Canada/Eastern');
   To: date_default_timezone_set('America/Los_Angeles');

   From: $baseUri = '/';
   To: $baseUri = '/fileserver.php';

6. append to caspiadav/sql/sqlite.addressbooks.sql:
```sql
INSERT INTO addressbooks (principaluri, displayname, uri, description, synctoken) VALUES
('principals/admin','default calendar','default','','1');
```
7.	add all of the sabredav-prep files to the git repository, and upload to https://github.com/caspiaorg/sabredav-prep

## Install a debian server

1. Base server install

2. Install additional modules

3. Install sabre-dav files from vendor

4. Install Caspia installation files

5. Prep folders and databases

6. ​