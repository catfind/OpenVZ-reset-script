**WARNING: completly untested**

This script will reset a VE if the file `/etc/reset-ve` exists on it. The VE can
be specified in the first few lines of the `ve_resetter`. Calling this script 
periodically on the host, enables the root user of the VE to completly reset it
by calling

    touch /etc/reset-ve

To set it up, you need to edit the first couple of lines of the script, as appropriate for your setup:

    #configuration by user
    ve_target_id=0
    ve_conf_path="/etc/vz/conf/"
    ve_data_path="/data/vz/private/"
    vzctl_create_params="--ostemplate ubuntu-10.04-minimal_10.04_amd64 --config web --ipadd <ip> --hostname <hostname>"


Then, create a new cronjob, calling the script as root user on your root node.