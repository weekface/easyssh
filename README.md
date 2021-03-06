# easyssh
Golang package for easy remote execution through SSH

So easy to use!

example/run.go

```
package main

import (
	"fmt"

	"github.com/weekface/easyssh"
)

func main() {
	ssh := &easyssh.MakeConfig{
		User:   "cjc",
		Server: "localhost",
		Key:    "/.ssh/id_rsa",
	}

	response, err := ssh.Run("ls")
	if err != nil {
		panic("Can't run remote command: " + err.Error())
	} else {
		fmt.Println(response)
	}
}
```

example/scp.go
```
package main

import (
	"fmt"

	"github.com/weekface/easyssh"
)

func main() {
	ssh := &easyssh.MakeConfig{
		User:   "cjc",
		Server: "localhost",
		Key:    "/.ssh/id_rsa",
	}

	err := ssh.Scp("/home/cjc/zipkin.rb")

	if err != nil {
		panic("Can't run remote command: " + err.Error())
	} else {
		fmt.Println("success")

		response, _ := ssh.Run("ls -al zipkin.rb")

		fmt.Println(response)
	}
}
```
