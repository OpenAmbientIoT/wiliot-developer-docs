# Wiliot Sensing Events Overview



### Event Types

Wiliot's cloud generates several types of events. Customers can [choose to receive all events or a subset](https://support.wiliot.com/hc/en-us/articles/4414607675667). All events return a value and have a confidence metric. The following sections list the available events, when they are triggered, and the meaning of the value they return:

#### Current, Recommended Event Types

The following events are recommended for use for all new cloud 2 cloud applications. Where possible, existing applications should transition to using these events. Each event sent from the Wiliot cloud includes a value and confidence metric. It is possible to set minimum and maximum thresholds on event values/confidence to reduce the number of events sent, as described [here](https://support.wiliot.com/hc/en-us/articles/360057035074-Creating-Cloud-2-Cloud-Applications#filtering).

The remainder of this page describes the various event types.

Note: Any event not documented on this page should be considered experimental and not currently recommended for use.

#### Simple Tag Events

Most events relate to a tag. They are described in the following table:

| Event name | Alias | Generated | Returned Value/Confidence |
| --- | --- | --- | --- |
| Active | ACTV | - Immediately after the first packet is received from a tag<br>- When a tag becomes active/inactive<br>- Periodically (every 10m) | 1 as long as the packets are received from the tag (with confidence = 1)<br><br>0 once no more packets are received from the tag with an increasing confidence value, where 0.5 means no packet received for 3 minutes and 0.95 means no packet received for 15 minutes |
| Temperature | TEMP_C | Every 30s | Temperature reading (Celsius) |
| Location Change | LOCH | Change in the probability of a tag being located near a certain gateway:<br>- When the tag is first reported by one or more gateway<br>- When the tag changes its location from one gateway to another<br>- When the confidence level of the tag's location changes significantly - based on confidence parameter<br>- After a tag generated an AWAY event and was subsequently seen by any gateway<br>- Every 10 minutes even with no location change | value = The distance between the coordinates of the current gateway and the previous gateway in km. -1 If the tag has not been "seen" in the past 15 minutes.<br><br>confidence = The likelihood that the reported gateway is the closest to the tag. |
| Geolocation Change | GEOLOC | When a tag reported location changes by 0.2Km or more | Value is the distance (in km) from the previous location |
| Debug | DBUG | When a packet is received by the Wiliot cloud | Value is the number of packets received by the gateway since the last packet sent to the cloud<br><br>Confidence is a number between 0 and 1 representing the RSSI value associated with the packet where 0 is equivalent to -91 and 1 is -40. Intermediate values can be linearly mapped to this range |

#### Alpha-release Tag Events

These events are not yet Plan-of-Record but are in early release for testing, and available to access through the [Wiliot API](<https://support.wiliot.com/hc/en-us/articles/4410665346195>). This is not visible in the Wiliot Management Portal.

| Event name | Alias | Generated | Returned Value/Confidence |
| --- | --- | --- | --- |
| Asset Occupancy | ASSET_OCCUP | Every 20-30 seconds for all labels. To generate event, tags must be part of a [label](https://support.wiliot.com/hc/en-us/articles/4415657388819-Management-Portal-Labels). | Value: level of occupancy between [0,1] where 0 is empty and 1 is full.<br><br>Value of -1 indicates unknown occupancy (when tags are inactive). |

#### Gateway/Bridge Events

Some events are not related to a specific tag. Instead, they relate to a certain gateway. They are described in the following table:

| Event name | Alias | Generated | Returned Value/Confidence |
| --- | --- | --- | --- |
| Gateway/Bridge Connection status | NTWK | - When a gateway connects/disconnects<br>- When a bridge connects/disconnects | value = 1 when a gateway connects for the first time<br><br>value = 0 within 120s after the last connection from a gateway<br><br>*Bridge ID is stored under id column, while Gateway ID is stored under gateway_id column |
| Bluetooth Low Energy Nearby | BLE_NEARBY | - Every 60 seconds | Value is the number of non-Wiliot bluetooth packets (on channel 37) sent to the gateway in the preceding 60 seconds. |

#### Deprecated Event Types

The following events are still being generated but are not recommended for use for new applications. Where possible, existing applications should transition away from these events.

| Event name | Alias | Generated | Returned Value |
| --- | --- | --- | --- |
| Heartbeat | HRTB_S | Immediately after the first packet is received and every 5m as long as packets from the tag are being received | 1.0 |
| Fast Heartbeat | HRTB_F | Immediately after the first packet is received and every 4s as long as packets from the tag are being received | 1.0 |
| Tag moved | GONE | When the frequency of packets from the tags drops below a threshold. This threshold can be indirectly controlled by modifying the confidence parameter (between 0 and 1). A lower value corresponds to higher sensitivity (more GONE events) | Number of seconds since the last packet was received |
| Tag placed down | BACK | When packets from the tag arrive at the cloud following a GONE event | The time between the previous packet and the packet which triggered the event |
| False tag movement detected | HERE | When the GONE event was falsely detected. This event or, more precisely, its absence can be used to reduce false positive GONE events. | The time between the previous packet and the packet which triggered the event |
| No Tag packet reception | AWAY | Once no packet is received from a tag for 180s, then every 20s up to 15m | Number of seconds since the last packet was received |


#### Additional Event Attributes

In addition to the value and confidence attributes, there are more attributes the customer can elect to send to their endpoint with each event when [creating cloud 2 cloud applications](https://support.wiliot.com/hc/en-us/articles/360057035074). They are listed below:

| Attribute | Description | Example |
| --- | --- | --- |
| ownerId | The ID of the tag's owner | my-company |
| tagId | The ID of the tag the event was generated for* | my-item-1234 |
| gatewayId | The ID of the gateway (or bridge) which uploaded the tag packet to the Wiliot tag and triggered the event | GW12345678 |
| id | For tag events - the tag ID. For gateway/bridge events, the gateway ID or bridge ID | GW12345678 |
| gatewayName | A user-friendly, customer-controlled name for the gateway. Null in case of bridge | my-gateway-1234 |
| timestamp | The timestamp (in ms) the event was generated at | 16215694930344 |
| isoTimestamp | The same timestamp in an ISO format | 2021-05-21T07:50:09.066+02:00 |
| eventName | The name of the event | LOCH |
| latitude | The latitude of the gateway/mobile device receiving which generated the event (if known) | 33.0222 |
| longitude | The longitude of the gateway/mobile device receiving which generated the event (if known) | -117.0839 |
| tagsInLabel | The number of tags that contributed to the event when the event is for a label | 2 |

### * only for tag events (unknown for gateway events)