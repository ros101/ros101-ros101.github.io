---
layout: notes
---
# Michelle

A simple shell that can run custom commands.

Full sourcecode on [https://github.com/ros101/michelle](https://github.com/ros101/michelle)

```python
'''Michelle'''

import os
import subprocess
from colorama import Fore

class Michelle():
    """my Shell"""

    def __init__(self) -> None:
        """initialize the commands"""
        self.commands = {
            # prints the help
            'help': Michelle.do_help,
            # changes directory
            'cd': Michelle.do_cd,
            # lists files in the current directory
            'LIST': Michelle.do_list,
            # sums two numbers
            'ADD': Michelle.do_add,
            # quits
            'EXIT': None
        }

    def run(self) -> None:
        """Main loop"""
        while True:
            # gets the commandline
            line = input("$ ").strip()
            # skip if empty
            if not line.strip():
                continue
            # splits it in components
            parts = line.split(' ')
            # if it's not a known command...
            if not parts[0] in self.commands:
                try:
                    # ...pass it to the standard shell
                    subprocess.run(parts, check=True)
                except Exception as exception:
                    # prints errors
                    _print(exception, Fore.YELLOW)
                continue
            # EXIT is not a real command, it just breaks the loop
            if parts[0] == 'EXIT':
                break
            # if none of the above, it's a custom command
            self.commands[parts[0]](self, parts[0], parts[1:])

    def do_help(self, _a, _b):
        """executes the HELP command"""
        for command in self.commands:
            _print(command, Fore.CYAN)

    def do_cd(self, _, params):
        """executes the CD command"""
        path = ' '.join(params)
        try:
            os.chdir(os.path.abspath(path))
        except Exception:
            _print(f'cd: no such file or directory: {path}', Fore.YELLOW)

    def do_list(self, _a, _b):
        """executes the LIST command"""
        # prints sorted and colored
        for element in sorted(os.listdir()):
            _print(element, Fore.WHITE if os.path.isfile(element) else Fore.GREEN)

    def do_add(self, _, params):
        """add numbers passed as parameters"""
        total = 0
        try:
            # this is just a loop to sum numbers
            for element in params:
                total = total + int(element)
            _print(f'the sum is {total}', Fore.GREEN)
        except Exception as _:
            _print(f'invalid number: {element}', Fore.YELLOW)      

def _print(line:str, color_fg):
    """utility method to add colors"""
    print(f'{color_fg}{line}{Fore.RESET}')
```

A scan with `bandit` reveals potential vulnerabilities:

```
$ bandit michelle/shell.py
[main]	INFO	profile include tests: None
[main]	INFO	profile exclude tests: None
[main]	INFO	cli include tests: None
[main]	INFO	cli exclude tests: None
[main]	INFO	running on Python 3.9.12
Run started:2022-05-06 06:30:50.984238

Test results:
>> Issue: [B404:blacklist] Consider possible security implications associated with the subprocess module.
   Severity: Low   Confidence: High
   CWE: CWE-78 (https://cwe.mitre.org/data/definitions/78.html)
   Location: michelle/shell.py:9:0
   More Info: https://bandit.readthedocs.io/en/1.7.4/blacklists/blacklist_imports.html#b404-import-subprocess
8	import os
9	import subprocess
10	from colorama import Fore

--------------------------------------------------
>> Issue: [B603:subprocess_without_shell_equals_true] subprocess call - check for execution of untrusted input.
   Severity: Low   Confidence: High
   CWE: CWE-78 (https://cwe.mitre.org/data/definitions/78.html)
   Location: michelle/shell.py:48:20
   More Info: https://bandit.readthedocs.io/en/1.7.4/plugins/b603_subprocess_without_shell_equals_true.html
47	                    # ...pass it to the standard shell
48	                    subprocess.run(parts, check=True)
49	                except Exception as exception:

--------------------------------------------------

Code scanned:
	Total lines of code: 111
	Total lines skipped (#nosec): 0

Run metrics:
	Total issues (by severity):
		Undefined: 0
		Low: 2
		Medium: 0
		High: 0
	Total issues (by confidence):
		Undefined: 0
		Low: 0
		Medium: 0
		High: 2
Files skipped (0):
```

Such findings are expected, being this a shell.

Input validation for the custom commands would increase security and error handling. However, if any non-custom command is allowed and executed, this software remains unsafe.
