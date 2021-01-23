# Create our first application

## Step 1: Create a Virtual Cloud Network
1. From the OCI Services menu, click **Virtual Cloud Networks** under **Networking**. Select the compartment assigned to you from the drop down menu on the left side of the screen(you may need to scroll down to see the dropdown) and Click **Start VCN Wizard**.
    ![](./images/HAApplication_001.png)  
    <span style="color: red">NOTE: Ensure the correct Compartment is selected under COMPARTMENT list</span>
2. Choose **VCN with Internet Connectivity** and click **Start VCN Wizard**.
    ![](./images/HAApplication_002.png)  
3. Fill out the dialog box:
    - **VCN Name**: Provide a name
    - **Compartment**: Ensure your compartment is selected
    - **VCN CIDR Block**: Provide a CIDR block (10.0.0.0/16)
    - **Public Subnet CIDR Block**: Provide a CIDR block (10.0.1.0/24)
    - **Private Subnet CIDR Block**: Provide a CIDR block (10.0.2.0/24)
    - Click *Next*

    ![](./images/Function_001.png)  
    ![](./images/HAApplication_004.png)  
4. Verify all the information and Click **Create**.
    ![](./images/Function_002.png) 
5. This will create a VCN with the following components.
    - VCN
    - Public subnet
    - Private subnet
    - Internet gateway (IG)
    - NAT gateway (NAT)
    - Service gateway (SG)
6. Click **View Virtual Cloud Network** to display your VCN details.
    ![](./images/HAApplication_006.png)  
    ![](./images/Function_003.png)  

## Step2: Setup Policy
If you are using *emeaccoe* tenancy or a tenancy is provided for you for the workshop, policies might be created for you. In that case you do not need to setup policies, skip this step. Ask you trainer!

1. From the OCI services menu click **Policies** under **Identity**.
    ![](./images/Function_040.png)  
2. Make sure that the compartment you created your VCN in is selected and then click Create Policy.
    ![](./images/Function_041.png)  
3. Type `FunctionApplicationPolicies` into the name section and type `Allow functions to work` in the description section. Scroll down to the Policy statements section. Click the **+ Another Statement**.
    ![](./images/Function_042.png)  
    Copy and paste the following as your first policy statement.
    ```
    allow service FAAS to use virtual-network-family in tenancy
    ```
    Copy and paste the following as your second policy statement.
    ```
    allow service FAAS to read repos in tenancy
    ```
    Click **Create**.
    ![](./images/Function_043.png)  
    Verify that your policy has been added to the policy list.
    ![](./images/Function_044.png)  

## Step3: OCIR Login
Follow the guide for [Log in to Oracle Cloud Infrastructure Registry](https://docs.oracle.com/en-us/iaas/Content/Functions/Tasks/functionslogintoocir.htm)


## Step4: Create a Function Application
Next we will create our first application.
1. From the OCI services menu click **Functions** under **Developer Services**.
    ![](./images/Function_039.png)  
2. Click **Create Application** and fill out the dialog box.
    - **NAME**: WorkshopFunctionApplication
    - **VCN in** : Choose the compartment where your VCN was created
    - **SUBNETS** : Choose your VCN's public subnet
    
    Click **Create**.
    ![](./images/Function_030.png)  
3. Scroll down and click on **Getting Started**. and **Local Setup**
    ![](./images/Function_045.png)  
    Follow the steps documented within Getting Started. On the first step, you need to make a choice of a lanugage selection. You need to delete the other options.

    **Important**: While giving a name for repository, on a shared tenancy environment, make sure that it is unique.