
## About

A set of critical theory terms and definitions that can be used with the
command line tool `dict.` 

Dict? Linux has a nice little command line dictionary program called `dict.` It
supports adding arbitrary dictionaries from different sources. It is a
client-server architecture that works with a program called dictd. dictd is the
dictionary `server` and `dict` is the client. this is perhaps structurally
verbose for most people's needs, but it means for example you can connect to
_remote_ database servers and display the definition on your local client. 

To install: `sudo apt-get install dict dictd dictfmt`

## Contributing

### Dictionary File Format
jargon file --> 

jargon file format:
:heading1:meaning1
:heading2:meaning2

where the "meaning" can be several kilobytes long and may contain HTML tags (it
cannot contain newline character). Both "heading" and "meaning" can contain
spaces. 

Lines  beginning with '\*', '=', or '-' are also removed.  All text
before the first headword is included in the headers.

## Compiling locally

TL;DR: `dictfmt --utf8 -s "Rhizomatic Nomadic Dictionary" -j nomadict < nomadict.txt`

------ 

Save the data in a text file, eg. mydict.txt. Then run the command:

`dictfmt --utf8 -s "My Long Dictionary Name" -j dict-name < mydict.txt`

The command will produce the files mydict.index and mydict.dict. The text
string after -s switch will be displayed as the dictionary name in the
application.

The resulting `.dict` file is formatted with headwords starting in col 0,
enclosed in colons, followed by the definition.  The colons surrounding the
headword are removed, and the headword is indexed. 

See `man dictfmt` for more info about headers, comments, etc. 

example compile command for the nomad dictionary: 
`dictfmt --utf8 -s "Rhizomatic Nomadic Dictionary" -j nomadict < nomadict.txt`


## Adding the dictionary

The above commands will compile for use with the dictd program. (`sudo apt
install dictd` or similar). Once installed and running, dictionaries can be
added/configured from the config files:

`/var/lib/dictd/db.list`
`/etc/dictd/dictd.conf`

most dictionaries are stored in `/usr/share/dictd`.

### Hosted version

Aspirational :). 

## Using

* `dict -I` will list available dictionaries, verify `nomadict` is present
* `dict -d nomadict <word>` or just `dict <word>` will search all available dictionaries. 





