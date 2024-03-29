
*** This branch is dedicated to Phase 5 release ONLY! It is still work in progress ***
======================================================================================


JBoss BPM Suite & JBoss Fuse Travel Agency Integration Demo
===========================================================
Demo based on JBoss BPM Suite and JBoss Fuse products to highlight migration to micro-services. The installation
will take some time as the Fuse containers are provisioned automatically for you during the installation phase
so that the micro-services only need to be started before running the JBoss Travel Agency process.


Install on your machine
-----------------------
1. [Download and unzip.](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/archive/master.zip)

2. Add products to installs directory.

3. Run 'init.sh' or 'init.bat' file. 'init.bat' must be run with Administrative privileges.

4. Start the JBoss BPM Suite server, login, build and deploy JBoss BPM Suite process project at http://localhost:8080/business-central (u:erics/p:bpmsuite1!).

5. Add fabric server passwords for Maven Plugin to your ~/.m2/settings.xml file the fabric server's user and password so that the maven plugin can login to the fabric.

     ```
     <!-- Server login to upload to fabric. -->
     <servers>
         <server>
             <id>fabric8.upload.repo</id>
             <username>admin</username>
             <password>admin</password>
         </server>
     </servers> 
     ```

6. Start Fuse Server, by running 'fuse' or 'fuse.bat': 

7. Login to Fuse management console at:  http://localhost:8181    (u:admin/p:admin).

8. Under Runtime tab, you will see 6 containers, select and start them all.  
![Fuse Under Runtime](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/blob/master/docs/fuse-images/fuse01-underruntime.png?raw=true)

9. Check if web services are avaiable under APIs tab.
![Fuse WS APIs](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/blob/master/docs/fuse-images/fuse02-underapis.png?raw=true)

10. Enjoy the demo!


Booking a trip to Edinburgh (just one scenario)
-----------------------------------------------
1. Build & deploy project.

