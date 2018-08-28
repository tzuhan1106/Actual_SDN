# actual_sdn
This is the sdn practice on the cisco 2960x

## Run Controller
```
ryu-manager --observe-links ofctl_rest.py actualSDN_django_switch.py
```
## Run django
```
python manager.py runserver
```
## Check flows
* 127.0.0.1:8080/stats/flow/{dpid}
