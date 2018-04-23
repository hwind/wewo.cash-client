# wewo.cash-client
The goal of https://wewo.cash is to help everyone be able to access the information from blockchain easily, to enjoy the benefits of blockchain technology.Today, accessing the information from blockchain is not that straight forward. https://wewo.cash tries to bridge the gaps between people and blockchain.

[MEMO](https://memo.cash/protocol) is an on-chain social network protocol based on Bitcoin Cash. It makes people be able to post like twitter by sending a bitcoin cash transaction. Due to the nature of blockchain, these data can be accessed by anyone in the world, it's not owned by any company. You don't need to worry about data missing when the company is closed or your account is closed.

HERE is the REST API interface to access MEMO account & posts. You can easily build frontend on top of it to have your customized client, but be able to connect with anyone in the world who's using MEMO with any other clients.

# DISCLAIMER
* wewo.cash may update these APIs in future. We will try to keep the backward compatibility as much as we can, but it's not guranteed.
* Though from techonogy's perspective, anyone can post anything on the blockchain and no one can delete it, wewo.cash perserve the rights to filter the content to be compliance with moral and legal requirements.

# Host Endpoint
https://wewo.cash/api/v1/

# Account
GET /account
This API returns the MEMO account data.

Request:
Param |	required | data type | description | default
---|---|---|---|---|---
address | false | string | only legacy format is supported today | N/A

Response:
Param |	required | data type | description
---|---|---|---|---|---
txHash | true | string |  | N/A
address | true | string | The BCH address which send out the transaction to set its MEMO name
name | true | string | The updated MEMO account name
lastUpdateTime | true | datetime | The transaction time

# Memopost
GET /memopost
This API returns the MEMO post data.
Request:
Param |	required | data type | description | default
---|---|---|---|---|---
address | false | string | only legacy format is supported today | N/A

Response:
Param |	required | data type | description
---|---|---|---|---|---
txHash | true | string |  | N/A
address | true | string | The BCH address which send out the transaction to post msg
msg | true | string | The msg posted by the address
lastUpdateTime | true | datetime | The transaction time

# Follow
GET /follow
This API returns the MEMO follow/unfollow data

Request:
Param |	required | data type | description | default
---|---|---|---|---|---
address | false | string | only legacy format is supported today | N/A

Response:
Param |	required | data type | description
---|---|---|---|---|---
txHash | true | string |  | N/A
address | true | string | The BCH address which send out the transaction to follow someone else
destAddress | true | string | The address being followed
isFollow | true | boolean | True means follow, False means unfollow
lastUpdateTime | true | datetime | The transaction time

# Like
GET /account
This API returns the MEMO like data

Request:
Param |	required | data type | description | default
---|---|---|---|---|---
address | false | string | only legacy format is supported today | N/A

Response:
Param |	required | data type | description
---|---|---|---|---|---
txHash | true | string |  | N/A
address | true | string | The BCH address which send out the transaction to like a post
destTxHash | true | string | The transaction being liked
lastUpdateTime | true | datetime | The transaction time

# Posts
GET /posts
This API is a high level aggregation across account/post/like. It tells who (name) post what(msg) at when(time), and how many people like it.

Request:
Param |	required | data type | description | default
---|---|---|---|---|---
address | false | string | only legacy format is supported today | N/A

Response:
Param |	required | data type | description
---|---|---|---|---|---
txHash | true | string |  | N/A
address | true | string | The BCH address which send out the transaction
name | true | string | The updated MEMO account name
msg | true | string | The msg posted by the address
timestamp | true | datetime | The post timestamp
like | true | int | The count of like on this post

# FAQ
* When are you going to support WRITE operations so that people can set name, post msg ... from wewo.cash

Answer: We do plan to support WRITE operations. We don't want to store customer's privacy key on the server, so we are looking for a different solution here. We think the private key should be owned by user themselves in blockchain age. For MEMO, once you lost your private key, you not only lose a few cents of BCH, but also **totally** lose your MEMO account. Also, once giving the private key to any centralize company, you give up the control of your account, then why not just use twitter.
