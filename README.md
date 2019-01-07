# gorename
**Golang Rename in vs-code is unusable**, but it just runs golang's rename tool

the problem is that this tool often thinks it needs to search through the gopath for any dependencies that might need renaming, which is **never** what anyone pressing F2 is expecting.
Searching the git issues, I found that @prateek already commented out that global search code, but when compiling his gorename I still got the same issue. (turns out it somehow still uses the golang/x/tools package when I build it)

I reorginized the code into one package, and tested that it works, comparison with go 1.11 code shows that the tools/refactoring/rename hasn't changed since.
now renaming in vs-code works within two seconds (due to code checking and vetting done before running gorename)

## installing:
```
go install github.com/amitbet/gorename
```

original hack:
https://github.com/prateek/tools/commit/72b0e988ce6957db328582decda8829154c66545
