Procedure to run the application:
---------------------------------

Prerequisites:
--------------
   Linux VM with Node.js, Memcached, Mongo DB software’s.

Procedure:
---------
1) Run memcached and mongodb servers.

2) Start alarm simulator using following command
     cd AlarmSimulator
     node app.js

3) Start Alarm Receiver using following command
     cd AlarmReceiver
     node app.js

4) Alarm Receiver will receive alarms from Simulator and store in MongoDB (if not duplicate). Open mongo client and using below commands to find alarm count and view alarms
     ./mongo
     db.alarms.count()
     db.alarms.find()

5) Start Alarm Rest Service using following command.
     cd RestAlarmService
     node app.js

6) Sample Rest URL’s to retrieve alarms
     curl http://localhost:8088/reports/AllSignals                  					/*To get All signals*/
     curl -is http://localhost:8088/reports/severity/<<Severity>>   					/*To get Signals on basis of severity*/ )ex: curl -is http://localhost:8088/reports/severity/1)
     curl -is http://localhost:8088/reports/cleared/1               					/*To get Signals which are cleared*/
     curl -is http://localhost:8088/reports/cleared/0               					/*To get Signals which are not cleared*/
     curl http://localhost:8088/reports/date/dd-mm-yyyy<<11-07-2013>>                                   /*To get Signals on basis of timestamp*/
     curl http://localhost:8088/reports/date/dd-mm-yyyy<<11-07-2013>>/dd-mm-yyyy<<11-07-2014>>        	/*To get Signals between  timestamps*/


