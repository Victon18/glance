# Framework for Designing IoT Products
### Thingworx Development Process

It is divided into six stages
- Experience
---
define the problem to solve and the value the application provides users.

- Model
---
create the schema to store the IoT data and functionality, which is the backbone that later stages rely upon.
1. Scale
2. Connectivity
3. Development
4. UI build
5. Analytics

Thing
----
A ThingWorx Thing represents a tangible set of information and data in the ThingWorx system.
attributes are:
- **Properties**, which are status variables.
    They may be IoT data, such as oil pressure from a device, or internally computed data, such as the optimal speed of an assembly line as determined by advanced analytics.
- **Services**, which are commands that the user may issue to the Thing.
    For example, if a user can change the speed of an assembly line or add a user to the system, they would do so by executing a service.
- **Events and Subscriptions** are linked together.
    Subscriptions are similar to services. However, instead of a user executing them, they are executed automatically when an event occurs.

- Analyze, Build, and connect
---
**Analyze** - aggregate and optimize the IoT data to make it easier to understand and more valuable.
**Connect** -  establish the connection to IoT devices and enterprise systems.
**Build** - create a user interface for your users.

The next three stages, analyze, connect, and build, may be accomplished in any order or in parallel.
However, they cannot be accomplished without a model

- You cannot analyze data that is not defined in the ThingWorx model.
- Devices require a modeled thing to connect to, such as a Database Thing or a Device Thing.
- The build stage creates a user interface informed by data in the model.
    This user interface is usually, but not always, a Web-based user interface.
    It may be an augmented reality UI based on Vuforia, or it may provide notifications using email or SMS.


- Deploy
---
**Deploy** - move the IoT application into a reliable, scalable, and secure production system.
access control testing, scalability testing, user acceptance testing, selecting the correct hardware, scaling the production system appropriately,
setting up redundancy, and high availability functionality, securing the system with encryption, setting up a backup scheme, and migration are all deploy stage topics.

### Smart, Connected Product (SCP) Stack

There are five layers in this framework
- **Product Infrastructure** is the bottom layer of the stack. It includes the product hardware and software.
- **Sensors** are the next layer in the stack. Sensors are components that detect the product state and the network that communicates that information.
- **Connectivity** is the middle layer in the stack. It defines the communication protocols used to send information from the product to the cloud.
- **Analytics** is the fourth layer. It translates the sensor data into meaningful information.
- **Smart Apps** are the top layer of the stack, which integrates all the layers to provide IoT functionality.

### Network and Data Storage
The programmable logic controller has a serial connection to a computer.
That gateway computer has an Internet connection and is the ideal place to install ThingWorx Kepware Server.
Another common IoT gateway technology is Bluetooth.

### Outages and Security
**Outages** - It does not store historical data, so it does not need to retrieve it in the event of an outage. However, the operator should be notified of any network outage.
**Security**
ThingWorx applications do not define the security rules of the systems they connect to.
ThingWorx must obey the rules set by the remote device or system.
Secure passwords, tokens, certificates, or application keys appropriately. They should be encrypted and stored in a location that is not Internet-accessible.
The PLCs used by most applications have no security or direct Internet connection.
They are connected using a serial connection to a gateway server. The gateway, ThingWorx Kepware Server, handles security.

### Sensor and software
**Sensor**
If the facility does not have a sensor for ambient temperature, it can be retrieved from an Internet weather service.
Users set high and low-temperature alert levels, so no sensor is required.

**Software**
The easiest route is to get the data from that system rather than build a new connectivity mechanism.
Most applications get this data from the programmable logic controller
ThingWorx software development kit can be used if the device have enough processing power
If the sensor is not connected and you cannot add software to the device,
you need to build a gateway device that reads the sensor and has the processing capability to communicate with ThingWorx.

### Build Stage

**Mashup Builder** is a tool built into the ThingWorx Platform, enabling the developer to create a Web-based user interface that interacts with the ThingWorx model.
It contains user interface elements, called widgets.
Then, the Mashup contains links to model data, such as the temperature property of a storage facility on the right.
The items are mashed together in the center panel, resulting in the term Mashup, creating elements that combine user interface elements with model data.

**Vuforia Studio** creates a three-dimensional augmented reality (AR) experience, accessible using a cellphone application or augmented reality hardware like HoloLens.

**Custom REST API** (Representational State Transfer Application Programming Interface) Interface.
A ThingWorx REST API is automatically created when a ThingWorx model is created.
Any development tool can make these REST API requests, so you may use any tool.
In fact, Mashup Builder accesses ThingWorx using the same REST API, so the user interface created
using another tool is not inherently any less efficient than one created using Mashup Builder.

The Twilio extension can be used to create an Alert Sender Thing and send text messages. This is a textbased user interface.
A notification extension, enabling ThingWorx to send email. This turns the user’s email account into a ThingWorx user interface.
ServiceMax is a field service ticket management system. ThingWorx can post a service ticket to ServiceMax.

### Connect stage
Connectivity Technology List
- .Net SDK
- Kepware Server
- C SDK
- Extensions
- Java SDK
- Servives
- Flow

Connectivity Technology Locations
- platform
- gateway
- edge

### Experence overview
- Application user
- Application value
- Device connectivity
- Application capability
---
There are four potential capabilities of an IoT device, each escalating in complexity.

1. Stage One
---
An IoT device can be monitored, reporting data to the IoT system.
This capability has the least value.
It is read-only and doesn’t do anything to change the behavior of the device.
It also requires the most work to build initially.
I have to set up the connections, sensors, and model.
However, it is a prerequisite to the other capabilities.

2. Stage Two
----
The second IoT capability is control.
This is the ability to send a command from the IoT system to the device

3. Stage three
---
The third IoT capability is optimize. This is the ability to send a command with extra logic

4. Stage four
---
The last IoT capability is automate. This does the optimal task automatically, without user interaction
- User Interface

### Composer UI Menu
- search
You can search entities created

- New
creeate new entity
set project context

- browse
browse and creat entity of specific type and create the entity
    - Modelling
    - Visualization
    - Data storage
    - Collabration
    - Security
    - System

- open project
see all open entity organised by both entity type and project context

- project view
show all active projects with entiites atteached and list

- permission
vew and edit user permission to entity
collection tab allows permissions to be edited at once
run time and design time to be eited separately


- monitoring
whats happening in thingwork
and houses the status, alrets submenu

- manage
allows users to access the file repository

- import export
import and export file extenxion, data and entities

- user
access to user preferences menu can select the service editor theme
provide comments upon each entity save
toggle

- help

# Mashup


