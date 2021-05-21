## 🗒️ Notes

### 🗝️ Basics

Concepts

- regional and public service
    - separate product in each region
- lets you create, store, manage keys
- Symmetric and Asymmetric keys
- can perform cryptographic operations
- keys never leave KMS
    - provides FIPS 140-2 (L2) standard

CMK - Customer Master Keys

- logical container for actual keys
- contains few things:
    - id
    - date
    - policy
    - desc
    - state
- can be generated or imported
- maximum of 4kb of data encrypted

CMK Visually

- user creates CMK
- CMK encrypts key
- user call encrypt operation to encrypt data
    - decrypt to do the opposite
- CMK never leaves KMS
- never stored in plain text form

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6b80c6df-107d-4458-b3f1-f0b52461e6f7/Screen_Shot_2021-05-21_at_8.37.40_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6b80c6df-107d-4458-b3f1-f0b52461e6f7/Screen_Shot_2021-05-21_at_8.37.40_AM.png)

Data Encryption Keys (DEKs)

- another type of key KMS generates from CMKs
- used to encrypt data >4kb in size
- DEK is linked to a CMK
- KMS doesn't store the DEK in any way
    - it provides it to you
    - then discards
- KMS provides you with 2 versions of DEK
    - plaintext version
    - ciphertext version
- you encrypt data using the plaintext version
    - then discard the plaintext version of key
    - then store the encrypted key with data
- pass to KMS to decrypt

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3575855a-ce8e-4136-8d72-49afb34cce10/Screen_Shot_2021-05-21_at_8.45.24_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3575855a-ce8e-4136-8d72-49afb34cce10/Screen_Shot_2021-05-21_at_8.45.24_AM.png)

Key Concepts

- CMKs are isolated to region and never leave KMS
- 2 types of CMKs - AWS Managed or Customer Managed
- Customer managed keys are more configurable
- both types support key rotation
- CMKs contain backing key
- can create Alias that is a shortcut to CMK
- every CMK has a key policy(resource policy)
    - trust isn't automatic
    - key needs to trust the account
    - use in combine with IAM policies for role separation

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9e993da-251d-4982-8731-3f54f266dd84/Screen_Shot_2021-05-21_at_8.49.41_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9e993da-251d-4982-8731-3f54f266dd84/Screen_Shot_2021-05-21_at_8.49.41_AM.png)