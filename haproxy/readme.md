To access the aerospike cluster from outside of the aerospikenetwork, we need an ingress node. 
HA-Proxy will provide ingress access to the aerospike cluster.  The sameple config will discover up to 10 backend instances.  Scaling byond 10 will require editin the haproxy.cfg
```
docker build -t haproxy-aeorspike .
```
The node running haproxy should be spcified in the aerospike_mesh.conf network.service.access-address
```
docker run -d --sysctl net.ipv4.ip_unprivileged_port_start=0 -p 3000:3000 --net aerospike_aerospikenetwork haproxy-aeorspike
```