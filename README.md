# eutask
A EuPathDB website development utility that facilitates editing files locally,
pushing changes to a remote website, and rebuilding that remote website.

`eutask` is configuration based, which makes it easy to work with multiple
remote website instances.

## installation
Clone this repository and put its `bin` directory in your `$PATH`.

```
Usage: eutask [task..] [options]

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

## configuration
A `.eutaskrc` file defines the following properties:
* `url` The root url to the remote website (e.g., dfalke.plasmodb.org).
* `server` The server the remote website resides (e.g., ash.pcbi.upenn.edu).
* `base_project` The root SVN project for the website (e.g., ApiCommonPresenters).
* `webapp` The name of the webapp (e.g., dfalke.plasmo).
* `instance` The name of the tomcat instance (as known by `instance_manager`) (e.g., PlasmoDB).
* `PROJECT_HOME` The absolute path of the local directory containing SVN projects.
* `REMOTE_PROJECT_HOME` The absolute path of the remote directory containing SVN projects. (Optional, defaults to `$BASE_GUS/project_home`).

**Example**
```
url=dfalke.plasmodb.org
server=luffa
base_project=ApiCommonPresenters
webapp=plasmo.dfalke
instance=PlasmoDB
PROJECT_HOME=$HOME/Projects/eupathdb/project_home
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
