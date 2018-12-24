### Repeat last command, but edit in an editor first
`fc`

### Create a long, multiline command in an editor and execute on exit
`ctrl+x+e`

### make a full path of directories/subfolders in one command
`mkdir -p /long/path/filled/with/subdirs`

### make numbered folders
`mkdir {1..20}`

### combine previous commands to make several numbered folders within other folders
`mkdir -p ./{DirA,DirB,DirC}/subdir{1..3}`
		-- DirA
		|	|-subdir1
		|	|-subdir2
		|	|-subdir3
		|
		-- DirB
		|	|-subdir1
		|	|-subdir2 ..etc

### Created a long path and want to cd into it, but to lazy to type?
`cd !$` *will cd into last argument from last command used*

### $() and <()?
`echo $(ls)` will print the output of ls to screen. Using `<()` will make the output appear to be a file. Useful for commands that only accepts files as input.

### `if` statements,`[]` and `[[]]`
*Single bracket is the older, less intuitive one and will cause issues as it will continue on evaluated to nothing `$(grep nothing /dev/null)` which would compare to `[ = '']` and your script will behave weird. Use `[[]]` instead.*

```bash
if [[ -f $logfile ]]; then
    echo "$(date +"%Y-%m-%d [%T]"):   $1" >> ${logfile};
    writeidlog "$1";
else
    touch $logfile;
    echo "$(date +"%Y-%m-%d [%T]"):   $1" >> ${logfile};
    writeidlog "$1";
fi
```
