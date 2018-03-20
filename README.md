# bin
Simple bash scripts that are useful, especially on the SCC cluster

### Install

- Note that you will have to personally fill in anything in angle-brackets (i.e.
  < and >) in these scripts to personalize them.
- The scripts in "cluster-bin" are intended for use from inside the cluster,
  whereas everything else is intended for local usage.
- Both the "cluster-bin" and other scripts assume you install them into a folder
  in `$HOME/bin`, but this is only important for locating the
  `filetypes-pics-models-list.txt` files for use in `copy-pics-models` and
  `sync-pics-models-only-to-local`. This is also easily changed if you want to put them
  somewhere else.

### What they do

- `cluster-bin/backup-project-to-nb`: Backs up your personal "project" folder
  into your personal "projectnb" folder.
- `cluster-bin/copy-pics-models`: Copies ONLY the filetypes in
  `filetypes-pics-models-list.txt` from your personal "projectnb" data to a
  `pics-models-only` folder in your personal "project" folder.
- `cluster-bin/grsed`: Replaces all instances of the first string argument with
  the second string argument in ALL files in ALL subfolders from the current
  working directory. Also gives you a warning listing the number of changes
  before it runs!

- `gr`: A trivial alias for using grep to find all instances of a string in all
  files in all subfolders from the current working directory.
- `grsed`: Same as the version in `cluster-bin/grsed`.
- `poorquery`: Matches regex-identified png-files (or other extensions if you
  want) anywhere on a filesystem and outputs an HTML file displaying them.
- `sync-from-scc-conflux`: Syncs everything FROM inside a folder on the SCC called
  `scc-conflux` TO a local version of that folder, but does not delete any
  files (can be made to do so).
- `sync-to-scc-conflux`: Syncs everything FROM a local version of the folder
  `scc-conflux` TO a folder on the SCC of the same name, but does not delete
  any files (can be made to do so).
- `sync-pics-models-only-to-local`: Copies ONLY the filetypes in
  `filetypes-pics-models-list.txt` FROM the `pics-models-only` folder in your
  personal "project" folder on the SCC TO a copy of the folder on your local
  machine.

### My (former) workflow

What I used to do was:

1. Run all my simulations, saving everything (including flat PNGs saved as a
   result of passing `dsPlot` to `dsSimulate`) into a folder on my personal
   "projectnb" directory. I would only save the results/plots, NOT the data,
   since I didn't need to run secondary analyses.
2. Even if I did save the data, I would then use `cluster-bin/copy-pics-models`
   to save only the plots/metadata of my recent simulations to my personal
   "project" directory.
3. I would then use `sync-pics-models-only-to-local` to
   grab an offline copy of all the plots.
4. Finally, I would use `poorquery` to quickly "slice" the plots I wanted to
   see. However, this requires that all of the varied parameters and their
   values be embedded in the filenames for ALL plots, which DynaSim does not do
   by default anymore.
