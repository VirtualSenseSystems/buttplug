# Generic Sensor Messages

Messages for requesting and receiving information about generic
sensors on devices, including batteries, radio levels, accelerometers,
buttons, etc.

---
## BatteryLevelCmd

**Description:** Requests that a device send its battery level.

**Introduced In Spec Version:** 2

**Last Updated In Spec Version:** 2

**Fields:**

* _Id_ (unsigned int): Message Id
* _DeviceIndex_ (unsigned int): Index of device to query for battery reading.

**Expected Response:**

* [BatteryLevelReading](sensors.html#batterylevelreading) message with
  matching Id on successful request.
* Error message on value or message error.

**Flow Diagram:**

<mermaid>
sequenceDiagram
    Client->>Server: BatteryLevelCmd Id=1 DeviceIndex=0
    Server->>Client: BatteryLevelReading Id=1 DeviceIndex=0 BatteryLevel=0.5
</mermaid>

**Serialization Example:**

```json
[
  {
    "BatteryLevelCmd": {
      "Id": 1,
      "DeviceIndex": 0
    }
  }
]
```
---
## BatteryLevelReading

**Description:** Message containing a battery level reading from a
device, as requested by [BatteryLevelCmd](sensors.html#batterylevelcmd).

**Introduced In Spec Version:** 2

**Last Updated In Spec Version:** 2

**Fields:**

* _Id_ (unsigned int): Message Id
* _DeviceIndex_ (unsigned int): Index of device battery reading is from.
* _BatteryLevel_ (double): Battery Level with a range of [0.0-1.0]

**Expected Response:**

* None. Server-to-Client message only.

**Flow Diagram:**

<mermaid>
sequenceDiagram
    Client->>Server: BatteryLevelCmd Id=1 DeviceIndex=0
    Server->>Client: BatteryLevelReading Id=1 DeviceIndex=0 BatteryLevel=0.5
</mermaid>

**Serialization Example:**

```json
[
  {
    "BatteryLevelReading": {
      "Id": 1,
      "DeviceIndex": 0,
      "BatteryLevel": 0.5
    }
  }
]
```
---
## RSSILevelCmd

**Description:** Requests that a device send its RSSI level.

**Introduced In Spec Version:** 2

**Last Updated In Spec Version:** 2

**Fields:**

* _Id_ (unsigned int): Message Id
* _DeviceIndex_ (unsigned int): Index of device to query for RSSI level.

**Expected Response:**

* [RSSILevelReading](sensors.html#rssilevelreading) message with
  matching Id on successful request.
* Error message on value or message error.

**Flow Diagram:**

<mermaid>
sequenceDiagram
    Client->>Server: RSSILevelCmd Id=1 DeviceIndex=0
    Server->>Client: RSSILevelReading Id=1 DeviceIndex=0 RSSILevel=-40
</mermaid>

**Serialization Example:**

```json
[
  {
    "RSSILevelCmd": {
      "Id": 1,
      "DeviceIndex": 0
    }
  }
]
```
---
## RSSILevelReading

**Description:** Message containing a RSSI level reading from a
device, as requested by [RSSILevelCmd](sensors.html#rssilevelcmd).

**Introduced In Spec Version:** 2

**Last Updated In Spec Version:** 2

**Fields:**

* _Id_ (unsigned int): Message Id
* _DeviceIndex_ (unsigned int): Index of device the reading is from.
* _RSSILevel_ (int): RSSI Level, usually expressed as db gain, usually [-100:0]

**Expected Response:**

* None. Server-to-Client message only.

**Flow Diagram:**

<mermaid>
sequenceDiagram
    Client->>Server: RSSILevelCmd Id=1 DeviceIndex=0
    Server->>Client: RSSILevelReading Id=1 DeviceIndex=0 RSSILevel=-40
</mermaid>

**Serialization Example:**

```json
[
  {
    "RSSILevelReading": {
      "Id": 1,
      "DeviceIndex": 0,
      "RSSILevel": -40
    }
  }
]
```
