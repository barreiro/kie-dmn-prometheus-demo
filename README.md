# Demo for monitoring DMN with Prometheus

This is a demo to evaluate the effectiveness of exposing DMN metrics over to Prometheus. 

## How to run it

### Install and run Prometheus

This demo assumes Prometheus is installed in the system. The easier way is to instal it from a package repository, like `dnf install golang-github-prometheus-prometheus`

On a terminal window, start Prometheus in this folder by running `prometheus`. It will automatically pick the settings from the `prometheus.yml` file. To re-set Prometheus simple delete the `data` folder.

### Run the demo

Start the DMN application from command line by typing `mvn clean package exec:java` 

### Analyze the system

On a browser, open [http://localhost:9090](). There will be two counters available `dmn_execute_prometheus_total` and `dmn_execute_micrometer_total` that are the same, but one is recorded directly while other is using the [micrometer.io]() metrics facade.

Prometheus functions are available. For example the function `rate(dmn_evaluation_prometheus_total[60s])` will output the number of evaluations per second over an interval of 60 seconds.
