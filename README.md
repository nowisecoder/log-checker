# log-checker

This repository has been created to complete the task provided by Credit Susie during my interview/notice period tenuure.


# Summary of task
Our custom-build server logs different events to a file named logfile.txt. Every event has 2 entries in the file - one entry when the event was started and another when the event was finished. The entries in the file have no specific order (a finish event could occur before a start event for a given id).

Every line in the file is a JSON object containing the following event data:

id - the unique event identifier
state - whether the event was started or finished (can have values STARTED or FINISHED)
timestamp - the timestamp of the event in milliseconds
Application Server logs also have the following additional attributes:

type - type of log
host - hostname
Example contents of logfile.txt:

![download](https://user-images.githubusercontent.com/47608273/169256153-f79adab2-79b9-4c71-826b-82da94cafcfd.jpg)


In the example above, the event scsmbstgrb duration is 1491377495216 - 1491377495213 = 3ms. The longest event is scsmbstgrc (1491377495218 - 1491377495210 = 8ms).

# The program should:

Take the path to logfile.txt as an input argument
Parse the contents of logfile.txt
Flag any long events that take longer than 4ms
Write the found event details to file-based HSQLDB (http://hsqldb.org/) in the working folder
The application should create a new table if necessary and store the following values:
Event id
Event duration
Type and Host if applicable
Alert (true if the event took longer than 4ms, otherwise false)
