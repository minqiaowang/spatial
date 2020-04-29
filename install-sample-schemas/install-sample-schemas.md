# Install Sample Schemas for Spatial

## Introduction

### Objectives

-   Prepare the sample schema for spatial

### Lab Prerequisites

This lab assumes you have completed the following labs:
* Lab: Login to Oracle Cloud
* Lab: Generate SSH Key
* Lab: Setup


## Step 1: Download Sample Schemas installation Scripts
1.  Sudo to **oracle** user. Run this command to download the database sample schemas installation scripts. You will download a zip file named **v19.2.zip**.
    ````
    <copy>
    sudo su - oracle
    wget https://github.com/oracle/db-sample-schemas/archive/v19.2.zip
    </copy>
    ````
    ![image-20200429133037177](images/image-20200429133037177.png)
    
    

2.  Unzip the zip file you downloaded, and cd to the directory.

    ````
    <copy>
    unzip v19.2.zip
    cd  cd db-sample-schemas-19.2/
    </copy>
    ````
    ![image-20200429133418845](images/image-20200429133418845.png)

3.  Change all embedded paths to match your working directory. The installation scripts need your current directory embedded in various locations. Use a text editor or the following Perl script to make the changes, replacing occurrences of the token `__SUB__CWD__` with your current working directory.

    ```
    <copy>
    perl -p -i.bak -e 's#__SUB__CWD__#'$(pwd)'#g' *.sql */*.sql */*.dat 
    </copy>
    ```

    ![image-20200429133949928](images/image-20200429133949928.png)

    
## Step 2: Install the Sample Schemas

1. Before install, let's check the oracle environment

    ````
    <copy>
    . oraenv
    ORCL
    </copy>
    ````

    ![image-20200429134245301](images/image-20200429134245301.png)

2. You can now install the whole sample schemas. In this spatial lab, we only use the **OE** schema. The **OE** schema depend on **HR** schema. So in the next steps, we will install only the **HR** and **OE** schema.

    Run the following command to install **HR** schema first.

    ````
    <copy>
    sqlplus system/Ora_DB4U@orclpdb @./human_resources/hr_main.sql hr users temp Ora_DB4U ./log localhost:1521/orclpdb
    exit
    </copy>
    ````
     ![image-20200429135059926](images/image-20200429135059926.png)

    Then, install the **OE** schema.

    ````
    <copy>
    sqlplus system/Ora_DB4U@orclpdb @./order_entry/oe_main.sql oe users temp hr Ora_DB4U /home/oracle/db-sample-schemas-19.2/order_entry/ ./log v3 localhost:1521/orclpdb
    exit
    </copy>
    ````

     ![image-20200429135420511](images/image-20200429135420511.png) 

    You may now proceed to the next lab.

## Acknowledgements

- **Author** - Minqiao Wang, DB Product Management, April 2020
- **Last Updated By/Date** - 

See an issue?  Please open up a request [here](https://github.com/oracle/learning-library/issues).   Please include the workshop name and lab in your request.    Please include the workshop name and lab in your request. 