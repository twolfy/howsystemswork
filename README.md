# How systems work

> At least for me

This is my view of how my daily Systems world works. It is not an intend to produce the most profound Systems documentation out there. It does not aim for full coverage!

It just helps me to keep an overview about topics from my daily systems tasks. How stuff is related to each other and what are the different building blocks.

## Topics to cover

### How to keep control about what is running under our responsibility?

* debugging is a lot more complex \(what are ...?\)

  * linux kernel
    * network / fs namespaces
    * routing of network packages within the linux kernel \(how do namespaces affect the normal package flow?\)
    * cgroups
    * network stages like nftables ebtables iptables?
    * how does the vfs work with ceph and trim commands?
    * debugfs to debug distributed storage?
    * pitfalls of distributed storage solutions?

  * kubernetes / container management
    * where are pitfalls?
    * how to fix ordinary problems here?
    * what are usual issues while operating a cluster?

  * docker
    * which stages does docker touch, while running an instance? is there any, or does docker just some command delegation to the linux stack?

  * why might different versions of kubernetes, linux kernel and docker be a problem? \(try to define each domain and the overlapping interfaces / area of operation\)
  * if a network package gets lost, why and how can I find the root problem?

### Basic principles

* Do data / communication verification (security rules) on the smallest layer possible
  * to make use of easy to understand principles
  * to require a general thumb of rules
  * to require to understand the real problem
  * to enforce a good design (trying to apply a general security layer will test your concept)
  * to enforce an as simple as possible solution (at least, its more probable to get a simple one)

* What are indicators for probably healthy and promising OpenSource projects?
* Principles in programming?
* Principles in infrastructure design?
* What about small scripts - are they useful? => yes they are, why?
* What about huge monolithic projects - are they useful? => yes they are, why?

### How may github and reading code of projects be integrated in my daily doing?

* while debuging problems, it often results in code reading

  * how might this get easier?
  * can I automate it a little bit more?
  * are there common questions, so I might be able to develop a common query interface?

* common projects of interest

  * gRPC \(nodejs, python, php, go\)
  * kubernetes
  * coreos/\* projects
  * prometheus
  * nagios
  * inluxdb/\* projects
  * nodejs
  * golang
  * python
  * php

### Which programming languages I'm required to be fluent in writing?

> reading programming languages should be considered as always required and quick to learn

For each language, listed here, I might gather core facts about the language and easy entry points to understand the language quickly. Also I might cover common tasks and concepts, specific for the language. A chapter about common concepts might be required too. Just to give an overview.

* golang

  * good for programs to distribute
  * high performance
  * resilient systems

* python

  * scripting / automating system related tasks
  * writing simple system daemons

* nodejs

  * writing APIs

* php

  * a lot of web apps are written in PHP, so I need to know how it works and how I might make the apps work as I want them to work

* polymer \(polymer-project from google\) \(not a language, but a key component in building web portals\)

### Package manager, their strenghts and weaknesses

* bower
* npm
* composer
* pip

### systemd

* what it does
* how does it replace previous solutions
* good use cases
* how does journald fit in relation with graylog / logstash

### logging while it's cloudy

* where is graylog positioned
* how does it differ from logstash
* how about fluentd?
  * https://cloud.google.com/solutions/real-time/fluentd-bigquery
  * http://www.fluentd.org/architecture

### modern metric gathering

* what role does prometheus play?
* how is this related to influxdb?
* why might monitoring just be analyzing datapoints?
* how about TS \(timeseries\) DBs in general? (compairson [spreadsheet](https://docs.google.com/spreadsheets/d/1sMQe9oOKhMhIVw9WmuCEWdPtAoccJ4a-IuZv4fXDHxM/edit#gid=0))
  * influxdb
  * dalmatinerdb (https://dalmatiner.io/)
  * riak ts (http://basho.com/products/riak-ts/ (why is https not default here?), [architecture overview](http://info.basho.com/rs/721-DGT-611/images/RiakTS-Enterprise-Technical-Overview.PDF))
  * prometheus \(which is also \(at first\) a monitoring system\)

### Containers

* see [Containerization](/containerization.md)

### LKVM \(Native Linux KVM Tool\) by kvmtool

> Native Linux KVM tool
>
> =====================
>
> kvmtool is a lightweight tool for hosting KVM guests. As a pure virtualization
>
> tool it only supports guests using the same architecture, though it supports
>
> running 32-bit guests on those 64-bit architectures that allow this.

\(from [here](https://kernel.googlesource.com/pub/scm/linux/kernel/git/will/kvmtool/+/3695adeb227813d96d9c41850703fb53a23845eb/README)\)

Install kvmtool via \`apt install kvmtool\`

### How distributed / scaled storage systems work with modern workload requirements

* what about object stores like Ceph, Swift and the cloud alternatives?
* what about scaling ASID compliant databases, how to scale them best?

  * where are the pitfalls and how to solve common multi-master issues?

* when not using traditional database systems, how to scale then?

  * mongodb
  * redis
  * etcd
  * confd
  * memcached

### What about backup and disaster recovery in a distributed, many replicated world?

* ....

### Systems automation

* why should I use ansible
  * in a traditional szenario \(VMs/bare metal\) it's more or less clear
  * but which role does it have in a kubernetes, autoscaling container world?
  * how might it help with CI/CD, or not help?

* [gitlab CI](https://about.gitlab.com/gitlab-ci/)
  * how does it work
  * and why is it powerful or not powerful?
  * how is it related to ansible? \(CD\)
  * how is it different to [Quay from CoreOS](https://quay.io)

* how to package software, or, do I need to build packages anymore?

### How does Machine Learning affect my daily tasks?

may I use it for...

* monitoring
* continues deployments
* continues integration
* data analyzing
* security concerns
* dependency awareness for firewalling, package management, system dependencies? \(like an alerting for complexity\)
* config analyzing to discover service relations and how a request might be resolved, just by analyzing code and data sets \(config, database 

# The second part of this book: Cloud Services

Building blocks of the Cloud

* API services which benefit from a scaled customer base like machine learning services and big data

## What does it mean, if we think about migrations into the Cloud - for my position?

* how may I need to adapt my skill sets \(back to basics, deep dive into development - extending my complexity skills\)
* how are on prem solutions affected?
* automate everything results in? \(more complexity for humans, easier access for programs, lower human interaction or better: consolidated workforce\)
  * we are currently in a time of transitions - computing gets serious

## What might come in the next 2 to 3 years in Clouding?

* machine learning prepares good / "easy" access on complex data for programs

  * we don't need to specify relations, or not all of them
  * after preparation, an operation system and its apps is just a bunch of relations \(data structures \[config syntax, databases and tables\] and context information \[config values, generated data\], like human languages\), so why should machine learning not cover maintenance and systems setups?

* automate maintenance

* automate code analysis \(for bugs and required dependencies like RDBs, Storage, Computing, other software packages\) and its deployment

# The third part of this book: Software Engineering

## Useful algorithm for...

* Sorting / Filtering a huge amount of data via Map / Reduce?
* ...

## Useful data structures

* which perform well, are "easy" search/query able
* are lightweight (in case of storage space and complexity)

## How do ASTs work?

* Which data structures are in use?
* How to query?
* How encode them for machine learning? (like natural language processing)
* How does it work with...
  * PHP
  * Python
  * Golang
  * JavaScript
* 
