# Installing Iota
**Description**

This section describes how to install Iota on Windows 7 and Windows 10.



1. **Download** iota-installer-Windows-XX.X.exe into a directory using the download link provided by Particle Analytics.

2. **Execute** the iota-installer-Windows-XX.X.exe as administrator.

3. The Iota Suite Setup welcome window will show up. You need to click **Next >**

   ![](/images/Installation_Welcome_to_Iota_Setup.PNG)
   
4. Review and accept the terms of the license agreement by clicking **I Agree.**

   ![](/images/Installation_License_agreement.PNG)
  
5. Select the destination folder for Iota installation and click **Next >**. The default destination folder for the installation is  `C:\Program Files\iota_suite`.
   
   ![](/images/Installation_location.PNG)


6. Select the name for the Start Menu folder that will appear in the Windows Start Menu and click **Next >**. The default name is `Iota` 
   
   ![](/images/Installation_Start_Menu_folder.PNG)


7. Select the components to install and click **Install**. If you are installing Iota for first time, you need to select all components to install.
   
   ![](/images/Installation_Choose_Components.PNG)

8. Wait until the installation process finishes.

9. Once Iota has been installed, click on **Finish** to close the Iota Suite Setup.

10. **Create a new environment variable** called `IOTA_PATH` that points to the installation directory of Iota (see step 5 of Installation Instructions):
    

**Windows 10**

  1. In Search, search for and then select: **System** (Control Panel)

  2. Click the **Advanced system settings** link.

  3. Click **Environment Variables**. In the section **User Variables for ...**, Click **New**. 

  4. In the **New User Variable** window, specify **Variable Name:** `IOTA_PATH` 

  5. In the **New User Variable** window,  Click **Browse Directory...** . and select the folder where Iota was installed (e.g. `C:\Program Files\iota_suite`) and click **OK**.

  6. In the **New User Variable** window, double-check that Variable value shows the path to `iota_suite` directory and click **OK.**

  7. In the **Environment Variables** window, click **OK**

  8. In the **System Properties** window, click **OK.**

​    

**Windows 7**

     1. From the desktop, right click the **Computer** icon.

     2. Choose **Properties** from the context menu.

     3. Click the **Advanced system settings** link.

     4. Click **Environment Variables**. In the section **User Variables for ...**, Click **New**. 

     5. In the **New User Variable** window, specify **Variable Name:** `IOTA_PATH`

     6. In the **New User Variable** window,  Click **Browse Directory...** . and select the folder where Iota was installed (e.g. `C:\Program Files\iota_suite`) and click **OK**.

     7. In the **New User Variable** window, double-check that Variable value shows the path to `iota_suite` directory and click **OK.** 

     8. In the **Environment Variables** window, click **OK.**

     9. In the **System Properties** window, click **OK.**


11. Go to Windows Start Menu and look for **Iota**.

   ![](/images/Installation_Iota_Menu.PNG)

12. Menu entry Iota Suite will show the following options:

    * **Iota iPython Terminal** gives access to a IPython terminal where the user can import and use the Iota Python Library
    * **Iota Jupyter** launches [Jupyter Notebook](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html) where the users can create and load their notebooks and conduct the analyses of their simulations data.
    * **Iota Manual** provides access to the online Iota user manual
    * **License registration** allows users to get the information required to generate and register a license file
