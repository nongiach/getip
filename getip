#!/usr/bin/python2.7
"""
      _           _
  ___| |__   __ _(_) __ _ _ __      ___
 / __| '_ \ / _` | |/ _` | '_ \    / __|
| (__| | | | (_| | | (_| | | | |  | (__
 \___|_| |_|\__,_|_|\__, |_| |_|___\___|
                    |___/     |_____|
"""

import re
import sys
import telnetlib
import urllib2

if len(sys.argv) == 1:
    print "Usage : getip patern [user | ip | promo | state | all]"
    sys.exit(1)

grep =  re.compile(sys.argv[1])

mfunc = {
        "all"   : (lambda line : line.replace("\n", "")),
        "user"      : (lambda line : line.split(" ")[1]),
        "ip"        : (lambda line : line.split(" ")[2]),
        "promo"     : (lambda line : line.split(" ")[9]),
        "state"     : (lambda line : line.split(" ")[10].split(":")[0]),
        "client"     : (lambda line : urllib2.unquote(line.split(" ")[11].replace("\n", ""))),
        }

if len(sys.argv) < 3:
    sys.argv += ["ip"]

tn = telnetlib.Telnet("ns-server.epitech.eu", 4242)
tn.read_until("\n")
tn.write("list_users\n");

while 42:
    line = tn.read_until("\n", 1)
    if line == "" or line == "rep 002 -- cmd end\n":
        break
    if grep.search(line) != None:
        for i in sys.argv[2:]:
            if i in mfunc:
                print mfunc[i](line),
            else:
                print "Unknow", i
                sys.exit(1)
        print "\n",
