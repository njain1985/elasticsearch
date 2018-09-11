Elasticsearch OHI for Infrastructure

Config
1. Follow comments in config.yaml

Installation
  -  cp elasticsearchOHI /var/db/newrelic-infra/custom-integrations/
  -  cp config.yaml /var/db/newrelic-infra/custom-integrations/
  -  cp elasticsearch-definition.yml /var/db/newrelic-infra/custom-integrations/
  -  cp elasticsearch.yml /etc/newrelic-infra/integrations.d/

Notes
- If you see Could not queue event: Queue is full. lines in the Infra Agent log you'll need to increase event_queue_depth in newrelic-infra.yml from it's default value of 1000
- By default the _nodes/stats endpoint returns all metrics, you might want to trim this back with the instructions here

DIY
- Install go (https://golang.org/doc/install)
- install dep (https://github.com/golang/dep) if you haven't already
- dep is on the roadmap to be part of go 1.10, it's on the Golden Path
- mkdir ${ProjectRoot}
- cd ${ProjectRoot}
- export GOPATH=${ProjectRoot}
- mkdir -p bin pkg src/source.datanerd.us/fit
- cd src/source.datanerd.us/fit
- `git clone git@source.datanerd.us:FIT/elasticsearchOHI
- cd elasticsearchOHI
- dep ensure
- go build

To Do
- Convert split and discard prefixes to regular expressions
- Allow for pattern based metric renaming
- Implement basic auth
- Implement OAuth
