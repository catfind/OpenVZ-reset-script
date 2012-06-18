**WARNING: change the root password for your VE in the script before installing it!**

This script will reset a VE if the file `/etc/reset-ve` exists on it. The VE can
be specified in the first few lines of the `ve_resetter`. Calling this script 
periodically on the host, enables the root user of the VE to completely reset it
by calling

    touch /etc/reset-ve

**Setup**

To set it up, you need to edit the first couple of lines of the script, as appropriate for your setup:

    #configuration by user
    ve_target_id=0
    ve_conf_path="/etc/vz/conf/"
    ve_data_path="/data/vz/private/"
    vzctl_create_params="--ostemplate ubuntu-10.04-minimal_10.04_amd64 --config web --ipadd <ip> --hostname <hostname>"
    ve_root_pw="<password>"

Please take care and **change** the root password to be used for your VE!

Then, create a new cronjob, calling the script as root user on your root node.

    crontab -e

For checking every 2 minutes, and logging the resets and possible errors, your crontab entry could look like this:

    # m h  dom mon dow   command
    */2     *       *       *       *       /var/catfind/ve_resetter > /var/catfind/ve_resetter.log 2> /var/catfind/ve_resetter_error.log

