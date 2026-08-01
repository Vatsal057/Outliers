# data/ folder: put the organizer dataset here (never commit it)

This folder is where your code reads the datathon dataset from.

Everything in this folder is git-ignored on purpose. The repository is public,
and the dataset contains individual student assessment records. Committing it
(or any file made from it that still holds individual rows) would publicly
expose real children's data, and it disqualifies your submission.

## How to use it

1. Download the dataset from the NAS server/ 
2. Put the files in this `data/` folder on your own machine.
3. Have your `src/run_all.py` (or `src/run_all.R`) read from `./data/` using
   relative paths, not absolute paths like `C:\Users\...` or `/home/...`.

When judges run your code, they will put the same dataset into this folder
before running your entry point, so relative paths to `./data/` will work.
