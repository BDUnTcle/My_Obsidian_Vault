---
create date: 2024-09-11
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
modification date: 
type: CourseNotes
---

# Before the Class
## Lectures and Materials
---
# Distributed Artificial Intelligence in cloud computing and IoT field
---
# Introduction.
Hi everyone, my name is Jiahao. My topic today, is "Distributed Artificial Intelligence in Cloud Computing and IoT Fields".
During my presentation, I will first introduce those concepts , how they work and their advantages. 
Then we step into a specific application scenario of this kind of technology in recent days.

As we step into the Internet of Things era, the number of mobile devices is growing exponentially, leading to massive amounts of generated data. The recent reports show that there will be 30.9 billion connected IoT devices in 2025, and the size of data is expected to reach nearly 79.4 Zettabytes. 

Meanwhile, powered by advanced algorithms , AI tools perform well in handling big data. 

However, cloud AI and computing is facing challenges in real-time applications.

For instance, cloud-based services are typically time-consuming and resource-demanding due to the transmission of massive amounts of data , and it also becomes difficult to meet the delay-sensitive and context-aware services.

On the other hand, in order to achieve high-performance and accuracy in AI models, devices often have high requirements for computing power---they need to be equipped with high-performance GPUs. 
However, for mobile devices, these hardware requirements become challenging, as most mobile devices cannot meet the demands of it's high energy consumption and large size.

These concerns call for DAI, where model training and inference can be performed in a distributed manner nearby the data source, combined with end-edge-cloud computing (EECC)

## How it works
As shown in the picture, in the EECC framework, from bottom to top are end layer, edge layer, and cloud layer, where each layer is responsible for different AI tasks.

The end layer can collect, preprocess data and make early decisions. 
It includes millions of  sensors, mobile devices, smartphones, and actuators, which have certain computing and storage capacities. 
With local processing, only compact processed data needs to be transmitted to the upper computing devices, which significantly reduces latency and network costs.

The edge and network layer is the bridge that connects the end and cloud layer. 
It includes base stations, routers, gateways, access points.
It is mainly responsible for authentication, encryption, model selection, and request forwarding. 
The pre-processed data from the end layer can be aggregated in edge layer for deep analysis and decision,

The cloud layer is equipped with powerful computing capabilities and storage resources. 
It is responsible for data storage, device management and complicated model training. 
It can train AI models with high accuracy and coordinate the end and edge layers.

Also, with many optimization approaches, such as parallelism and distributed learning framework, the performance of DAI can be further increased.
# Specified Area I
Nowadays, the EECC paradigm continues to have a profound impact on a wide range of intelligent applications. Here, I will focus on a specific scenario of how AI-Enabled distributed computing has influences in UAVs(unmanned aerial vehicles) . They are using to enable real-time applications, such as pattern recognition and object detection.

Look at this picture, in the system model of a UAVs network, each drone will be represented by an embedded ML system platform equipped with a camera and memory. It also includes  a specific drone  named master UAV to provide powerful resources. In the real applications, there will be multiple networks like this in different level. 
Each cluster of master is served by a base station and is formed  based on the targeted tasks and events.

One study shows that well trained AI models at the levels of local computing and edge computing  can provide better MSE (mean square error) levels with short execution times, which means better performance.

Next, I want to show you guys a 1 minute video of a drone light show .
This video was filmed in Shenzhen, China, this September, and it is the hottest drone application scenarios in China recent days. Its said that over 10 thousands drones were used in this performance. I believe it provides a great demonstration of the potential of DAI technology in this field.

---

# Flash Cards
