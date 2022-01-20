# createweb.pl

createweb.pl is a perl-based utility for generating a static (html-table based) website
from a set of folders, to be used with e.g. Apache with SSI enabled.

Historically it was developed by Per Marker Mortensen for use at the
Neurobiology Research Unit website nru.dk.

It has since been adapted for McStas (mcstas.org) and McXtrace
(mcxtrace.org) and other websites by Peter Willendrup.

License: GPL3

# Usage
Inputs, a set of folders:
* -c contents 
  * Contains interpreted website-content. 
  * main.html in the root will become site front page (index.html).
  * sitename in the root folder contains a top "Home" label of the generated menu.
  * Subdirectories will become pages/menu entries presented on the left in the generated menu.
  * A subdir with a matching html filename Item/Item.html will become an index page within the generated menu/site structure.
  * The menu will contain two levels of subdirectories / labels, below that level pages will include a list of links to subdirectories within.
  * If a file "siteonly" is found within a directory, the content of that directory will not be interpreted.
  * If a file "name" is found within a directory, the content will be used to label the link to the corresponding page.
  * If a file "external" is found within a directory, the content will be interpreted as an html link to an exernal page.
  * Files named "priority" are used to define the placement in the generated menu.
* -l layout 
  * header.html that defines the start of the generated html table and defines colouring etc.
  * footer.html that ends the generated html table
  * logos etc.
* -s specialcontents (non-interpreted website-content)
* -p allows to set a site URL prefix
* -w defines the output directory where the generated site with html table is placed

Example 
```
createweb.pl -c ../contents/ -s ../specialcontents/ -l ../layout/ -w /srv/web/mysite.org/wwwnew\
 -p ""
```

