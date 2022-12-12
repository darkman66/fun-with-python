# Hooks

```bash
 ~/work/fun-with-python/ ll .git
total 72
18B Nov 19 15:55 COMMIT_EDITMSG
96B Dec 9 23:01 FETCH_HEAD
21B Nov 19 15:55 HEAD
41B Nov 22 17:45 ORIG_HEAD
310B Oct 16 20:46 config
73B Oct 16 20:46 description
372B Oct 29 22:05 fork-settings
480B Oct 16 20:46 hooks
1.9K Nov 22 21:58 index
96B Oct 16 20:46 info
128B Oct 16 20:46 logs
1.6K Dec 9 23:01 objects
112B Oct 16 20:46 packed-refs
160B Oct 16 20:46 refs

 ~/work/fun-with-python/ ll .git/hooks
total 120
478B Oct 16 20:46 applypatch-msg.sample
896B Oct 16 20:46 commit-msg.sample
4.6K Oct 16 20:46 fsmonitor-watchman.sample
189B Oct 16 20:46 post-update.sample
424B Oct 16 20:46 pre-applypatch.sample
1.6K Oct 16 20:46 pre-commit.sample
416B Oct 16 20:46 pre-merge-commit.sample
1.3K Oct 16 20:46 pre-push.sample
4.8K Oct 16 20:46 pre-rebase.sample
544B Oct 16 20:46 pre-receive.sample
1.5K Oct 16 20:46 prepare-commit-msg.sample
2.7K Oct 16 20:46 push-to-checkout.sample
3.6K Oct 16 20:46 update.sample
```

# pre-commit

simple pylint script

```bash
#!/bin/sh

set -e

pylint --rcfile=./config.rc 2>&1
```

improved version - only for changed files


```bash
#!/bin/sh

set -e

FILES_CHANGED=$(git diff --name-only --diff-filter=ACM origin/main  | grep "\.py" || true

if [ -n "$FILES_CHANGED" ]; then
    echo $FILES_CHANGED | xargs pylint --rcfile=./config.rc 2>&1
fi
```
