# Sentiment Analysis

This workflow analyzes a large amount of Tweets using a pre-trained Tensorflow Net, or alternatively using NLTK language corpus lookup, to determine sentiment per US state.

#### Overview

This repository contains a parallel sentiment analysis implementation, orchestrated with the Abstract Function Choreography Language and runnable on the [Apollo Engine](https://github.com/Apollo-Core)


![workflow diagram](./diagrams/workflow-slim.svg)

**Fig 1: workflow.yaml control and data flow**



#### Get the code

```
git clone https://github.com/Apollo-Workflows/Sentiment-Analysis
cd Sentiment-Analysis
```


#### Autodeploy
1. Save the credentials for your cloud provider in the according subfolder:
   - AWS: Put credential file under `aws/credentials`
   - IBM: Add `ibmcloud_api_key` to `ibm/terraform.tfvars`
2. 
   - A: Deploy to all providers:
        Run from root dir `docker run --rm -it --entrypoint=/app/deployAll.sh -v ${PWD}:/app/ chrisengelhardt/apollo-autodeploy`
   - B: Deploy single provider with custom settings:
        Run `docker run --rm -v ${PWD}:/app/ chrisengelhardt/apollo-autodeploy --help` from within the directory of your chosen cloud provider

Note: For IBM you have to create a namespace first and place it into `ibm.tf` at line `namespace = "YOURNAMESPACE"`.

```
Usage: /app/deploy.sh [--help] [--region region] [--url] [--mapping]

Commands:
        --help                  Show this help output.
        --region region         Sets a specific region for the deployment. Use a region from:
                                https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html
        --url                   Prints out all deployment urls
        --mappings              Creates typeMapping.json with the deployment urls
```


#### References

**Twitter data set**: [Z. Cheng, J. Caverlee, and K. Lee. You Are Where You Tweet: A Content-Based Approach to Geo-locating Twitter Users. In Proceeding of the 19th ACM Conference on Information and Knowledge Management (CIKM), Toronto, Oct 2010](https://archive.org/details/twitter_cikm_2010) (Accessed Dec 14 2020)

**Tensorflow Text classification model (used in `sentim-inference`):** [Text classification | Tensorflow Lite](https://www.tensorflow.org/lite/models/text_classification/overview) (Accessed Dec 22 2020)

**Textblob Library & NLTK corpora (used in `sentim-inference-textblob`)**: [sloria/TextBlob | GitHub](https://github.com/sloria/textblob) (Accessed Dec 25 2020)
