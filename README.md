# O11y Base Core Datablaster
   This is the base set of configurations need to get about 100 different sourcestypes in to your Splunk Demo Environment. 

   This leverages the standalone [datablaster](https://splunk.atlassian.net/wiki/spaces/SS/pages/1078228782750/Datablaster) configurations. 

##   Steps to use: 
   1. Download the most recent binary from [repo](http://10.234.3.156/data-blaster-samples/)
   2. Clone this repo on the splunk system 
   3. Run the following command 
      chmod +x ./data-blaster-samples/data-blaster-linux-metrics
   4. Run the following command 
      nohup ./data-blaster-samples/data-blaster-linux-metrics -c ./data-blaster-samples/mix.yml &
   5. Validate no errors - run the following command
      less nohup.out 
      ^ THIS Should be an empty file
   6. check Splunk Instance 


## Authors and acknowledgment
Weidemann was the culprit for the majority of the creation of the data. 
N8 may have done some light editing and updating. 

## License
Apache 2.0

## Project status
Please contribute to add new data sources as you can see it is pretty straightforward this will be updated through time. 
