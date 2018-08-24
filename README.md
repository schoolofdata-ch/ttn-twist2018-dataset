# twist2018-dataset

> Data part of ongoing research, provided by Benedikt Hitz-Gamper, Institute of Information Systems, University of Bern, benedikt.hitz@iwi.unibe.ch

## Data files

### File `ttn_gateways.csv` (134 rows)

* `device_id`: unique key for device_id in table `ttn_measurements` (this is an internal key, not connected with TTN IDs)
* `eui_id`: id used by TTN to uniquely identify gateways 
* `platform`: make/model of gateway if provided
* `category`: clustered value for `platform`
* `lat`/`lng`: location of gateway if provided
* `altitude`: altitute of gateway if provided
* `ETH_dist`: distance from gateway to ETH main building (selection criteria for gateways is < 20km)

### File `ttn_measurements.csv` (750926 rows)

* `id`: unique id
* `device_id`: key for `device_id` in table `ttn_gateways`
* `last_online`: last handshake of gateway with TTN backend
* `rx_ok`: number of packets received by this gateway (counter is never reset)
* `tx_in`: number of packets sent by this gateway (counter is never reset)
* `measured_at`: time of measurement

To decide whether a gateway is online, verify the difference of `measured_at - last_online`. If difference is smaller than 30 to 90 seconds, the gateway was online at this time.

*Note:*
Somethimes `last_online` is greater than `measured_at`, this has to do with the fact that the values get actually stored in the database after `measured_at` and sometimes even a newer `last_online` is available.

## Credit

Data part of ongoing research, provided by Benedikt Hitz-Gamper, Institute of Information Systems, University of Bern, benedikt.hitz@iwi.unibe.ch
