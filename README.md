Purpose
=======

This repository is intended to build a RPM (based on Fedora 23 sRPM) with the cryptsetup-nuke-keys patch

To build package you can run:
------------------------------------
<pre>[root:~/src] # rpmbuild -ba SPECS/cryptsetup-1.6.8-2.fc23.spec</pre>

don't forget to rebuild initramfs with the new package installed:

<pre>dracut -vf</pre>

cryptsetup-nuke-keys
====================

A patch for cryptsetup which adds the option to nuke all keyslots given a certain passphrase.
Original cryptsetup patch by Juergen Pabel, found here - http://lxer.com/module/newswire/view/103692/index.html

<pre>
root@kali:~# cryptsetup luksAddNuke /dev/sda5
Enter any existing passphrase:          (existing password)
Enter new passphrase for key slot:      (set the nuke password)
</pre>

Once the machine is rebooted and you are prompted for the LVM decryption passphrase.
If you provide the nuke password, all password keyslots get deleted, rendering the encrypted LVM volume inaccessible.

For more details check -  http://www.kali.org/how-to/emergency-self-destruction-luks-kali
