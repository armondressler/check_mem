# check_mem
# check_mem: Nagios plugin to check available memory
> obviously

The default nagios-plugins-all package doesnt seem to contain a suitable binary,
that's why this one exists now.

## Installing

Requires python3, plus the nagiosplugin and psutil modules.
```shell
pip3 install nagiosplugin
pip3 install psutil
```

Copy the check_mem script to your nagios-plugins directory (/usr/lib64/nagios/plugins on centOS7) 
and make it executable.
The check_mem_icinga2_command file contains a definition for an icinga2 CheckCommand Object for easy deployment.
 

## Features

The plugin is written according to the nagios plugin developer guidelines (https://nagios-plugins.org/doc/guidelines.html).
It returns with either 0 (OK), 1 (WARNING), 2 (CRITICAL) or 3 (UNKNOWN).
The info message prints the percentage of total memory in use, 
as well as the absolute memory used in MB. The performance data is appended to the message:

    ./check_mem --warning 80 --critical 90
    CHECKMEMORY WARNING - 81.5% (outside range 0:80) equalling 3049MB of total memory used. | available_memory_absolute=3049.1MB;;;0 available_memory_pct=81.5%;80;90;0;100



### --warning
Type: `Integer`  
Default: 80

Range to trigger a warning, "80" will set the warning range from 80-100.
"80:" will set the warning range to 0-80.


### --critical
Type: `Integer`  
Default: 90

Range to trigger a critical state.


## Licensing

Copyright 2018 armon dressler

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.