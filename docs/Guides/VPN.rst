#############################
VPN Installation Instructions
#############################

*******
Windows
*******

1. Visit the `GlobalProtect VPN <https://vpn.princeton.edu/>`_ web portal.
2. Enter your Princeton NetID, your password, and click Log in. 
3. Wait for Duo to send a request to your default device and approve the Duo request.
4. To download, click on the GlobalProtect Agent :numref:`(see red box %s) <webPortal>`.

.. figure:: VPN/VPN1.png
    :width: 100%
    :align: center
    :figclass: align-center
    :name: webPortal
     
    GlobalProtect VPN web portal

5. On Windows - Select Continue installing from outside the Store :numref:`(see red box %s) <install>`.

.. figure:: VPN/VPN2.png
    :width: 50%
    :align: center
    :figclass: align-center
    :name: install
     
    GlobalProtect Install

6. You will see the GlobalProtect Setup Wizard. The installer will guide you through the steps required to install the software. Click Next.
7. On the Select Installation Folder screen, click Next.
8. On the Confirm Installation screen, click Next.
9. On the Account Control pop-up, enter an admin user name and password. You will be asked, “Do you want to allow this app to make changes to your device?” Click Yes.
10. On the Installation Complete screen, click Close to exit.
11. Once installed, you should see the following pop-up :numref:`(see image %s) <vpnNOIP>` on your desktop.

.. figure:: VPN/VPN3.png
    :width: 50%
    :align: center
    :figclass: align-center
    :name: vpnNOIP

12. Type vpn.princeton.edu in the text box :numref:`(see image %s) <vpnIP>`, click Connect.

.. figure:: VPN/VPN4.png
    :width: 50%
    :align: center
    :figclass: align-center
    :name: vpnIP

13. Enter your Princeton NetID, your password, and click Log in :numref:`(see image %s) <duo>`.

.. figure:: VPN/VPN5.png
    :width: 50%
    :align: center
    :figclass: align-center
    :name: duo

14. A pop-up should then appear. Click Yes :numref:`(see image %s) <popUP>`.
15. Wait for Duo to send a request to your default device and approve the Duo request.

.. figure:: VPN/VPN6.png
    :width: 50%
    :align: center
    :figclass: align-center
    :name: popUP

If you have connected, you should see a small blue globe on your taskbar :numref:`(see image %s) <globe>`.

.. figure:: VPN/VPN7.png
    :width: 50%
    :align: center
    :figclass: align-center
    :name: globe


*****
MacOS
*****

1. Download and install SonicWall Mobile Connect from the Mac App Store.
2. Open the SonicWall Mobile Connect application.
3. Click Accept to continue.
4. Click the gear icon to add a connection.
5. Enter the following: Name: "Princeton University" Server: "remote.princeton.edu"
6. Click Save.
7. Click Connect.
8. Confirm Princeton University is selected and click Next.
9. Enter your Princeton NetID and password and click Login.
10. Wait for Duo to send a request to your default Duo device.
11. Approve the Duo request.* *IMPORTANT: The connection will fail if you do not approve the Duo request. For information about Duo multifactor authentication, see http://www.princeton.edu/duo.
12. The SRA software is now installed and configured.