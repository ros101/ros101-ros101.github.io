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
    '''my Shell'''

    def __init__(self) -> None:
        '''initialize the commands'''
        self.commands = {
            'help': Michelle.do_help,
            'cd': Michelle.do_cd,
            'LIST': Michelle.do_list,
            'ADD': Michelle.do_add,
            'EXIT': None
        }

    def run(self) -> None:
        '''Main loop'''
        while True:
            line = input("$ ").strip()
            if not line.strip():
                continue
            parts = line.split(' ')
            if not parts[0] in self.commands:
                subprocess.run(parts)
                continue
            if parts[0] == 'EXIT':
                break
            self.commands[parts[0]](self, parts[0], parts[1:])

    def do_help(self, _a, _b):
        '''executes the HELP command'''
        for command in self.commands:
            _print(command, Fore.CYAN)

    def do_cd(self, _, params):
        '''executes the CD command'''
        path = ' '.join(params)
        try:
            os.chdir(os.path.abspath(path))
        except Exception:
            _print("cd: no such file or directory: {}".format(path), Fore.YELLOW)

    def do_list(self, _a, _b):
        '''executes the LIST command'''
        for element in sorted(os.listdir()):
            _print(element, Fore.WHITE if os.path.isfile(element) else Fore.GREEN)

    def do_add(self, _, params):
        '''add numbers passed as parameters'''
        sum = 0
        try:
            for element in params:
                sum = sum + int(element)
            _print("the sum is {}".format(sum), Fore.GREEN)
        except Exception as exception:
            _print("invalid number: {}".format(element), Fore.YELLOW)

def _print(line:str, color_fg):
    '''utility method to add colors'''
    print('{color_fg}{line}{reset_fg}'.format(line = line,color_fg = color_fg, reset_fg = Fore.RESET))
```

A scan with `bandit` reveals potential vulnerabilities:

```
$ bandit michelle/shell.py
[main]	INFO	profile include tests: None
[main]	INFO	profile exclude tests: None
[main]	INFO	cli include tests: None
[main]	INFO	cli exclude tests: None
[main]	INFO	running on Python 3.9.12
Run started:2022-04-17 14:48:50.674921

Test results:
>> Issue: [B404:blacklist] Consider possible security implications associated with the subprocess module.
   Severity: Low   Confidence: High
   CWE: CWE-78 (https://cwe.mitre.org/data/definitions/78.html)
   Location: michelle/shell.py:4:0
   More Info: https://bandit.readthedocs.io/en/1.7.4/blacklists/blacklist_imports.html#b404-import-subprocess
3	import os
4	import subprocess
5
6	from colorama import Fore

--------------------------------------------------
>> Issue: [B603:subprocess_without_shell_equals_true] subprocess call - check for execution of untrusted input.
   Severity: Low   Confidence: High
   CWE: CWE-78 (https://cwe.mitre.org/data/definitions/78.html)
   Location: michelle/shell.py:30:20
   More Info: https://bandit.readthedocs.io/en/1.7.4/plugins/b603_subprocess_without_shell_equals_true.html
29	                try:
30	                    subprocess.run(parts, check=True)
31	                except Exception as exception:

--------------------------------------------------

Code scanned:
	Total lines of code: 58
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
