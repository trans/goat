# Goat


        _))
       /* \     _~
       `;'\\__-' \_
          | )  _ \ \
         / / ``   w w
        w w


**Know what you need? It's a Goat.**

Goat is simple helper tool for Go developers who do not want
to be confined to a Go *workspace*.


## Usage

Instead of `go`, use `goat` in the very same manner.
That's pretty much all there is to it, but read "How It Works"
below to fully understand why.

Goat can work with old-school workspaces as long as a `.go`
file is added to the workspace's root directory, so, personally,
I alias `go` to `goat` in my `.profile` or `.bashrc` file, 
and just *go* from there, i.e.

```bash
    alias go=goat
```

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

And you can edit the code via the more accessible `lib` directory.

Conversely you can `ln -s lib mydomain.org/myapp` instead, if you
wish. It should work the same either way.


## Coming Soon

The next version of our friendly Goat will utilize the `.go` file
more project metadata. In paritcular project dependencies, with
which the goat will be able to install them all in one fell swoop!
And maybe we'll find a few other nice things for the goat to do.


## Caveats

Perhaps it would be nice if the projects `*.go` source code files
could be in the toplevel directory, like it is for projects that
use a workspace, but linking `src/mydomain.org/myapp` to `../../..`
(the project's root), well, that might prove problematic given
all the other content. But please let me know I am wrong about that!


## Copyrights

(c) 2013 Open Bohemians, FreeBSD License

