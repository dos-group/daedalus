# Daedalus: Self-adaptive Autoscaling for Distributed Stream Processing Systems

**Note**: This repository is a fork of the [original repository](https://github.com/pfisterb/daedalus), but with small modifications regarding the evaluation code, README, etc.

This repository contains a self-adaptive autoscaler for DSP systems called Daedalus.  Daedalus monitors a running DSP job and builds performance models to estimate the maximum processing capacity at different scale-outs. By predicting recovery times and anticipating the future workload with time series forecasting, Daedalus enables long-lived scaling actions that can process the incoming workload, achieve reasonable latencies, and minimize resource usage.

## DSP Jobs

The `dsp_jobs` directory contains three representative jobs for Apache Flink, WordCount, the Yahoo Streaming Benchmark, and a Traffic Monitoring job. It also contains WordCount for Kafka Streams. Jars for the jobs can be built using `mvn clean package`. With the `build_images.sh` script, the jobs are uploaded to images in order to be deployed in a Kubernetes cluster.

## Helm Charts

The `helm_charts` directory contains a collection of technologies required to run a DSP job. Desired technologies can be enabled in the main `values.yaml` file.
Install the enabled helm charts using:

``helm install -n [namespace] [deployment_name] [path_to_helm_charts]``

Uninstall with:

``helm uninstall -n [namespace] [deployment_name]``

## Daedalus

Before running Daedalus, adjust the configurations as desired in `config.py`. After installing the required dependencies, it can be run using:

``python main.py``
