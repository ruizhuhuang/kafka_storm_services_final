Start zookeeper, kafka, storm on Wrangler using the first threes node in a reservation
Config file and individual service start script in streaming_conf
mytestapp-jar-with-dependencies.jar org.apache.storm.TwitterHashtagStorm filters twitts and counts hashtag frequency

# ssh into nimbus/master node to run storm program
ssh \$node_1 "source \$DATA/streaming/streaming_conf/env_variables.sh; \$storm_server_start_dir/storm jar /data/03076/rhuang/mytestapp-jar-with-dependencies.jar org.apache.storm.TwitterHashtagStorm  mJ4B3XXGvVqcpHfYJB5eCcbf1 fmzP5vjCXOMy053UP9TXzdAmdu2PuzDZntHEdWpyjR7Q1GqvUZ 2267758213-9Rxk6noahhJMK6XuhAPXJuLVguAUSyd70EllgQx CuR6gA6Kj2wy55t3EXTracaeNBbzVneSdpJFFVQzzhjks /data/03076/rhuang/HashTagCount.txt food"

# submit slurm job to start streaming services and run TwitterHashtagStorm
bash streaming_services_start.sh hadoop+PEMFS+2077  10:00:00 PEMFS

