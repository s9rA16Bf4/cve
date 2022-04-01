# 2019-13623

```
In NSA Ghidra before 9.1, path traversal can occur in RestoreTask.java (from the package ghidra.app.plugin.core.archive) 
via an archive with an executable file that has an initial ../ in its filename. This allows attackers to overwrite 
arbitrary files in scenarios where an intermediate analysis result is archived for sharing with other persons. 
To achieve arbitrary code execution, one approach is to overwrite some critical Ghidra modules, e.g., the decompile module.
```

This rewrite is written in go, and contains a couple of more features then the one found over at exploit.db, for example this version allows you to pass
a file of commands to execute once the target tries to decompile an object.

## Provided tests
1. Opens a reverse shell to the attacker
2. Creates a file with the context 'I think you have a security issue' and then tries to open it with atom

## How to use
1. Download Ghidra <= 9.0.4
2. Run `go run exploit.go -s <path_to_script> -pti <path_to_ghidra_download>`
3. Everything is done now, you can try to see if it works by running the downloaded ghidra and try to decompile a file. 


### Source
* https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-13623
* https://blog.fxiao.me/ghidra/
* https://www.exploit-db.com/exploits/47231
