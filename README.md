# Goat

**Goats eat anything!**

Goat is simple helper tool for Go developers who don't want
be confined to a Go *workspace*.


## Usage

Instead of `go`, use `goat` in the very same manner.
That's pretty much all there is to it, but read "How It Works"
below to fully understand why.

Goat can work with old-school workspaces as long as a `.go`
file is added to the workspace's root directory, so, personally,
I alias `go` to `goat` in my `.profile` or `.bashrc` file, 
and just "*go* from there".


## How It Works

Goat searches up the directory heirarchy for a `.go` file.
When it finds this file, it prepends it's locatation to
`$GOPATH`, passes the command off to `go` and restores
the old `$GOPATH` when the `go` tool is finished.

To utilize Goat your project needs to be organized like
a miniture private workspace. i.e.

    bin/
    pkg/
    src/
      mydomain.org/
        myapp/
          mycode.go

To make coding a bit more pleasent link `lib` to your projects
source.

    $ ln -s src/mydomain.org/myapp lib

So then your project looks like this:

    bin/
    lib/ -> mydomain.org/myapp/
    pkg/
    src/
      mydomain.org/
        myapp/

And you can edit the code via the more concise `lib` directory.

Conversely you can `ln -s lib mydomain.org/myapp` instead, if you
wish. It should work the same either way.


## Caveats

Perhaps it would be nice if the projects `*.go` source code files
could be in the toplevel directory, like it is for projects that
use a workspace, but linking `src/mydomain.org/myapp` to `../../..`
(the project's root), well, that might prove problematic
given all the other content. But please let me know if I am 
wrong about that!


## Copyrights

(c) 2013 Open Bohemians, FreeBSD License

