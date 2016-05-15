---
layout: post
title: My Go Micro Workflow - Setup
categories: [go]
tags: [go, programming, rest, api, microservice, gin]
fullview: false
comments: true
---

I'm using go micro now, and here is my workflow.

I have a cloud ide here : `https://c9.io/sofyan_a`. After I spawn a new ubuntu machine, then the next step is:

1. Install the latest version of golang `https://github.com/golang/go/wiki/Ubuntu`
	 Make sure you have `GOROOT` AND GOPATH set and `GOPATH/BIN `in your `PATH`
	 `export GOPATH=$HOME/workspaces/go and export PATH=$PATH:$GOPATH/bin`
	 
2. Install consul and get it running
	 Follow 
	 - https://www.consul.io/intro/getting-started/install.html
	 - https://www.consul.io/intro/getting-started/agent.html
	 Run the agent: `consul agent -dev -advertise=127.0.0.1` 
	 ^ this needs to be runing when you launch your go micro apps

3. Install protobuff 3+
	 Just grab the binary out of it and stuff it in /bin and chmod it or whatever
	 `https://github.com/google/protobuf/releases`
	 - OSX: `https://github.com/google/protobuf/releases/download/v3.0.0-beta-2/protoc-3.0.0-beta-2-osx-x86_64.zip`
	 - Linux: `https://github.com/google/protobuf/releases/download/v3.0.0-beta-2/protoc-3.0.0-beta-2-linux-x86_64.zip`

4. Install go micro's special generator plugin
	 `go get github.com/micro/protobuf/{proto,protoc-gen-go}`
	 This is so that when we write our .proto files, it will create our .pb.go file for us just by running  protoc --go_out=plugins=micro:. .

5. Install mongo, mysql, postgress and rabbit
	 Mongo: `https://docs.mongodb.org/v3.0/tutorial/install-mongodb-on-ubuntu`
	 Mysql: `apt-get install mysql-server`
	 Rabbit: `http://monkeyhacks.com/post/installing-rabbitmq-on-ubuntu-14-04`  - make sure you expose guest/guest to connections

6. Install go swagger, we use this to generate swagger.json from our restful.go file
	 `https://github.com/go-swagger/go-swagger`
	 In a folder containing rest endpoint definitions you run a command like `swagger generate spec -o ./swagger.json`

7. Clone the main repos: ***whenever you're in a go repo, you might have to run 'go get --insecure .' for it to go fetch all dependencies before 'go build' will work
	 So you just "git clone" them.. and if you go into their directory and type "go build" it will create an executable, just ./{executable-name} and ensure you pass it database flag if it asks for it

8. Kubernetes
   `go get -u k8s.io/kubernetes`
   `cd $GOPATH/src/k8s.io/kubernetes`
   `godep restore`
   
   
Happy Codding :)
