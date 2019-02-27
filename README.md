[![](https://img.shields.io/badge/OS-Unix-blue.svg?longCache=True)]()
[![](https://img.shields.io/pypi/v/launchd-generator.svg?maxAge=3600)](https://pypi.org/project/launchd-generator/)
[![](https://img.shields.io/npm/v/launchd-generator.svg?maxAge=3600)](https://www.npmjs.com/package/launchd-generator)
[![Travis](https://api.travis-ci.org/looking-for-a-job/launchd-generator.svg?branch=master)](https://travis-ci.org/looking-for-a-job/launchd-generator/)

#### Install
```bash
$ [sudo] npm i -g launchd-generator
```
```bash
$ [sudo] pip install launchd-generator
```

#### Features
+   generate launchd.plist from ANY script
+   define [launchd.plist keys](http://www.manpagez.com/man/5/launchd.plist/) in script comments

#### How it works
`script.py` -> `script.py.plist`, `script.sh` -> `script.sh.plist`

```
#!/usr/bin/env <interpreter>

KEY: VALUE
```

#### CLI
```bash
usage: launchd-generator script ...
```

#### Examples
`agent.sh`
```bash
#!/usr/bin/env bash
# StartInterval: 10
```

`agent.sh.plist`
```xml
<key>ProgramArguments</key>
<array>
    <string>/path/to/agent.sh</string>
    <string>/path/to/agent.sh.plist</string>
</array>
<key>StartInterval</key>
<integer>10</integer>
```

`agent.py`
```python
#!/usr/bin/env python
"""
WatchPaths: ~/Desktop
WatchPaths: ~/Downloads
"""
```

`agent.py.plist`
```xml
<key>ProgramArguments</key>
<array>
    <string>/path/to/agent.py</string>
    <string>/path/to/agent.py.plist</string>
</array>
<key>WatchPaths</key>
<array>
    <string>/Users/username/Desktop</string>
    <string>/Users/username/Downloads</string>
</array>
```

```bash
$ cd ~/Library/LaunchAgents && find . \( -name "*.sh" -o -name "*.py" \) | xargs launchd-generator
```

#### Links
+   [launchd.plist(5)](http://www.manpagez.com/man/5/launchd.plist/)

<p align="center"><a href="https://pypi.org/project/readme-md/">readme-md</a> - README.md generator</p>