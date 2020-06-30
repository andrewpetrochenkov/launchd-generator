<!--
https://readme42.com
-->



[![](https://img.shields.io/badge/OS-Unix-blue.svg?longCache=True)]()
[![](https://img.shields.io/pypi/v/launchd-generator.svg?maxAge=3600)](https://pypi.org/project/launchd-generator/)
[![](https://img.shields.io/npm/v/launchd-generator.svg?maxAge=3600)](https://www.npmjs.com/package/launchd-generator)[![](https://img.shields.io/badge/License-Unlicense-blue.svg?longCache=True)](https://unlicense.org/)
[![](https://github.com/andrewp-as-is/launchd-generator/workflows/tests42/badge.svg)](https://github.com/andrewp-as-is/launchd-generator/actions)

### Installation
```bash
$ [sudo] pip install launchd-generator
```

```bash
$ [sudo] npm i -g launchd-generator
```

#### How it works
`script.py` -> `script.py.plist`, `script.sh` -> `script.sh.plist`

```
#!/usr/bin/env <interpreter>

KEY: VALUE
CUSTOM_KEY@type: VALUE # custom key. @type required - array/bool/integer/string
```

#### Features
+   generate launchd.plist from any script
+   define [launchd.plist keys](http://www.manpagez.com/man/5/launchd.plist/) in script comments

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

#### Related
+   [`classifiers-generator` - python classifiers generator](https://pypi.org/project/classifiers-generator/)
+   [`commands-generator` - shell commands generator](https://pypi.org/project/commands-generator/)
+   [`launchd-generator` - launchd.plist generator](https://pypi.org/project/launchd-generator/)
+   [`readme-generator` - `README.md` generator](https://pypi.org/project/readme-generator/)
+   [`setupcfg-generator` - `setup.cfg` generator](https://pypi.org/project/setupcfg-generator/)
+   [`travis-generator` - `.travis.yml` generator](https://pypi.org/project/travis-generator/)

#### Links
+   [launchd.plist(5)](http://www.manpagez.com/man/5/launchd.plist/)

<p align="center">
    <a href="https://readme42.com/">readme42.com</a>
</p>