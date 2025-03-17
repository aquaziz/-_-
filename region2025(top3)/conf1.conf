! Configuration File for keepalived

vrrp_instance CL_2 {
    state BACKUP
    interface ens3
    virtual_router_id 80
    priority 100
    advert_int 3
    virtual_ipaddress {
        192.168.10.100
    }
front 2

_______________________
! Configuration File for keepalived

vrrp_instance CL_1 {
    state MASTER
    interface ens3
    virtual_router_id 80
    priority 110
    advert_int 3
    virtual_ipaddress {
        192.168.10.100
    }
}

front1
