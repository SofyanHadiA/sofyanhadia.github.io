---
layout: post
title: Microservices in Go with Gin
categories: [go]
tags: [go, programming, rest, api, microservice, gin]
fullview: false
comments: true
---

Microservices are new ways to achieve many cool things, but actually it was not really new. Tech giant like Google, Facebook, and Amazon already use microservices for a years. Microservices is a way to take encapsualtion and application abstraction to the next level. By implementing this pattern system components can be developed in isolation, diffrent machine, diffrent language, keep sparation of concern and allow for each component tob deployed in isolation. As an instance when there is a component fail, we can fix it just by take the machine running the component down and deploy another machine running it. 
I will give a walk-through of how to create simple microservice in Go using Gin framework.

### Getting Started
First step is to wire up a foundation, we will create following items:
* server cli: entry point of the application
* service controller: managing service, wiring up routes.
* api model: data model shared by the server, the client, and also database
* resource: grouping oh handlers to manage api requests
* http client: simple sample of http client
* unit test: you know what it is :)

### Server CLI
For now lets try to keep it simple. We just need to put run command here and some basic configuration and dependecy injection
```go
func main() {
    // not much here; it'll grow as we externalize config and add options
    svc := service.TodoService{}
    svc.Run()
}
```
### Service Controller
This is the main controller for our application. 

### API Model

### Resource

### HTTP Client

### Unit Test
