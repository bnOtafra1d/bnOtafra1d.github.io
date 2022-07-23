# Bluetooth Essentials

Bluetooth is a standardized protocol for sending and receiving data using a 2.4HZ wireless link. It's allows for as a low-power and short-range wireless transmissions between electronic devices. It is most commonly found in headsets, wireless mice and keyboards, and other embedded/IOT devices.

## How Bluetooth Works

Wireless technology is now a very common tool in the modern world. Most people are familiar with WiFi in their homes and businesses. Bluetooth devices communicate directly with each other, as opposed to sending traffic to an intermediary device like a router. This provides a low power option and increases battery life.

Low-power radio waves transmist data between 2.400 GHz and 2.483.5 GHz. You can find further information on this topic [here](https://www.bluetooth.com/learn-about-bluetooth/key-attributes/range/).

### Master, Slaves, and Piconets

Bluetooth networks operate with a master/slave model which controls when and where a device can send data. This type of network is called a piconet. In a piconet, a master device can be connected to multiple different slave devices. The slave device can only be connected to a single master device.

Using this model the master is able to coordinate and send data to any of it's slaves and request data from them as well. Slaves can only communicate with the master and are unable to transmit to other slaves in the piconet.

### Address and Names

The Bluetooth Device Address (**BD_ADDR**) is a unique 48-bit identifier assigned to bluetooth devices by manufacturers. This is often presented as a 12-digit hexadecimal value (ex. **00:AB:22:CD:44:EF**). The first first 24 bits of the address identifies the manufacturer. The last 24 bits are the unique identifier of the address. In the picture below you can see the output of a scan using [bettercap](https://www.bettercap.org/) which shows the name of numerous bluetooth devices and their unique addresses:

![image-20220723144819584](/home/eris/snap/typora/57/.config/Typora/typora-user-images/image-20220723144819584.png)

Bluetooth devices can also have user-friendly names such as the device named **Infinitime** above, as well as the picture below which lists devices linked to the master:

![image-20220723145714568](/home/eris/snap/typora/57/.config/Typora/typora-user-images/image-20220723145714568.png)

### Connection Process

Establishing a Bluetooth connection between two devices follows a multi-step process involving three progressive states:

1. **Inquiry** - When two devices have never connected, one must run an inquiry or **discovery** between themselves. One of the devices will send out an inquiry request. Any device that is listening for this request will respond with it's address, name, and other important information.
2. **Paging (Connecting)** - This is the process of forming a connection between the two devices. Each device needs to know the address of the other device which is found during the inquiry process.
3. **Connection** - Once a device has completed the devices enter the connection state. Devices can either be actively communicating with one another or put into low-power sleep mode to conserve power.
   * **Active Mode** - This is the mode in which devices are actively transmitting and receiving data.
   * **Sniff Mode** - In this mode the device goes into a sleep mode and only listens for transmissions at a set interval (every 200ms for instance).
   * **Hold Mode** - This is a temporary mode where a device sleeps for a pre-defined period and then returns back to active mode once that interval has passed.
   * **Park Mode** - This mode is where the master tells the slave to sleep until being told to wake up and begin to transmit data.

### Bonding and Pairing

Pairing is the process where devices exchange information needed to establish and encrypted connection. The devices being paired will authenticate with each other before beginning to securely transmit data. Bonding is when the information from the pairing process is stored on the devices. This allows the process of devices to connect securely together without manual intervention.
