# myrha
Summarize supportdump files from Mirantis MCC/MOS clusters<br>
<br>
# Installation:
Download the .sh scripts which corresponds to your distro (myrha-mac.sh or myrha-linux.sh). After that, create a link to /usr/local/bin folder:<br>

```
$ sudo ln -s ~/Downloads/myrha-mac.sh /usr/local/bin/myrha
```

You should run "myrha" command inside the supportdump extracted folder, where either MCC or MOS logs are located. Example:<br>

```
$ ~/Downloads/test/kaas-bootstrap/logs/ ls
kaas-mgmt/  mos/
$ ~/Downloads/test/kaas-bootstrap/logs/ myrha
```

Myrha will check for nececessary packages and will prompt you to install them if needed (using apt,dnf or brew).<br>
Once the script is complete, a new folder called "myrha" will be created, where yaml files will be created, containing the summary of different cluster aspects (MCC and/or MOS). The generated folder content should look like this:

```
$ ~/Downloads/test/kaas-bootstrap/logs/ ls myrha 
files             mos_nodes.yaml       mos_openstack.yaml  mos_l2template.yaml  mcc_cluster.yaml  mcc_lcmmachine.yaml  mcc_ipamhost.yaml    mcc_pv_pvc.yaml
mos_cluster.yaml  mos_lcmmachine.yaml  mos_mariadb.yaml    mos_subnet.yaml      mcc_events.yaml   mcc_mariadb.yaml     mcc_l2template.yaml  
mos_events.yaml   mos_ceph.yaml        mos_ipamhost.yaml   mos_pv_pvc.yaml      mcc_nodes.yaml    mcc_certs.yaml       mcc_subnet.yaml      
```

By default, the script is set to automatically open Sublime text with all files generated. You can also open them up on vim by commenting the following lines:<br>

```
/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl --new-window --command $LOGPATH/*.yaml 2> /dev/null
```

and uncommenting the following ones:<br>

```
#nvim -R -c 'silent argdo set syntax=yaml' -p $LOGPATH/*_*
#nvim -R -p $LOGPATH/*.yaml
```

