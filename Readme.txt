Apache Kafka 4.0.0— New Version released in March 2025 

how to run the server, create a topic, and run a producer and consumer.
 step-by-step based on standard Kafka usage, Stand alone system

download from this link : https://kafka.apache.org/downloads

select Source download: kafka-4.0.0-src.tgz (asc, sha512)

downloaded  kafka-4.0.0-src.tgz 

* ms using mac system 

moved the downloaded file in a newly created folder Kafka_Demo

open terminal check with command pwd it will show the path 
change the path and go to newly created folder  i.e Kafka_Demo  to extract it. 

$tar xvzf afka-4.0.0-src.tgz 

it will extract and create a folder kafka-4.0.0-src

open the folder and check bin  and config folders 
in bin you will find the schell script  and in bin you also find windows folder  when u open it you will find batch script 
you will find all the shell script to run server  create topic start produce start consumer 


next open the config folder and check for server.properties  is important 
you have to edit server.proprties
check for below 

 process.roles=broker,controller
 node.id=1
 controller.quorum.voters=1@localhost:9093
 listeners=PLAINTEXT://localhost:9092,CONTROLLER://localhost:9093
 log.dirs=/tmp/kafka-logs


to Start the Server 

open new terminal 
browse to newly created folder Kafka_Demo
run the below 

 - Start the server:
     ```
     ./bin/kafka-server-start.sh config/server.properties
     ```
   - The server should start and log messages indicating it’s running as both a broker and controller.

   when you will get this error 
   Classpath is empty. Please build the project first e.g. by running './gradlew jar -PscalaVersion=2.13.15'
plz run ./gradlew jar -PscalaVersion=2.13.15

and then start again the server/broker 

Then start the Kafka broker:
     ```
     ./bin/kafka-server-start.sh config/server.properties
     ```
   - Default `server.properties` has `listeners=PLAINTEXT://:9092`

   open a new terminal in new tab and create a kafka topic. 

   Creating a Topic
Once the server’s running, create a topic:
```
./bin/kafka-topics.sh --create --topic my-topic --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1

Running a Producer
Use the console producer to send messages:
```
./bin/kafka-console-producer.sh --topic my-topic --bootstrap-server localhost:9092

enter the msg 

Hi This my first Kafka msg 


Running a Consumer
Start a console consumer to read messages:
```
./bin/kafka-console-consumer.sh --topic my-topic --bootstrap-server localhost:9092 --from-beginning

 you will see the msg 

 
Hi This my first Kafka msg 

