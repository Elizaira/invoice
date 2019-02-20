[//]: # (SPDX-License-Identifier: CC-BY-4.0)

## Hyperledger Fabric Samples

Please visit the [installation instructions](http://hyperledger-fabric.readthedocs.io/en/latest/install.html)
to ensure you have the correct prerequisites installed. Please use the
version of the documentation that matches the version of the software you
intend to use to ensure alignment.

## Download Binaries and Docker Images

The [`scripts/bootstrap.sh`](https://github.com/hyperledger/fabric-samples/blob/release-1.3/scripts/bootstrap.sh)
script will preload all of the requisite docker
images for Hyperledger Fabric and tag them with the 'latest' tag. Optionally,
specify a version for fabric, fabric-ca and thirdparty images. Default versions
are 1.4.0, 1.4.0 and 0.4.14 respectively.

```bash
./scripts/bootstrap.sh [version] [ca version] [thirdparty_version]
```

## License <a name="license"></a>

Hyperledger Project source code files are made available under the Apache
License, Version 2.0 (Apache-2.0), located in the [LICENSE](LICENSE) file.
Hyperledger Project documentation files are made available under the Creative
Commons Attribution 4.0 International License (CC-BY-4.0), available at http://creativecommons.org/licenses/by/4.0/.



## INVOICE (Group 6)


### Development Environment
#### Go version: go version go1.10.4 linux/amd64
#### Operating System: Ubuntu 18.04.1 LTS

**NOTE:** Please make sure that you have no existing docker containers that could affect this application’s fabric network before following the instructions. Also, make sure that you don’t have any existing key-store data to avoid errors during the deployment of the network. If you have existing docker containers, you can clean it via this command on terminal: `docker stop $(docker ps -aq) && docker rm $(docker ps -aq)`.

### Setup the Environment:
#### Step 1: 
create folder **"invoice"** inside the fabric-samples. Copy all the files inside except for the **"node_modules"**.

**NOTE:** The files you need inside the folder are the following:

<pre>fabric-samples/
  | ---- invoice/
              | ---- app.js
              | ---- enrollAdmin.js
              | ---- package.json
              | ---- registerUser.js
              | ---- startFabric.sh
</pre>

#### Step 2:
Create a folder **"invoice"** inside **/fabric-samples/chaincode**
Then copy the folder **"go"** in the repository **/fabric-samples/chaincode/invoice**

This will be the output:
<pre>fabric-samples/
  | ---- chaincode/
     | ---- invoice/
        | ---- go/
           | ---- invoice.go
</pre>

#### Step 3:
Open the terminal to run the file. Go to the directory where your invoice folder located **fabric-samples/chaincode/invoice**. Run **./startFabric.sh**.

Then execute the following:

* npm install or npm i
* node enrollAdmin.js
* node registerUser.js
* node app

#### Step 4:
To test the if the file is working you can use POSTMAN or Insomia REST Client or any other tools.

#### Testing Endpoints

#### Display All Invoices
##### http://localhost:3000/
##### Use the GET http request in this function as we are getting data
<br />
<br />
<br />

#### Raise Invoice
##### http://localhost:3000/invoice
##### Use the POST http request in this function as we are pushing data
Select **Form URL Encoded** as a structure
##### Parameters
+ invoiceid
+ invoicenum
+ billedto
+ invoicedate
+ invoiceamount
+ itemdescription
+ gr
+ ispaid
+ paidamount
+ repaid
+ repaymentamount

##### NOTE: gr , ispaid , paidamount , repaid , repaymentamount default values are as follows N , N , 0 , N , 0
**gr = N**
<br />
**ispaid = N**
<br />
**paidamount = 0**
<br />
**repaid = N**
<br />
**repaymentamount = 0**
<br />
<br />
<br />

#### Goods Received
##### http://localhost:3000/invoice
##### Use the PUT http request in this function as we are modifying a data
Select **Form URL Encoded** as a structure

##### Parameters
+ invoiceid
+ gr
<br />
<br />
<br />

#### Bank Payment to Supplier
##### http://localhost:3000/invoice
##### Use the PUT http request in this function as we are modifying a data
Select **Form URL Encoded** as a structure

##### Parameters
+ invoiceid
+ ispaid
<br />
<br />
<br />

#### OEM Repays to Bank
##### http://localhost:3000/invoice
##### Use the PUT http request in this function as we are modifying a data
Select **Form URL Encoded** as a structure

##### Parameters
+ invoiceid
+ repaid
<br />
<br />
<br />

