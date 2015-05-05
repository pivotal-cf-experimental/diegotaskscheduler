# Diego Task Scheduler

This is a prototype task scheduling system that allow you to send docker images hosted on e.g. Docker Hub to a running instance of Lattice.

## Installation

As this is a Clojure / Leiningen project, you need leiningen installed. This can be achieved on a Mac with homebrew like so:

```sh
brew update
brew install leiningen
```

## Running in development mode

From the home directory, run the following, replacing $YOUR_IP_HERE with the IP of your machine on the network. This is needed to allow Lattice to keep Diego Scheduler updated about finished tasks.

```sh
PORT=8080 \
API_URL=http://192.168.11.11:8888/v1 \
CALLBACK_URL="http://$YOUR_IP_HERE:8080/taskfinished" \
lein run
```

Open a browser at http://localhost:8080/. You should see a rudimentary interface for creating a Task. The defaults will result in a "Successful" docker image being downloaded and run. It will have error output in the Result column. This is because AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY have bogus values. You could replace these bogus values to have the s3copier task carry out its business properly.