2. Start process with following data in start form (either from JBoss BPM Suite dashboard or using external client
	 UI deployed at [http://localhost:8080/external-client-ui-form-1.0](http://localhost:8080/external-client-ui-form-1.0)):

  ```
  Name: [your-name]

  Email Adress: [any-email]

  Number of Travellers: 2  

  From Destination: London

  To Destination: Edinburgh

  Preferred Date of Departure: 2014-12-20

  Preferred Data of Arrival: 2014-12-29

  Other Details / Notes: [any-text]
  ```

3. Login to [http://localhost:8080/business-central](http://localhost:8080/business-central)

  ```
  - login for admin role (u:erics / p:bpmsuite1!)
  ```

4. Two web services will be run and a sub-process to calculate the cost before deciding it is not needed that this booking be
	 reviewed on pricing, so you will find a task 'Employee Booking' for you to process.

5. Navigate to the "Tasks" tab and click on it. From the task in the list, click on the "Lock" icon to claim the task

6. Click on the "Work" tab from the resulting right-side pane window that opened.

7. Fill in the form provided for the task, it allows review of all the booking data submitted, generated by services and 
   calculated by the rules. You can request a review to send it back for a pricing review or check the completed box to 
   finish the task and process (isBookingConfirmed). All tasks have automated reassignment, meaning if not completed within 1 minute
   they will be put back into the group.

8. Enter credit card details (beginning with 1234...) for compensation to be triggered., Expiry details of the 
   card (e.g. 12/12) and your full name.

9. Check the logs and you will see that the process has been compensated.

10. To trigger different path for successful booking of Flights, just change the 'Credit Card details' to use any 
    card number that does not begin with 1234....

11. For details on demoing the compensation aspects of the Travel Agency demo project, 
    see [docs/compensation-howto/README-COMPENSATION.md](docs/compensation-howto/README-COMPENSATION.md)


Supporting Articles
-------------------
[A Microservices Migration Story with JBoss BPM Travel Agency (video)](http://www.schabell.org/2015/05/microservices-migration-story-with-jboss-bpm-travel-agency-video.html)

[Integration Project- Micro Services Migration Story with JBoss BPM Travel Agency - Part Five](http://wei-meilin.blogspot.tw/2015/05/integration-project-micro-services_22.html)

[Integration Project- Micro Services Migration Story with JBoss BPM Travel Agency - Part Four](http://wei-meilin.blogspot.tw/2015/05/integration-project-micro-services_19.html)

[Integration Project- Micro Services Migration Story with JBoss BPM Travel Agency - Part Three](http://wei-meilin.blogspot.nl/2015/05/integration-project-micro-services_15.html)

[Integration Project- Micro Services Migration Story with JBoss BPM Travel Agency - Part Two](http://wei-meilin.blogspot.nl/2015/05/integration-project-micro-services_11.html)

[Integration Project- Micro Services Migration Story with JBoss BPM Travel Agency - Part One](http://wei-meilin.blogspot.tw/2015/05/integration-project-micro-services.html)

[A Micro Services Migration Story with JBoss BPM Travel Agency](http://www.schabell.org/2015/05/micro-services-migration-story-with-jboss-bpm-travel-agency.html)

[Online Free PEX Webinar - A Guide to Modern BPM Tools](http://www.schabell.org/2015/04/online-free-pex-webinar-guide-to-modern-bpm-tools.html)

[Quickest Way into the Clouds with JBoss BPM Travel Agency](http://www.schabell.org/2015/02/into-clouds-with-jboss-bpm-travel-agency.html)

[Webinar - How to Excite the Travel Industry with a BPM Story](http://www.schabell.org/2015/02/webinar-how-to-excite-travel-industry.html)

[Slides from webinar - How to excite the travel industry with a BPM story](http://www.schabell.org/2015/02/slides-webinar-jboss-bpm-travel-agency.html)

[How to fly with the JBoss BPM Travel Agency (video 4 of 4)](http://www.schabell.org/2015/02/how-to-fly-with-jboss-bpm-travel-agency-part4.html)

[How to fly with the JBoss BPM Travel Agency (video 3 of 4)](http://www.schabell.org/2015/01/how-to-fly-with-jboss-bpm-travel-agency-part3.html)

[How to fly with the JBoss BPM Travel Agency (video 2 of 4)](http://www.schabell.org/2015/01/how-to-fly-with-jboss-bpm-travel-agency-part2.html)

[How to fly with the JBoss BPM Travel Agency (video 1 of 4)](http://www.schabell.org/2015/01/how-to-fly-with-jboss-bpm-travel-agency.html)

[Jump Start Your Rules, Events, Planning and BPM Today](http://www.schabell.org/2014/12/jump-start-rules-events-planning-bpm-today.html)

[3 Reasons You Need The New JBoss Travel Agency](http://www.schabell.org/2014/12/3-reasons-you-need-new-jboss-travel-agency.html)

[How To Excite the Travel Industry With a BPM Story](http://www.schabell.org/2014/10/how-to-excite-travel-agencies-with-bpm-story.html)



Released versions
-----------------
See the tagged releases for the following versions of the product:

- v1.0 - JBoss BPM Suite 6.1 and JBoss Fuse 6.1.1 with micro-service migration from traditional web services for Travel Agency project.

[![Microservices video](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/blob/master/docs/demo-images/microservices-video.png?raw=true)](https://vimeo.com/ericschabell/bpms-fuse-travel-agency-integration-demo)

![Digital Sign](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/blob/master/docs/demo-images/digital-sign.jpg?raw=true)

![Agency Process](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/blob/master/docs/demo-images/agency-process.png?raw=true)

![Calculate Process](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/blob/master/docs/demo-images/calculate-process.png?raw=true)

![Compensation](https://raw.githubusercontent.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/master/docs/demo-images/compensation-process.png?raw=true)

![Special Trips UI Form](https://raw.githubusercontent.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/master/docs/demo-images/SpecialTripsUIform.png)

![Started Process](https://raw.githubusercontent.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/master/docs/demo-images/started-process.png?raw=true)

![BPM Suite BAM](https://raw.githubusercontent.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/master/docs/demo-images/mock-bpm-data.png?raw=true)

![Fuse Under MQ Tab](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/blob/master/docs/fuse-images/fuse03-unsermq.png?raw=true)

![Fuse Message Broker Statistics](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/blob/master/docs/fuse-images/fuse04-msgbroker.png?raw=true)

![Fuse Booking Route](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/blob/master/docs/fuse-images/fuse05-bookingroute.png?raw=true)

![Fuse Cancel Booking Route](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/blob/master/docs/fuse-images/fuse06-cancelbookingroute.png?raw=true)

![Fuse Promotion FLight Route](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/blob/master/docs/fuse-images/fuse07-promotionflightroute.png?raw=true)

![Fuse Web Service Route](https://github.com/jbossdemocentral/bpms-fuse-travel-agency-integration-demo/blob/master/docs/fuse-images/fuse08-wsroute.png?raw=true)
