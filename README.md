**WARNING: completley untested**

This script will reset a VE if the file `/etc/reset-ve` exists on it. The VE can
be specified in the first few lines of the `ve_resetter`. Calling this script 
periodically on the host, enables the root user of the VE to completley reset it
by calling

    touch /etc/reset-ve
