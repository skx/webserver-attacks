Source Repository:
    https://github.com/skx/webserver-attacks/

Mirror:
    http://git.steve.org.uk/skx/webserver-attacks



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
     Shellshock against user-agent - Regexp:'^\(\)' Field:'agent' INPUT agent:() { :;}; /bin/bash -c \ bytes:3941 date:02/Dec/2014 datetime:02/Dec/2014:13:02:49 +0000 logname:kvm-hosting.org method:GET path:/ proto:HTTP/1.1 referer:- request:GET / HTTP/1.1 rhost:176.102.38.75 status:200 time:13:02:49 timezone:+0000 user:-
     176.102.38.75



Rule Definitions
----------------

Rules are read from the following two directories, if present:

* `/etc/webserver-attacks.d/`
* `./webserver-attacks.d/`

Rules contain three things:

* A regular expression to match.
* A description to output when a match is made, and the `--verbose` flag is in-use.
* The field to match against.  (Where a field is a component of the logfile, such as `referer`, `agent`, etc.)


Rules are JSON-encoded, and should make sense.




Contribute
----------

Additional rule-submissions are welcome.


Steve
--
