# Registering Iota license
**Description**

This section describes the steps to register a license for Iota:



### Local license

1. Go to Windows **Start Menu** and inside the **Iota** folder, click on **License Registration** icon.

   

    ![License_registration_Menu_entry](C:\Users\AJanda\Documents\Iota_Reborn_documentation\images\License_registration_Menu_entry.PNG)

   

2. After a few seconds, a new tab with the **hostname** of your machine and some instructions will be open in your default web browser. 

3. **Copy** the **hostname** shown in the window and **email** it to info@particle-analytics.com to get your license file

4. Once you have received your **license file** from our team, **copy** it to the **`AppData\Local\ParticleAnalytics\Iota`** folder located at your home directory (e.g. 
   `C:\Users\Stephen\AppData\Local\ParticleAnalytics\Iota`).

5. Please, change the name of the license file to **`particle.lic`** if the name of file is different.

6. Go to Windows **Start Menu** and click on **Iota Jupyter** icon to launch Jupyter Notebooks and start creating a new iota notebook

   

   ![License_registration_Iota_Jupyter](C:\Users\AJanda\Documents\Iota_Reborn_documentation\images\License_registration_Iota_Jupyter.PNG)





### Floating license

Iota supports floating licenses using the license server developed by Reprise Software Inc. For information on how to install the license server, please contact [support@particle-analytics.com](mailto:support@particle-analytics.com). 

If the license server has been already installed:

1. Go to Windows **Start Menu** and inside the **Iota** folder, click on **License Registration** icon.

   

    ![License_registration_Menu_entry](C:\Users\AJanda\Documents\Iota_Reborn_documentation\images\License_registration_Menu_entry.PNG)

   

2. After a few seconds, a new tab with the **hostname** of your machine and some instructions will be open in your default web browser. **Ignore** the instructions and **close** the tab.

3. Open with a text editor the file **config.ini** located inside the **`AppData\Local\ParticleAnalytics\Iota`** folder located at your home directory (e.g. 
   `C:\Users\Stephen\AppData\Local\ParticleAnalytics\Iota\config.ini`)

4. In the section `[DEFAULT]`, replace the file path of the variable  **licence** by **port_number@server_IP** information of your license server (e.g. `licence = 5053@172.16.254.1`) and **save** the changes.

5. Go to Windows **Start Menu** and click on **Iota Jupyter** icon to launch Jupyter Notebooks and start creating a new iota notebook.