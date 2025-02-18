# Welcome to Concord! :sunglasses:
Use this guide to set up your own Concord instance. Or just use this one, don't change the configs, just add your playbook, playbook flows, inventory, see below guides.

- [Concord important links](https://github.com/Samuel-Singh/Concord_Testing/tree/main?tab=readme-ov-file#concord-important-links)
- [Concord access](https://github.com/Samuel-Singh/Concord_Testing/tree/main?tab=readme-ov-file#concord-access)
- [Concord Onboarding](https://github.com/Samuel-Singh/Concord_Testing/tree/main?tab=readme-ov-file#concord-onboarding)
- [Github setup](https://github.com/Samuel-Singh/Concord_Testing/tree/main?tab=readme-ov-file#github-setup)
- [How to run a playbook](https://github.com/Samuel-Singh/Concord_Testing/tree/main?tab=readme-ov-file#how-to-run-a-playbook)

---

![image](https://github.com/user-attachments/assets/e2c97ebe-9136-47ee-8c18-09fba53668a4)

---

### Concord important links
Quick start: https://concord.walmartlabs.com/docs/getting-started/quickstart.html

Concord base URL: http://<your-concord-server>:8001/#/org

Sample Concord Github: https://github.com/Samuel-Singh/Concord_Testing

---

### Concord access
Below are the steps to give access to individuals and/or teams via LDAP.

1. Go to the Concord UI and navigate to **Organizations → Your_Org_Name → Teams → New team**
2. Give a name to your team and click create. You can add a description if you want to.
3. Steps to add individuals:
     - Click on the new team name. Under the Members tab, click on edit.

     - Search for the individual you want to add, assign the role, click on **save changes**

4. Steps to add groups:
     - Click on the new team name. Under the Members tab, click on edit.
     - Search for the group you want to add, assign the role, click on **save changes**

5. Now go to **Organizations → Your_Org_Name → Projects → Your_Project_name → Access → Edit**

6. Enter the team name you created in step 2. It should be in the dropdown.

7. Give this team the appropriate access level and click on Save Changes.

8. Now the individuals and/or groups will have access to your project.

---

### Concord Onboarding
To start using Concord to run playbooks on single or multiple servers, you first need to check if your organization exist and has access to Concord. If not, you need to contact the Concord administrator to create one and/or give you access.

- Go to https://concord.prod.walmart.com/#/org and see if you can find your organization in the list.
      - Disable this incase the organization does exist but you do not have access to it. ![image](https://github.com/user-attachments/assets/5ab1656a-6d38-4c94-9a79-8eca6e1ced3f)


**Steps to start using Concord to run playbooks.**
1. Create a GIT repository.
      - For this guide, we will be referring to this. https://github.com/Samuel-Singh/Concord_Testing
2. Add a concord.yml file in the root directory.

      - Basic minimal example to get started: ![image](https://github.com/user-attachments/assets/3b9cd7a6-9ef8-4117-a828-edf013dc7da1)

3. Assuming that your organization is created in Concord, go to the console: http://<your-concord-server>:8001/#/org and click into your organization.
4. A deploy key has to be created.
      - Verify that your organization ID is created as per the previous step.
      - Navigate to **Organizations → Your_Org_Name → Secrets**.
      - Select **New Secret** on the toolbar.
      - Provide a string, for example, mykey as a **Name** and select **Generate a new key pair as a Type**.
      - Click **Create**.
5. This key has to be installed in your git repo. This is under **Settings → Deploy keys → Add deploy key**
6. Create your project under your organization.
      - Log into the [Concord Console](https://concord.prod.walmart.com/#/org) user interface.
      - Navigate to **Organizations → Your_Org_Name → Projects**.
      - Select **New Project** on the toolbar.
      - Provide a **Name** for the project. For example, myproject.
      - Click **Create**.
      - Under the **Repositories** tab, select **Add repository**.
      - Provide a **Name** for the repository. For example, myrepository.
7. Connect your Project with your git repo.
      - Under Organizations → Your_Org_Name → Projects → Repositories tab, select Add repository.
      - Enable Custom authentication.
      - Select the Credentials of the key you created in step 4.
      - Provide a Name for the repository. For example, GTP.
      - Provide the URL of the git repo. Example: git@gecgithub01.walmart.com:maa-platform-engineering/Concord.git
      - Enter "main" as the Branch/Tag
      - Click on Test connection on the bottom right to ensure that all the credentials are working as expected.

        ![AddaRepo](https://github.com/user-attachments/assets/7ca0a716-2b42-4cea-a7f7-3adfb9a1708b)

8. You now have a Concord UI that is connected to your Git repo and is ready to be customized and used.

---

### GitHub setup
Your GitHub setup with look like the following, at least as a base to start with.
- [Inventories](https://github.com/Samuel-Singh/Concord_Testing/blob/main/inventory.ini)
- [Playbooks](https://github.com/Samuel-Singh/Concord_Testing/tree/main/playbook)
- [Concord YAML](https://github.com/Samuel-Singh/Concord_Testing/blob/main/concord.yml)
- README.md (optional but good to have)

#### Inventories
The inventories directory can be broken down by environments, projects, etc. Your call, you can choose to keep everything in 1 inventory.ini file.
Each environment (if you choose multiple environments) will have its own inventory.ini file that will list the hosts(servers) you want to run your playbook on.

Example: ![image](https://github.com/user-attachments/assets/364dfdec-08c6-4aee-81a8-8496b62324df)

#### Playbooks
This directory will contain all your Ansible playbooks in YAML format. Example: **Concord_Testing/blob/main/playbook/Linux_Info.yml**
Follow this as an example of an Ansible Playbook. https://github.com/Samuel-Singh/Concord_Testing/blob/main/playbook/Linux_Info.yml

- The hosts section of the playbook refers to the inventory.ini file. For this example, the hosts is called target_hosts, which is a variable defined in your Playbook's flow.yml under 'flows'.

![play](https://github.com/user-attachments/assets/03ee5831-34dc-4c4c-8cc9-4981e1526bd0)

#### Concord YAML
The concord.yml contains all the information Concord needs to connect the Concord UI with this Git repo.
Refer to this as an example: https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/concord.yml

![concord](https://github.com/user-attachments/assets/764bc381-32bc-46ef-adcb-ec40de504d22)

Use the above as a template and fill in the details as need.

---

### How to run a playbook
- Important: If you haven't setup your playbook, inventory file, flows yet then please do. Follow this [Github setup](https://github.com/Samuel-Singh/Concord_Testing/tree/main?tab=readme-ov-file#github-setup)
- The server(s) you want to run the playbook on also need a public key installed on them. The process varies depending on the cloud provider.
  - Process to obtain the key from Concord:
    - Log into Concord UI.
    - Navigate to Organizations → Your_Org_Name → Secrets.
    - Select New Secret on the toolbar.
    - Provide a string, for example, mykey as a Name and select Generate a new key pair as a Type.
    - Click Create
    - Click into the secret and copy the public key.

Steps to run a playbook in Concord.
1. Log into Concord UI.
2. Click on "Repositories" and then click on the blue play icon on the right. See screenshot below.

![image](https://github.com/user-attachments/assets/b4ed73bc-6598-4fb6-bdf6-80018160c045)

3. Select your playbook from the dropdown menu and click on start. Then click on "Open the process page" in the next pop up.
4. Click on "Form Wizard". This will take your to a prompt that will ask you for the hostname of the server(s) you want the playbook to run. Click on Submit.

Your playbook should be running now. Click on "Logs" to view the progress. You can also check your Slack channel for update, assuming you have Slack setup.
