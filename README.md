# Installation
If you don't already have Scoop, you need to install that first (using Powershell):
```
iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
```

```
scoop add bucket raisercostin https://github.com/raisercostin/raiser-scoop-bucket
scoop install picasa
scoop install picasa-starter
```

## Upgrade stuff

See https://github.com/lukesampson/scoop/wiki/App-Manifest-Autoupdate#using-autoupdate
```
powershell

#to check for upgrades
D:\home\raiser-apps\apps\scoop\current\bin\checkver.ps1 pidgin D:\home\raiser-apps\buckets\raiser-bucket
#to upgrade script
D:\home\raiser-apps\apps\scoop\current\bin\checkver.ps1 pidgin D:\home\raiser-apps\buckets\raiser-bucket -u
#to test new installer
scoop update pidgin
```

# kscript integration

To execute kotlin scripts in windows without bash

```
scoop add bucket raisercostin https://github.com/raisercostin/raiser-scoop-bucket
scoop install kscript
```

## Create a script

kello.ks
```
#!/usr/bin/env kscript

println("Hello from Kotlin!")
```

## Execute
```
> kscript kello.ks
Hello from Kotlin!

```

## Sample ls script in kotlin

ls.ks
```
#!/usr/bin/env kscript
@file:DependsOn("org.raisercostin:jedi-io_2.11:0.65")
@file:MavenRepository("raiser-repo","http://dl.bintray.com/raisercostin/maven" )

val location = org.raisercostin.jedi.Locations.file(args.getOrNull(0)?:".")
println("ls "+location.canonical())
for (arg in location.list()) {
    println("${arg.name()}")
}
```

```
kscript ls.ks .
```
