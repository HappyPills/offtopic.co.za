---
layout: post
title:  "Versioning your Go application"
permalink: /versioning-your-go-application/
date:   2016-03-15
tags:   go golang code version
---
Imagine you have a go application running in production that has been subject to a couple of updates. You open the logs but have no idea which version it is. Is this the same one as on the
live server or the one with all those bug fixes from last week?

Assuming you are not changing the executable's name on every build you could be stuck with a problem. Well, there happens to be an easy solution. Below I'll show you how you can set a `version` variable's value at compile time which you can then output to your logs on startup and also get it by giving it a `version` argument on startup:

```
$ .\main version  (or "main.exe version" for you Windows guys)
```

 So let's start. Create a main.go file and add a global string variable called `version`:

```go
package main

import "fmt"

var version string

func main() {
    fmt.Println(version)
}
```
Now let's run it:
```
$ go run main.go
```
Nothing. But expected since version was never assigned a value. Try again with `-ldflags`:

```
$ go run -ldflags "-X main.version=1.0.2" main.go
```
Success! It prints out 1.0.2. Using these flags you can update your CI server's build command to use the build number for your version number.

But what about the version argument? Queue a very impressive if statement at the start of our main method that checks if the second argument's value is "version":

```go
package main

import (
	"fmt"
	"os"
)

var version string

func main() {
	if len(os.Args) > 1 && os.Args[1] == "version" {
		fmt.Println("version", version)
		return
	}

	fmt.Println("do other stuff")
}
```

Now build and run it:

```
$ go build -ldflags "-X main.version=1.0.2" main.go
$ .\main version
version 1.0.2
```
And that's it.
