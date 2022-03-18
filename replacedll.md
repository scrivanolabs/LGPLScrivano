# How to replace Qt dll files used in Scrivano for Windows
Scrivano for Windows is built using the [Qt Framework](https://qt.io). It uses the Qt libraries (version 5.15.2) by dynamically linking to them at runtime. The use of such libraries is made under the LGPL v3.0 license (see here https://www.gnu.org/licenses/lgpl-3.0.en.html) which grants the user to replace the dynamically linked Qt libraries used in Scrivano with another independent build of the Qt libraries. Below there are instructions to replace the Qt dll libraries linked in Scrivano by using the MSIX Packaging Tool provided by Microsoft.

1. Download the <a href="https://www.microsoft.com/en-gb/p/msix-packaging-tool/9n5lw3jbcxkf">MSIX Packaging Tool</a> from the Microsoft Store.
2. Launch MSIX Packaging Tool, choose the option "Modification Package".
3. On the next screen, you can choose whether you want to create the modification package on your local machine, a remote machine or a virtual machine. Choose the option you want and click Next.
4. On the next screen, the program will check whether your system is ready to creat the package. Once the check is over, click Next.
5. On the "Select Installer" screen, check the box "Manually enter the main package information". In the "Package name" field, write "30692ScrivanoLabs.Scrivano" and in the "Publisher Name", write "CN=3DA70249-3C7F-4908-9853-37DB3965B8EA". From the "Signing Preference" dropdown menu, choose "Sign with a certificate" and choose a certificate file from your disk (to learn how to create a self-signing certificate file and add it your system see <a href="https://docs.microsoft.com/en-us/powershell/module/pki/new-selfsignedcertificate?view=windowsserver2022-ps">here</a>).
6. In "Package Information" screen, fill in the details of your modification package (you can choose any package and publisher name, but make sure that the publisher name matches the name used to generate your certificate file). Then click Next.
7. In "Installation" screen, click Next.
8. In the "Create Package" screen, click on "Package Editor", go the "Packaged Files" tab. From the drop down list, find the "VFS" folder. Right click on it and select "New Folder", then select "System". Finally, right click on "System" and select "Add File" and add the dll file you'd like to replace (e.g Qt5Core.dll). Repeat this for all the other dll files you'd like to replace.
9. Click on "Create". Install the modification package and Scrivano will run using the replace dll files.

NOTE: There is no guarantee that replacing dll files will not modify the app's behaviour or functionality, so use this method at your own risk. 

# How to replace Qt dll files used in Scrivano for Linux
Scrivano for Linux is built using the [Qt Framework](https://qt.io). It uses the Qt libraries (version 5.15.2) by dynamically linking to them at runtime. The use of such libraries is made under the LGPL v3.0 license (see here https://www.gnu.org/licenses/lgpl-3.0.en.html) which grants the user to replace the dynamically linked Qt libraries used in Scrivano with another independent build of the Qt libraries. The prebuilt libraries are located inside the installation directory. To replace them just replace the files with your own independent build of the Qt libraries.
