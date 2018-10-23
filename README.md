# Techops October 2018 Tech Challenge

The purpose of this tech challenge is to help us evaluate your ability to analyze a problem and write a script to solve it.

We've created a fictional backup format, along with some mock backup data in the `backups` directory. Your task is to write a unix shell script that is posix-compliant and well-documented. Your script should create a CSV-formatted report listing each username, the user's last completed backup date and time, and the size of that backup. In the backups folder, there is one folder for each user, where the folder name corresponds to the the user's username.

Some backup metadata may be missing, and some users may not have had any backups. Where there is no metadata file, write `ERR` in the CSV fields for that user. For instances where the user has no backups, write `N/A`.

## Backup format

Each user has a directory and a JSON backup metadata file. The metadata has the following format:

```
{
  "username": <the username, identical to the backup directory>,
  "backups": [
    {
      "dateStarted": <UNIX timestamp of when the backup started>,
      "dateFinished": <UNIX timestamp of when the backup finished>,
      "megabytesCopied": <number of megabytes copied in this backup>
    },
    ...
  ]
}
```

Each entry in `backups` represents a single successful backup, sorted in order of when that backup started from earliest to most recent.

## Requirements

You will need functional installations of:

1. Git: https://git-scm.com/downloads
2. jq: https://stedolan.github.io/jq
3. shellcheck: https://github.com/koalaman/shellcheck
3. A text editor
4. A POSIX shell

## Notes

* **Please don't share solved challenges publicly or with other job applicants** and please don't cheat. We probably won't know... *but you would know*.
* Consult the [jq docs](https://stedolan.github.io/jq/manual/).
* Use [shellcheck](https://www.shellcheck.net/) to ensure your script is POSIX compliant.
* The order in which we receive completed challenges will not be considered when we evaluate applicants.

## Steps

1. Clone the repo locally:

```
git clone https://github.com/EFForg/techops-techchallenge-oct2018
```

2. Make note of the backup metadata format and write a script that summarizes the state of all user backups in a CSV-formatted report. For the given data, this report should look like:

```
username, most_recent_backup_completed, backup_size_mb
personA, 2018-10-19T17:51:59-07:00, 803
personB, 2018-02-06T10:21:54-07:00, 450
personC, ERR, ERR
personD, N/A, N/A
...
```

3. After you've finished your work, bundle your local repo:

```
git bundle create send2eff.bundle --all
```

4. Email the `send2eff.bundle` file to your EFF point of contact.
