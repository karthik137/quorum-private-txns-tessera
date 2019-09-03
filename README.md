# quorum-private-txns-tessera
Private transactions using tessera


### Transaction manager in quorum

Quorum has provided two transaction managers.

1) Constellation
2) Tessera

### What is tessera?

Tessera is Java implementation of peer-to-peer encrypted message exchange for transaction privacy.

Tessera is a stateless Java system that is used to enable the encryption, decryption, and distribution of private transactions for Quorum.

#### Features of tessera:

1) Generates and maintains a number of private/public key pairs

2) Self manages and discovers all nodes in the network (i.e. their public keys) by connecting to as few as one other node

3) Provides Private and Public API interfaces for communication:
    a) Private API - This is used for communication with Quorum
    b) Public API - This is used for communication between Tessera peer nodes

4) Provides two way SSL using TLS certificates and various trust models like Trust On First Use (TOFU), whitelist, certificate authority, etc.

5) Supports ip whitelist.

6) Connects to any SQL DB which supports the JDBC client.



### Prerequisites


    a) Java 8 (if using the pre-built release jars)
    b) Java 8 - 11 (if building from source)
    c) Maven (if building from source)
    d) libsodium (if using kalium as the NaCl implementation)



#### Private transactions walkthrough

> Setup quorum network

> Here we will be using quorum-maker version 2.6.2 (This has tessera)

```
kirito@kirito-TUF-GAMING-FX504GE-FX80GE:~/quorum-maker/v2.6.2/quorum-maker$ ./setup.sh --tessera
   ______   __      __
  / ____ \ |  \    /  |  
 / /    \ \|   \  /   |  
 | |     | |    \/    |  
 | |     | | |\    /| |  
 | |     |  \| \  / | |  
 \ \____/ /\ \  \/  | |  
  \______/  \_\     |_|  Version 2.6.2 Built on Quorum 2.2.1

Please select an option: 
 1) Create Network 
 2) Join Network 
 3) Attach to an existing Node 
 4) Setup Development/Test Network 
 5) Exit
option: 4
Please enter a project name[Default:TestNetwork]:
Please enter number of nodes to be created[Default:3]:
Creating TestNetwork with 3 nodes. Please wait... 
 [▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐ ](100%)
Project TestNetwork created successfully. Please execute docker-compose up from TestNetwork directory

NODE   PUBLIC-KEY                                    IP         RPC    WHISPER  TESSERA  RAFT   NODEMANAGER  WS
node1  P+3IDN+Vjd8MyFgjPmRlLFlzIMjdCtXWsHqBBcwqu0Q=  10.50.0.2  22000  22001    22002    22003  22004        22005
node2  Ilrf/+q+SMH5jnsrILE/T4ufx4HX8X+IrMk7cdcURGc=  10.50.0.3  22000  22001    22002    22003  22004        22005
node3  gZgmCCSrCQxPMKl4BsFzXv4QX7YNoPYP01izwN+jSCY=  10.50.0.4  22000  22001    22002    22003  22004        22005

```


### Tessera REST API Documentation

```
https://jpmorganchase.github.io/tessera-swagger/index.html#/
```

#### Using tessera API's

##### Get Party info

> Request

```
API --> http://10.50.0.4:22002/partyinfo

TYPE --> GET
```

> Response

```json
{"url":"http://10.50.0.4:22002/","peers":[{"url":"http://10.50.0.4:22002/","lastContact":"2019-09-03T09:51:00.880Z"},{"url":"http://10.50.0.2:22002/","lastContact":"2019-09-03T10:02:10.674Z"},{"url":"http://10.50.0.3:22002/","lastContact":"2019-09-03T10:02:10.040Z"}],"keys":[{"key":"gZgmCCSrCQxPMKl4BsFzXv4QX7YNoPYP01izwN+jSCY=","url":"http://10.50.0.4:22002/"},{"key":"P+3IDN+Vjd8MyFgjPmRlLFlzIMjdCtXWsHqBBcwqu0Q=","url":"http://10.50.0.2:22002/"},{"key":"Ilrf/+q+SMH5jnsrILE/T4ufx4HX8X+IrMk7cdcURGc=","url":"http://10.50.0.3:22002/"}]}

```


##### Upcheck
> Request

```
API --> http://10.50.0.4:22002/upcheck

TYPE --> GET
```

> Response

```
I'm up!

```

#####  Push transactions between nodes

> Request

```

```



