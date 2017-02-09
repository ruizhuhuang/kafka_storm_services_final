Start zookeeper, kafka, storm on Wrangler using the first threes node in a reservation
Config file and individual service start script in streaming_conf
mytestapp-jar-with-dependencies.jar org.apache.storm.TwitterHashtagStorm filters twitts and counts hashtag frequency

# ssh into nimbus/master node to run storm program
ssh \$node_1 "source \$DATA/streaming/streaming_conf/env_variables.sh; \$storm_server_start_dir/storm jar /data/03076/rhuang/mytestapp-jar-with-dependencies.jar org.apache.storm.TwitterHashtagStorm  mJ4B3XXGvVqcpHfYJB5eCcbf1 fmzP5vjCXOMy053UP9TXzdAmdu2PuzDZntHEdWpyjR7Q1GqvUZ 2267758213-9Rxk6noahhJMK6XuhAPXJuLVguAUSyd70EllgQx CuR6gA6Kj2wy55t3EXTracaeNBbzVneSdpJFFVQzzhjks /data/03076/rhuang/HashTagCount.txt food"

# submit slurm job to start streaming services and run TwitterHashtagStorm
bash streaming_services_start.sh hadoop+PEMFS+2077  10:00:00 PEMFS


#Jar file:
ls /data/03076/rhuang/mytestapp-jar-with-dependencies.jar

#Submission slurm script:
ls /data/03076/rhuang/streaming_services_start.sh

#To submit streaming jobs
bash streaming_services_start.sh hadoop+PEMFS+2077  10:00:00 PEMFS
 



# Service start logs in
cd $DATA
ls streaming/log/kafka_logs/
ls streaming/log/storm_logs/
 
 
# Topology logs in
ls streaming/log/storm_logs/TwitterHashtagStorm-1-1486672420/6702/worker.log
 
ls streaming/log/storm1/nimbus/inbox/
ls streaming/log/storm2/workers/0264459a-472d-4e98-9e8f-1195a01cb480/artifacts/worker.log
ls streaming/log/storm3/workers/4369cac5-a5af-442a-b3d7-e6859d95b673/artifacts/worker.log
