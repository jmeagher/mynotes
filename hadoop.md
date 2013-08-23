### The biggest hive tables (or other folders, adjust the folder as needed)

    hadoop fs -du -s /user/hive/warehouse/* | sort -g | awk '{print ($1/1024/1024/1024) " GB\t\t" $2}'

### FSCK with reduced output

    hdfs fsck / | egrep -v "^\.+$"

### Monitoring and debugging

#### Inspect heap of a running process (counts by instance, change the grep depending on the process name)

    jmap -histo:live $(jps | grep JobTracker | cut -d' ' -f1) | head -n 30

#### Inspect a java process for garbage collection stats

    jstat -gcutil -h15 $(jps | grep JobTracker | cut -d' ' -f1) 4s
    

