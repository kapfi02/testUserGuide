# ADONIS Connect for Power BI - User Guide

## 1. Scenario Overview

The ADONIS Connect for Power BI scenario enables a connection between the data stored in ADONIS and Microsoft Power BI.

**Note**: This document focuses on integration with ADONIS. Integration with ADOIT and ADOGRC is also possible.

The current version of the module supports the following features:

- **Quick start with predefined template**: Use the predefined dashboard to visualize your key BPM data in Power BI. By inserting your URL, the dashboard will automatically be updated with your data from ADONIS.
- **Reports**: Embed your Power BI dashboard in MS Teams or MS PowerPoint to keep your colleagues informed about the current state of your Process Management Portfolio.
- **Real-time Synchronization**: View your ADONIS data in real-time in Power BI by synchronizing your dashboard or configure the dashboard to update itself at certain intervals.
- **Personalize your dashboard**: Customize colors, content, and shapes in your graphic presentations quickly and easily using data from your ADONIS repository without coding.

<p align="center">
  <img src="image02.jpg">
</p>

---

## 2. Architecture

The connection between ADONIS and Power BI is established through the ADONIS Standard REST API. Power BI requires the BASE URL of the ADONIS version in use, as demonstrated in the following setup instructions.

---

## 3. Setup

### 3.1 Prerequisites

- **Software Requirements**: ADONIS 16.0 or higher and Power BI Desktop 2.9 or higher must be installed.

### 3.2 Enable Basic Authentication in Administration Page

1. **Library Management**: 
   - Basic Authentication must be enabled in the Administration Page to access ADONIS data in Power BI.
   - Click on the gear icon in the Administration Page. Once the Administration banner appears, log in with your Administrator credentials.

<p align="center">
  <img src="image02.jpg" alt="Description" width="45%">
  <img src="image03.jpg" alt="Description" width="45%">
</p>

2. **Open Settings in Administration Page**:
   - Under “Product Configuration & Licence”, click on **Settings**, then **Standard RESTful services**, and open **General**.

   <div style="text-align: center;">
     <img src="14_files/image04.png" alt="Open Standard RESTful services in Administration page" />
   </div>

3. **Enable REST and Configure Basic Authentication**:
   - In the “Standard RESTful services (General)” tab:
     - Enable **Standard RESTful Services globally**.
     - Go to **Basic Auth** and check “Enable basic authentication”.
     - Enable all Repository scenarios.
     - Under **Cache path**, click “Enable HATEOAS links”.
     - Click **Save** to save your changes.

   <div style="text-align: center;">
     <img src="14_files/image05.png" alt="Configure Standard RESTful services" />
   </div>

   **Note**: Restart the Application Server before reopening ADONIS in the Web Client.

4. **Configure Security Settings for Basic Authentication**:
   - Return to the Home page of the Administration Page and select **More Options**.

   <div style="text-align: center;">
     <img src="14_files/image06.png" alt="Selecting More Options" />
   </div>

   - Scroll to **Authentication** section, find **General Settings**, and click on it.

   <div style="text-align: center;">
     <img src="14_files/image07.png" alt="Authentication section in ADONIS Admin Page" />
   </div>

   - Open **Security settings**. A window with JSON code will pop up. Add “allow all” between the brackets for all IP addresses under “rest”.

   <div style="text-align: center;">
     <img src="14_files/image08.png" alt="Open Security settings" />
   </div>

   The JSON code should look like this after editing:

   <div style="text-align: center;">
     <img src="14_files/image09.png" alt="Allow Basic Authentication as Admin" />
   </div>

5. **Save Changes**: 
   - Click the **Save changes** button in the lower right corner.

   <div style="text-align: center;">
     <img src="14_files/image10.png" alt="Save changes" />
   </div>

---

## 4. Test the ADONIS Connect for Power BI

1. Start the ADONIS services and open ADONIS in a browser. Copy the BASE URL of your ADONIS version (without admin or main views).

   **Example**: If running locally, the URL may look like: `http://localhost:8000/ADONIS16_0`.

2. Open the predefined template received via email. A window will pop up prompting you to enter your BASE URL.

   <div style="text-align: center;">
     <img src="14_files/image11.png" alt="Rest Basis URL prompt" />
   </div>

3. Enter the copied URL, appending `/rest/3.0/` to it.

   **Example**: `http://localhost:8000/ADONIS16_0/rest/3.0/`.

   **Note**: Ensure ADONIS services are running, as Power BI pulls data directly from the ADONIS web client.

4. **Authenticate in Power BI**:
   - When prompted, switch to the **Basic** tab and enter your ADONIS credentials.

   <div style="text-align: center;">
     <img src="14_files/image12.png" alt="Enter ADONIS credentials in Power BI" />
   </div>

5. **Load Your Data**:
   - Once all steps are completed, the template should populate with your data, visualized in Power BI.

   <div style="text-align: center;">
     <img src="14_files/image13.png" alt="Power BI template with ADONIS data" />
   </div>

---

## 5. Security

Users must have the necessary permissions to read information from ADONIS. While enabling Basic Authentication for Power BI, note that it is also generally enabled, though access still requires user credentials, repository, and query ID to securely access data.
