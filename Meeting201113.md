# Meeting 13.11.2020
* Skype
* 14:00–
* Rogier, Micha, Niko & Jack

## General

- Everyone will receive today a link that contains a working copy of the IKDP corpus (~230 gigabytes)
- This link expires in a week, so use it if you want the files. They will also be available through CSC's Allas service, but one also needs CSC's user account etc. for that.
- This version contains ELAN files and multimedia linked to them
  - Does not contain raw multimedia or any multimedia for sessions outside IKDP project (other dialects, Niko's older recordings etc.)
  - All ELAN files have been edited so that they have relative multimedia paths correctly set: this means clicking the file will always result in multimedia being opened, even if the corpus is at different harddisks

## About the corpus

### Workflow

- After copying the files one has to go into the main directory, `kpv`, and pull the newest files from Git.
- This is very easy with GitHub Desktop, or then by `git pull` in Terminal
- When an ELAN file is edited, one has to do:

```
git add kpv_izva20201113-01.eaf
git commit -m "testing to add a file, issue #1"
git push
````

In GitHub Desktop the principle is same: you select which file to add, then you write a commit, and send it over.

In some rare cases you may need to update a multimedia file, which is best done so that an individual file is sent over and put into a right directory. In some later stage we also may have a method to monitor automatically that the local corpus version contains all files.

There are several "views" into the corpus. For example, there are now several exports as simple text concordances, and `stats` directory contains information about unknown forms. 

Later there will also be exports that have full current annotations from FST, possibly in Korp's VRT format which we anyway need for Korp.

#### Issues

- ~~Linked files~~
- PFSX files are currently in Git. They change often even when ELAN file doesn't. It would be good to have a truly working solution for these, meaning all files open always with good preferences.
  - Solutions: leaving them out, keeping them as they are, automatically generating them with Git hooks
- **Note:**: Git hooks are important to maintain the corpus -- is it possible to get them work on Windows?
- There are currently extremely many unused tiers, which probably will never be used. 
  - **Niko proposes** that we remove most of those automatically and leave a subset that is currently in use and that we need. We have the tier types, and it is easy to create the tiers manually or automatically if someone needs them. Our elan-fst script already removes and rewrites the tiers as needed.
- **Niko also proposes** that all word-tiers are removed because they are useless, create maintenance problems (need to be updated after transcription is edited) and increase file size very much
- **Niko also proposes** that we generate reference id's automatically whenever a file is modified in a way that changes those (new annotations, split annotations, merged annotations?)
  - Works, but makes reference id's extremely unreliable outside specific versions
  - This, however, is probably how it should work anyway
  
