# Welcome to Concord! :sunglasses:
Use this guide to set up your own Concord instance. Or just use this one, don't change the configs, just add your playbook, playbook flows, inventory, see below guides.

- [Concord important links](https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/README.md#concord-important-links)
- [Concord access](https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/README.md#concord-access)
- [Concord Onboarding](https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/README.md#concord-onboarding)
- [Github setup](https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/README.md#github-setup)
- [Slack Integration](https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/README.md#slack-integration)
- [How to run a playbook](https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/README.md#how-to-run-a-playbook)

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
       ![image](https://gecgithub01.walmart.com/storage/user/87772/files/2bffcbd3-cb16-4c0d-88cc-3892030cc04a)

     - Search for the individual you want to add, assign the role, click on **save changes**
       ![image](https://gecgithub01.walmart.com/storage/user/87772/files/4ecd3d40-30d4-47d6-abcb-81ff74ff3593)


4. Steps to add groups:
     - Click on the new team name. Under the Members tab, click on edit.
       ![image](https://gecgithub01.walmart.com/storage/user/87772/files/a71623ac-c7ac-4453-b7a6-bc98160f1039)

     - Search for the group you want to add, assign the role, click on **save changes**
       ![image](https://gecgithub01.walmart.com/storage/user/87772/files/3e11c21f-e4ad-465e-99f8-46e8fe6f660c)

5. Now go to **Organizations → Your_Org_Name → Projects → Your_Project_name → Access → Edit**
6. Enter the team name you created in step 2. It should be in the dropdown.
7. Give this team the appropriate access level and click on Save Changes.
   ![image](https://gecgithub01.walmart.com/storage/user/87772/files/fa77e76d-e26d-4b86-9b7b-0e0c8d7a5bc9)


8. Now the individuals and/or groups will have access to your project.

---

### Concord Onboarding
To start using Concord to run playbooks on single or multiple servers, you first need to check if your organization exist and has access to Concord. If not, you need to submit a request via Jira ticket to get your organization created.

- Check here to find out your Organization name and cost center. https://teamrosters.walmart.com/app/#/
- Go to https://concord.prod.walmart.com/#/org and see if you can find your organization in the list.
      - Disable this incase the organization does exist but you do not have access to it. ![image](https://gecgithub01.walmart.com/storage/user/87772/files/fcfbb9ac-7bea-4e11-b29e-5c7aedbef33b)
      
     - Ask your manager, the organization might be named differently due to restrictions on certain characters in the name.
- If Organization is not created, click on this link [Request a new Concord Organization](https://concord.prod.walmart.com/api/v1/org/SDE/project/sde-onboarding/repo/main/start/concord_prepareCreateOrg). This will start a Concord process, fill out the details requested and a Jira ticket will be created.
      - This requires your manager's approval. A simple screenshot of an email will suffice.

**Steps to start using Concord to run playbooks.**
1. Create a GIT repository. https://gecgithub01.walmart.com/
      - For this guide, we will be referring to this. https://gecgithub01.walmart.com/maa-platform-engineering/Concord
2. Add a concord.yml file in the root directory.

      - Basic minimal example to get started: ![image](https://gecgithub01.walmart.com/storage/user/87772/files/d070ed88-c953-4abc-ab57-686fe83d5ea0)

3. Assuming that your organization is created in Concord, go to the [Concord console](https://concord.prod.walmart.com/#/org) and click into your organization.
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

        ![image](https://gecgithub01.walmart.com/storage/user/87772/files/2cdda30e-0ba9-4a5e-a29a-196edff11025)

8. You now have a Concord UI that is connected to your Git repo and is ready to be customized and used.

---

### GitHub setup
Your GitHub setup with look like the following, at least as a base to start with.
- [Inventories](https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/README.md#inventories)
- [Playbooks](https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/README.md#playbooks)
- [Concord YAML](https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/README.md#concord-yaml)
- README.md (optional but good to have)

#### Inventories
The inventories directory can be broken down by environments, projects, etc. Your call, you can choose to keep everything in 1 inventory.ini file.
Each environment (if you choose multiple environments) will have its own inventory.ini file that will list the hosts(servers) you want to run your playbook on.

Example: ![image](https://gecgithub01.walmart.com/storage/user/87772/files/22d9326d-4b35-4da3-82f3-128935f13414)

#### Playbooks
This directory will contain all your Ansible playbooks in YAML format. Example: **Concord/playbook/MAA_Tech_Solutions/Linux_Info.yml**
Follow this as an example of an Ansible Playbook. https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/playbook/Linux_Info.yml

- The hosts section of the playbook refers to the inventory.ini file. For this example, the hosts is called target_hosts, which is a variable defined in your Playbook's flow.yml under 'flows'.

![image](https://gecgithub01.walmart.com/storage/user/87772/files/b934b2e0-c55e-419a-b08a-e59921e5f5bb)

#### Concord YAML
The concord.yml contains all the information Concord needs to connect the Concord UI with this Git repo.
Refer to this as an example: https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/concord.yml

![image](https://gecgithub01.walmart.com/storage/user/87772/files/2249b3ec-eecd-4682-bd2f-d7cf6d5ae42c)

Use the above as a template and fill in the details as need.

---

### Slack Integration
Steps to integrate Slack with Concord so we can get notification when a Concord process has started/errored/completed.
1. Create a Slack channel. Ex: maa_engineering_concord
2. In that Slack channel, type in @concord and hit enter. This will add the concord app in your channel. Be sure to select the one that says concord app, not concordbot app.

![image](https://gecgithub01.walmart.com/storage/user/87772/files/5f3baa01-4baf-4e83-8e81-7276729fcbcd)

3. Create a directory within your Concord repo called stack_flows.yml. Use this: https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/concord/stack_flows.yml
4. Open your concord.yml and ensure that it has the following arguments:
  - slackChannel: "#maa_engineering_concord"   <------ put your Slack channel name
  - slackUsername: "concord-server"  <---- You can put any string here
  - slackNotification: "enabled"
  - slackIconEmoji: ":concord-doge:"  <--- Replace this with any emoji icon you wish

  ![image](https://gecgithub01.walmart.com/storage/user/87772/files/008dbc1f-a499-4f34-a671-1edbc355e47e)

5. Head over to where you have your flows defined.
  - If you chose to put them in concord.yml under flows section, go there.
  - If you have them separately in another folder, go there.
6. Add in a line before your playbook run called "-call :slackNotify"
7. Make sure that your playbook step has the "-try" and "error" arguments which has your playbook step nested in it.
```
flows:
  LinuxInfo:
  - checkpoint: "Start"
  - call: slackNotify
  - checkpoint: "User Input"
  - form: linux_server
  - checkpoint: "Run Playbook"
  - try: 
     - task: ansible
       in:
         config:
           defaults:
             forks: 50
           ssh_connection:
             pipelining: True
         auth:
           privateKey:
             user: concord-server
             secret:
               name: GCP
         playbook: playbook/MAA_Tech_Solutions/Linux_Info.yml
         inventoryFile: inventory.ini
         extraVars:
           target_hosts: ${linux_server.target}
    error:
     - call: slackNotify
       in:
         msgData:
           text: ":warning: Playbook finished with error: ${result.error}"
     - throw: "Ansible playbook has failed" 
  - call: slackNotify
     in:
       msgData:
         text: ":green-ball: Ansible playbook has been successfully completed"
```
8. Add in a line after your playbook run called "-call :slackNotify"
9. Now you should get a slack notification in your slack channel when a Concord Process has started, finished successfully, or finished with errors.

### How to run a playbook
- Important: If you haven't setup your playbook, inventory file, flows yet then please do. Follow this [Github setup](https://gecgithub01.walmart.com/maa-platform-engineering/Concord/blob/main/README.md#github-setup)
- The server(s) you want to run the playbook on also need a public key installed on them. The process varies depending on the cloud provider.
  - Process to obtain the key from Concord:
    - Log into Concord UI. https://concord.prod.walmart.com/#/org/Technology_Platform_Mergers_and_Acquisitions/project/MAA_Playbooks/process
    - Navigate to Organizations → Your_Org_Name → Secrets.
    - Select New Secret on the toolbar.
    - Provide a string, for example, mykey as a Name and select Generate a new key pair as a Type.
    - Click Create
    - Click into the secret and copy the public key.

Steps to run a playbook in Concord.
1. Log into Concord UI. https://concord.prod.walmart.com/#/org/Technology_Platform_Mergers_and_Acquisitions/project/MAA_Playbooks/process
2. Click on "Repositories" and then click on the blue play icon on the right. See screenshot below.

![image](https://gecgithub01.walmart.com/storage/user/87772/files/8475b7c2-f638-43b4-9ef2-62b4aba56c73)

3. Select your playbook from the dropdown menu and click on start. Then click on "Open the process page" in the next pop up.

![image](https://gecgithub01.walmart.com/storage/user/87772/files/9054da9e-9d9c-4370-9c73-baffa1cff801)

4. Click on "Form Wizard". This will take your to a prompt that will ask you for the hostname of the server(s) you want the playbook to run. Click on Submit.

![image](https://gecgithub01.walmart.com/storage/user/87772/files/24f7f364-22ee-4165-b3b0-056480a262b0)

Your playbook should be running now. Click on "Logs" to view the progress. You can also check your Slack channel for update, assuming you have Slack setup.
