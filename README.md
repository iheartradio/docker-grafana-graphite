StatsD + Graphite + Grafana 2
---------------------------------------------

This image contains a sensible default configuration of StatsD, Graphite and Grafana, and comes bundled with an example
dashboard for monitoring [kanaloa's reactive work dipatchers](https://github.com/iheartradio/kanaloa) metrics.
There are two ways of using this image:

### Using the Docker Index ###

This image is published under [iheartradio's repository on the Docker Index](https://hub.docker.com/r/iheartradio/docker-grafana-graphite/) and all you
need as a prerequisite is having Docker installed on your machine. The container exposes the following ports:

- `80`: the Grafana web interface.
- `8125`: the StatsD port.
- `8126`: the StatsD administrative port.

To start a container with this image you just need to run the following command:

```bash
docker run -d -p 80:80 -p 8125:8125/udp -p 8126:8126 --name grafana-dashboard iheartradio/docker-grafana-graphite
```

If you already have services running on your host that are using any of these ports, you may wish to map the container
ports to whatever you want by changing left side number in the `-p` parameters. Find more details about mapping ports
in the [Docker documentation](http://docs.docker.io/use/port_redirection/#port-redirection).


### Building the image yourself ###

The Dockerfile and supporting configuration files are available in our [Github repository](https://github.com/iheartradio/docker-grafana-graphite).
This comes specially handy if you want to change any of the StatsD, Graphite or Grafana settings, or simply if you want
to know how tha image was built. The repo also has `build` and `start` scripts to make your workflow more pleasant.


### Using the Dashboards ###

Once your container is running all you need to do is:
- open your browser pointing to the host/port you just published
- login with the default username (admin) and password (admin)
- configure a new datasource to point at the Graphite metric data (URL - http://localhost:8000) and replace the default Grafana test datasource for your graphs
- then play with the dashboard at your wish...

We hope that you have a lot of fun with this image and that it serves its purpose of making your life easier.

![Reactive Dispatcher Dashboard](dashboard.png)

