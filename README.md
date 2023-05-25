# O11y Base Core Datablaster
   This is the base set of configurations need to get about 100 different sourcestypes in to your Splunk Demo Environment. 

   This leverages the standalone [datablaster](https://splunk.atlassian.net/wiki/spaces/SS/pages/1078228782750/Datablaster) configurations. 

## Steps to Use Data Generator: 
   1. Download the most recent binary from [repo](http://10.234.3.156/data-blaster-samples/)
   2. Clone this repo on the splunk system 
   3. Run the following command (you can update the data-blaster-linux-metrics you download in Step 1)
      chmod +x ./data-blaster-samples/data-blaster-linux-metrics
   4. Run the following command 
      nohup ./data-blaster-samples/data-blaster-linux-metrics -c ./data-blaster-samples/mix.yml 
   5. Validate no errors - run the following command
      less nohup.out 
      ^ THIS Should be an empty file
   6. Check Splunk Instance validate data
## Steps for Splunk Demo Usage: Install Steps: 
   7. Install Customer Command / Script 
        1. Copy the local directory content into a local app directory - (ensure the $SPLUNK_HOME/etc/apps/<APP OF YOUR CHOICE>/local/ - (PRO TIP: install in an app that has global visibility)
            1. commands.conf 
            2. savedsearches.conf
               ^ this has a set of searches that will turn on bad data for an hour and then a search will turn on good data every hour moving forward
        2. Copy the bin directory content (2 locations: $SPLUNK_HOME$/bin/scripts "|" $SPLUNK_HOME/etc/apps/<YOUR APP ABOVE>/bin/)
            1. event_status.py
    8. Dashboard for turn on / turn off of events 
        1. In the app context above (step 7) click Dashboards > New Dashboard > Edit > Source
        2. Copy the details below for a easy dashboard to turn off bad / good events 
        ```<form version="1.1">
            <label>Bad Events Management Dashboard</label>
            <fieldset submitButton="true" autoRun="false">
               <input type="dropdown" token="action">
                  <label>Choose Action</label>
                  <choice value="|eventstatus action=1">Turn on Bad Events</choice>
                  <choice value="|eventstatus action=0">Turn off Bad Events</choice>
               </input>
            </fieldset>
            <row>
               <panel>
                  <title>Script Output</title>
                  <table>
                  <search>
                     <query>$action$</query>
                     <earliest>-15m</earliest>
                     <latest>now</latest>
                  </search>
                  <option name="drilldown">none</option>
                  <option name="refresh.display">progressbar</option>
                  </table>
               </panel>
            </row>
          </form>```
        3. Click Save 
        4. Test Dashboard by selecting a value and looking at mysql02 metrics for changes in behavior
   9. Demo Monkey Components
        1. Install Demo Monkey for Chrome [link](https://chrome.google.com/webstore/detail/demomonkey/jgbhioialphpgjgofopnplfibkeehgjd)
        2. In Chrome browser > click "Demo Monkey Icon" > Dashboard
        3. Click "Upload" and select IT_troubleshooting.mnky
        


## Authors and acknowledgment
Weidemann was the culprit for the majority of the creation of the data. 
N8 may have done some light editing and updating. 

## License
Apache 2.0

## Project status
Please contribute to add new data sources as you can see it is pretty straightforward this will be updated through time. 
