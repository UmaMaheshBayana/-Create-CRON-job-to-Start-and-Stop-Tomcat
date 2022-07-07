# -Create-CRON-job-to-Start-and-Stop-Tomcat

# Step-1

Create **deletelog.sh** file to Remove tomcat logs

```sudo nano deletelog.sh```

Past blow command in deletelog.sh
```
#!/bin/bash

sudo rm  /opt/sanela/server/tomcat/logs/*.log 
sudo rm  /opt/sanela/server/tomcat/logs/*.txt 
sudo rm  /opt/sanela/server/tomcat/logs/catalina.out
```

Enter ```ctrl+x``` and Enter to save the deletelog.sh

Convert **deletelog.sh** file to executable format.

```chmod u+x deletelog.sh``` (the file color will change to green color)

# Step-2 

Create **tomcatstop.sh** file in home directory

```sudo nano tomcatstop.sh```

Past the below command in **tomcatstop.sh**

```
#!/bin/sh
sudo ps -ef | grep tomcat | awk '{print $2}' | xargs kill -9
```

Enter ```ctrl+x``` and Enter to save the tomcatstop.sh

Convert **tomcatstop.sh** file to executable format.

```chmod u+x tomcatstop.sh (the file color will change to green color)```

# Step-3

Create **tomcatstart.sh** file in home directory

```sudo nano tomcatstart.sh```

Past the below command in **tomcatstart.sh**

```
#!/bin/bash
sudo '/opt/sanela/server/tomcat/bin/startup.sh'
```

Enter ```ctrl+x``` and Enter to save the tomcatstart.sh

Convert **tomcatstart.sh** file to executable format.

```chmod u+x tomcatstart.sh (the file color will change to green color)```

# Step-4

Configure cron job with time, in crontab

```sudo crontab -e```

Select option **1** and the crontab file will open, past the below line in the **crontab -e** file.

```
49 14 * * * /bin/sh /home/sanela/deletelog.sh
50 14 * * * /bin/sh /home/sanela/tomcatrestart.sh 
52 14 * * * /bin/sh /home/sanela/tomcatstart.sh
```
As per the above query i am running cron job every at 2 50 PM and 2 52 PM, please find the below image to known about the formate

Enter **ctrl+x** and Enter to save the crontab file.
