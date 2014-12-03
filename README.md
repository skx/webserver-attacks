* Source Repository:
    * https://github.com/skx/webserver-attacks/

* Mirror:
    * http://git.steve.org.uk/skx/webserver-attacks



About
-----

This repository contains a simple tool to detect and report malicious requests made against a webserver.


Usage
-----

Simply run the tool against a logfile, or set of logfiles:

     $ ./webserver-attacks *.log
     152.237.221.99
     189.26.60.153
     ..

For additional detail you can add the `--verbose` flag:

     $ ./webserver-attacks *.log --verbose
     Shellshock against user-agent - INPUT agent:() { :;}; /bin/bash -c \ bytes:2325 date:02/Dec/2014 datetime:02/Dec/2014:11:50:03 +0000 logname:blog.steve.org.uk method:GET path:/cgi-bin/dbs.cgi proto:HTTP/1.1 referer:- request:GET /cgi-bin/dbs.cgi HTTP/1.1 rhost:92.242.4.130 status:404 time:11:50:03 timezone:+0000 user:-
     92.242.4.130



Rule Definitions
----------------

Rules are read from the following two directories, if present:

* `/etc/webserver-attacks.d/`
* `./webserver-attacks.d/`

Rules contain a descriptive piece of text, then a series of regular expressions to match against particular headers.  For a rule to match each component of that rule must match.

For example you might wish to report against HTTP POST requests to missing PHP scripts, and the followign rule would do that:

     {"method":"POST","status":"404","path":"\\.php","description":"POST to missing PHP"}



Contribute
----------

Additional rule-submissions are welcome.


Steve
--
