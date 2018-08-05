# eutask
EuPathDB website development utility. Edit files locally, push to a remote
website instance, and rebuild.

`eutask` is configuration based, which makes it easy to work with multiple
remote website instances.

## installation
Clone this repository and put its `bin` directory in your `$PATH`.

```
Usage: eutask.js [task..] [options]

Tasks:
  sync              Push file to remote website instance.
  bld               Call bld in <target>. If <target> is not defined, defaults
                    to root GUS project.
  bldw              Build website files in <target>. If <target> is not defined,
                    defaults to root GUS project.
  wb:site           Call `wb site`.
  wb:model          Call `wb model`.
  reload            Reload the webapp.
  rebuild           Rebuild site using `rebuilder`.
  clean             Rebuild site using `rebuilder --do-aggressive-clean`. This
                    will wipe changes in the remote project_home.
  shell             Create a new shell session on remote server
  log               Tail catalina and tomcat logs on remote server

Options:
  -c, --configFile  Config file. Defaults to .eutaskrc in the first of immediate
                    or nearest ancestor directory.                      [string]
  -t, --target      GUS project (e.g., WDK) or component (e.g., WDK/View) to
                    apply tasks.                                        [string]
```

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