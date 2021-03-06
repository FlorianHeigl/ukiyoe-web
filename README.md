Ukiyo-e.org Web Site
====================

This is the new version of the Ukiyo-e.org web site. Uses a Mongodb + Elasticsearch backend. See [ukiyoe-models](https://github.com/jeresig/ukiyoe-models) for more information about the models that are used in running the site.

## ENV Variables

**Required:**

* `MONGODB_URL`: The location of the MongoDB server and database where the site's data is stored.

    Format: `mongodb://USERNAME:PASSWORD@SERVER:PORT/DATABASE`

* `ELASTICSEARCH_URL`: The location of the Elasticsearch server, where the site data is indexed.

    Format: `http://SERVER:PORT`

**Optional:**

* `NODE_ENV`: `production`

## Development

It's possible to run the Ukiyo-e.org site completely contained within [Docker](https://www.docker.com/) containers, using [Fig](http://www.fig.sh/).

To start, you'll need to [install Fig](http://www.fig.sh/install.html) on your system (and if you're on OS X, also [boot2docker](https://github.com/boot2docker/osx-installer/releases/latest) and [VirtualBox](https://www.virtualbox.org/wiki/Downloads)).

    Most recently tested with:
    Docker v1.4.1, Fig v1.0.1, boot2docker v1.4.1

After you've completed the installation you'll need to be running inside of a shell (on OS X, this is done by running: `boot2docker start`).

If you're using boot2docker on OS X you'll probably want to expose the Mongodb port. You can do this by running:

    VBoxManage modifyvm "boot2docker-vm" --natpf1 "guestmongodb,tcp,127.0.0.1,27017,,27017"

It'll make it so that connecting to Mongodb is simpler.

You'll then need to set up the Mongodb database. To start you'll need to run `fig up mongodb` to start the Mongodb server.

### Running the servers

    fig up

And that should start up a version of the site to play around with. You'll need to update the ENV Variables located in the `fig.yml` file (namely the missing passwords) if you wish to use the corresponding services.