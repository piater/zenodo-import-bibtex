# zenodo-import-bibtex #

Import publications from a BibTeX (`.bib`) file to
[Zenodo](https://zenodo.org/) using Zenodo's [REST
API](http://developers.zenodo.org/)

This tool attempts to make reasonable use of the BibTeX data to fill
as many of the available Zenodo metadata fields as possible.

The data models of Zenodo and BibTeX are so different that
fully-automatic import is not possible.  The result needs to be
checked, and almost always completed or corrected, and *publish*ed by
hand.

In addition to the formally-defined BibTeX fields, this script makes
use of the following:

  * `abstract` is used to fill Zenodo's *Description* field. (If it
    does not exist, `notes` is used instead, and if that is not used,
    placeholder text is inserted, since the Zenodo API requires a
    *Description* to be specified.)
  * `keyword` containing a comma-separated list of keywords
  * `doi`
  * `url` will be recorded as a *Related/alternate identifier* to an
    *identical* resource.
  * If `-p` is given and if the `url` field is present and ends in
    `.pdf`, then the tool attempts to upload the given PDF file.  It
    will take it from the directory specified via `-p`, or, if not
    found there, will attempt to download the `url`.

Author affiliations and ORCIDs can be read from a configuration file
(`$HOME/.config/zenodo-import-bibtex/config.json` by default); see the
example supplied.


## State of this Project ##

  * The script is already useful.
  * BibTeX parsing and metadata provision to Zenodo are probably
    incomplete.
  * The usage is not geared towards non-technical people.
  * The script does not check for duplicates.
