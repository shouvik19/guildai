# Remote label hello

Set a label:

    >>> run("guild label 1 -s remote-run-123 -r guild-uat -y")
    Labeled 1 run(s)
    <exit 0>

    >>> run("guild runs -r guild-uat -n1")
    [1:...]  hello/hello:from-file  ...  completed  remote-run-123
    <exit 0>

Tag (prepend) a value to a label:

    >>> run("guild label --tag foo 1 -r guild-uat -y")
    Labeled 1 run(s)
    <exit 0>

    >>> run("guild runs -r guild-uat -n1")
    [1:...]  hello/hello:from-file  ...  completed  foo remote-run-123
    <exit 0>

Append a value to a label:

    >>> run("guild label --append bar 1 -r guild-uat -y")
    Labeled 1 run(s)
    <exit 0>

    >>> run("guild runs -r guild-uat -n1")
    [1:...]  hello/hello:from-file  ...  completed  foo remote-run-123 bar
    <exit 0>

Clear label for run 1:

    >>> run("guild label --clear 1 -r guild-uat -y")
    Cleared label for 1 run(s)
    <exit 0>

    >>> run("guild runs -r guild-uat -n1")
    [1:...]  hello/hello:from-file  ...  completed
    <exit 0>

Restore the original label using append:

    >>> run("guild label -a remote-run-123 -r guild-uat -y")
    Labeled 1 run(s)
    <exit 0>

    >>> run("guild runs -r guild-uat -n1")
    [1:...]  hello/hello:from-file  ...  completed  remote-run-123
    <exit 0>
