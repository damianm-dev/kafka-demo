# kafka Demo (GitHub Codespaces Edition, Apache kafka_2.13-4.1.1)

This project demonstrates how to run latest Apache Kafka  inside GitHub Codespaces and how to .

---

## 1. GitHub Student Developer Pack (optional)

Since you are a student, you can get extended Codespaces limits here:  
https://education.github.com/pack

---

## 2. Prepare Your Repository

1. Install Git on your local machine https://git-scm.com/install/
2. Create a new empty GitHub repository and upload this folder.  

---

## 3. Using GitHub Codespaces

1. Go to: https://github.com/features/codespaces  
2. Click **New Codespace**  
3. Select your repository  
4. Codespace will open in VS Code Web. But you need to connect using VS Code Desktop.

---

## 2. VS Code Setup (IMPORTANT)

1. Install VS Code: https://code.visualstudio.com/
2. Install the **GitHub Codespaces** extension:
   - Open VS Code → Extensions → search "Codespaces" → Install
3. In the Activity Bar (left side), click **Remote Explorer**
4. You will see your Codespace → click **Connect**
5. VS Code will open a remote development session running inside Codespaces.

---

## 4. Install Java
Kafka requires Java 8 or higher. Check if Java is installed with java -version. If not installed, run:
```bash
sudo apt-get update
sudo apt-get install -y openjdk-11-jdk
```

---

## 5. Install Kafka
Download the latest Kafka release and extract it:
```bash
tar -xzf kafka_2.13-4.1.1.tgz
cd kafka_2.13-4.1.1
```

---

## 6. Start the Kafka environment
Generate a Cluster UUID and Format Log Directories

```bash
KAFKA_CLUSTER_ID="$(bin/kafka-storage.sh random-uuid)"
bin/kafka-storage.sh format --standalone -t $KAFKA_CLUSTER_ID -c config/server.properties
```
Start the Kafka Server
```bash
bin/kafka-server-start.sh config/server.properties
```

---

## 7. Create a topic to store your events
Open another terminal session and run
```bash
bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092

bin/kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092
```

---

## 8. Create a topic to store your events
```bash
bin/kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092
>This is my first event
>This is my second event
```

---

## 9. Read the events
```bash
bin/kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092
```

---

 ## 10. Terminate the Kafka environment
 Stop the producer and consumer clients with Ctrl-C, if you haven't done so already.
 Stop the Kafka broker with Ctrl-C

```bash
rm -rf /tmp/kafka-logs 
```
---

## 11. Create Python Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install kafka-python-ng
```
