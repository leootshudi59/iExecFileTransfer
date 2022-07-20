# Ace
## _Web3 file transfer app powered by iExec_ 

Ace FT is the very first web3 file transfer application that is built with the [iExec](https://iex.ec) protocol. 
The choice of the iExec stack was a no-brainer given that it covers the key requirements for the implementation a trustworthy web3 file transfer application.
Moreover, the iExec protocols has a built-in data monetization capability that we are leveraging in this project.

## What are we fixing
We believe that Web 2 is broken and it’s time for a new paradigm shift that can restore our right to privacy and security. 
Up until the emergence of Web3 we were forced to endure untrustworthy corporations selling our data to other corporation or even governments and centralized databases containing our personal details being hacked on a regular basis.
Ace is an illustration that 
- there is a better way to do business when it comes to file transfer, one which doesn’t call for sacrificing our security nor our need for great level of service and experience. 
- there is no need for a man in the middle when I am sending personal holiday pics to my family!
- nobody would be able to sell my data without my consent that is enforced and verifiable onchain.


## Features

- "WeTransfer-like" experience,  simply drag and drop files you want to share
- Set the beneficiary in the form of 0x address or ENS
- Beneficiary email notification 
- Built-in monetization! You can sell your added value content and get paid in $RLC
- Cool visual background randomly sourced from [unsplash](https://unsplash.com) API


## Core principles

Ace's system design is making use of all three types of computing assets that are part of iExec’s marketplace model : application, processing power (CPU) and dataset. The section below explains how Ace is mapped against iExec core concepts. 

**Modelization**

_Datasets_
Files that are being transferred are represented as iExec encrypted datasets

_Application_
Our application is trivial as it consists of simply downloading the transferred file. In fact, the iExec protocol is taking care the authorization by ensuring that only the selected requester can trigger the download application for the given dataset (i.e transferred files)

_Processing power (CPU)_
The processing capacity required to execute the application is provided by workers in the iExec network. The execution relies on Intel SGX compatible workers only.

_Users types_
- Provider: This is the content creator who want to send its assets to someone (the beneficiary) with or without monetization.
- Beneficiary: This is the recipient of the files
- Requester: This is the person who is authorised to trigger the (download) application with the dataset as an input. In our case, the beneficiary of a file transfer and the requester are just the same user.
 

**File Transfer process**

- Step 1 - Preparation
The preparation stage consists of the File encryption, the ipfs upload and the dataset deployment (registration on the iExec marketplace)

![IMAGE_DESCRIPTION](https://bafybeigb3aodzwkqsf3kdffjodbluzxpvvpe5ixzz542jcec4swzl3wbqi.ipfs.infura-ipfs.io)
 

The encryption and deployment are handled with the [iExec SDK](https://github.com/iExecBlockchainComputing/iexec-sdk) whilst the IPFS upload is a pretty straight forward process when using a library like [ipfs-http-client](https://www.npmjs.com/package/ipfs-http-client).
You can refer to [This section of the iExec documentation](https://docs.iex.ec/for-developers/confidential-computing/sgx-encrypted-dataset) to get a more detailed explaination on how to use confidentials assets with iExec.


- Step 2 - Governance rules
The second step of the process is to set the authorization for the beneficiary and requester and an optional monetization parameter (i.e. how much RLC will the requester need to pay in order to run the download app with my files).
**From an iExec prospective this step is just an order being placed on the marketplace.**

Step 3 -  Beneficiary notification (non-iExec service)

Step 4 - Optional payment and file download

## Notification system

## Use cases

## Future consideration
Here are some features that could be implemented after v1. 
- **Copyright protection and licensing:** Making the application more intelligent with the integration of a library for creating invisible watermark over images, videos and PDFs.
- **KYC:** Add the ability for the content provider to get proofs about the beneficiary's identity. For example creator of adult material will be able to check that the beneficiary is over 18.
- **Subscriptions:** The version 1 works on the basis that the content creator manages the list of beneficiaries on a seperate system. The subscription model will allow people to register their interest and join a "fan" club. Content providers will be able to chose their subscription list rather than selecting beneficiaries one by one


## License

MIT

**Free Software, Hell Yeah!**
