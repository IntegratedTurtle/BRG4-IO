# Aufbau
├── BRG4-IO
│   ├── archetypes
│   │   └── ...
│   ├── assets
│   ├── content
│   │   ├── _index.md
│   │   ├── tutorial
│   │   │   ├── install
│   │   │   └── learncpp
│   │   └── updates
│   │       ├── anmeldung
│   │       └── start.md
│   ├── data
│   ├── hugo.toml
│   ├── i18n
│   ├── layouts
│   ├── public
│   │   └── ...
│   ├── static
│   └── themes
│       └── ink
│           └── ...
└── ...
## Erklaerung
### Content
Im content folder ist alles drin was am Ende auf der Website stehen soll.
#### _index.md
ist die Startseite, dort stehen die Infos die jeder sofort sehen sollte
#### tutorial
In diesem folder befinden sich die Seiten, die auf der website unter dem tutorial tab zu finden sein sollten.\
Die folder sind so aufgebaut, tutorial> FolderName/index.md

man kann sie aus der hugo root(der folder in dem sich hugo.toml befindet) so erstellen:
```
hugo new tutorial/$NAME$/index.md
```
Index.md wird dann auch mit den wichtigen infos ausgefuellt.
#### andere Unterordner
Sind wie tutorials, aber das man beim command nicht tutorial sondern deren namen schreibt: bzw updates
```
hugo new updates/$NAME$/index.md
```
