# SDN Implementation
This is the sdn implementation on the cisco switch. Before you use the project, you need to set static IP for your host and controller. And you need to modify the mac_table.txt. The mac_table is used to record the valid hosts MAC Address & IP.

## Run Controller
```
ryu-manager --observe-links ofctl_rest.py actualSDN_django_switch.py
```
## Run django
```
python manager.py runserver
```
## REST API
This function can get flow stats, add flows, delete flows etc. Please refer to the following [link](https://ryu.readthedocs.io/en/latest/app/ofctl_rest.html).
#### Example of use:
* Get flow table: 127.0.0.1:8080/stats/flow/{dpid}
* Add flow:
```
$ curl –X POST –d '{
	"dpid":1,
	"actions": [
        {
            "type":"OUTPUT",
            "port": 2
        }
    ],
	"match":{
		"dl_dst":"MAC1",
		"dl_src":"MAC2"
	}
}'  http://localhost:8080/stats/flowentry/add

```
* Delete specific flow:
```
$ curl –X POST –d '{
	"dpid":1,
	"actions": [
        {
            "type":"OUTPUT",
            "port": 2
        }
    ],
	"match":{
		"dl_dst":"MAC1"
		"dl_src":"MAC2"
	}
}'  http://localhost:8080/stats/flowentry/delete

```
* Delete all flows:
```
$ curl -X DELETE http://localhost:8080/stats/flowentry/clear/{dpid}
```
