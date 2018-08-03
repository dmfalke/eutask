# eutask

EuPathDB website development utility. Edit files locally, push to a remote
website instance, and rebuild.

`eutask` is configuration based, which makes it easy to work with multiple
remote website instances.

## installation

Clone this repository and put its `bin` directory in your `$PATH`.

## examples

### Push all local changes to a remote website instance and rebuild
```
eutask sync rebuild
```

### Push all local changes for a GUS component and run bldw for that component
```
eutask sync bldw -t WDK/View
```

### Tail log files for a remote website (using `cattail ${url} -ct`)
```
eutask log
```

### TODO
List available tasks
