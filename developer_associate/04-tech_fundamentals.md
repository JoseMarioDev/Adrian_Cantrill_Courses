## 🗒️  Notes

👨🏽‍💻  YAML 101

- collection of key/value pairs
- supports strings, floats, ints, bool, lists, dict
- supports lists
    - lists can be inline
    - or indented with dashes "-"

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6ce47b18-cefd-4771-a5b0-d0d18655f81b/Screen_Shot_2021-05-10_at_3.28.33_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6ce47b18-cefd-4771-a5b0-d0d18655f81b/Screen_Shot_2021-05-10_at_3.28.33_PM.png)

- values can be in parentheses or not, both are valid
- supports dictionaries - a list of dictionaries
- is used for [CloudFormation](https://www.notion.so/CloudFormation-b92ad6a9f91d4cbf9d879fea5f1fb61d)
- indentation matters

---

👨🏽‍💻  JSON 101

- key/value pairs
- similar to YAML but format is just different
- doesn't care about indentation
- values can be string, obj, num, array, bool, or null
- supports objects and arrays.  can be nested
- used for AWS policies

---

🔑  Encryption 101 - part 1

encryption approaches

- encryption at rest -  data stored in hardware in encrypted form
- encryption in transit - apply encryption wrapper while data is being transferred

concepts

- Plaintext - unencrypted data
- Algorithm - code takes plaintext and key and encrypts data
- key - password
- Ciphertext - result of data that is encrypted with algorithm and key

symmetric encryption

- same key is used for encryption and decryption process
- good for local encryption like data on a laptop
- not so good when data needs to be sent over network between parties

asymmetric encryption

- uses 2 keys - public key and private key
- no requirement to exchange keys in advance
- used when 2 or more parties are involved and havent met before
- used by SSL, TLS, PGP, SSH
- much more difficult to do vs symmetric

---

🔑  Encryption 101 - part 2

signing

- when receiver acknowledges to sender message received
- receiver sends message encrypted w/private key to sender
- sender uses public key to decrypt message and verify if private key is correct
- inverse of asymmetric encryption process
- used for ID verification and login systems

steganography

- process of hiding something in something else
- think of "using invisible ink" in spy tactics
- embed data in other data

---

🌎  Network Start Pack 0

OSI Model

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fd7c330e-3b14-48d7-831f-87269dd7b703/Screen_Shot_2021-05-10_at_4.54.08_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fd7c330e-3b14-48d7-831f-87269dd7b703/Screen_Shot_2021-05-10_at_4.54.08_PM.png)

---

🌎  Network Start Pack 1 - Physical Layer

- physical medium can be copper, fiber, or wifi
- used to connect computers together
- hardware: hub - repeats to all devices on network, including collisions
- no access control
- no unique identified devices

---

🌎  Network Start Pack 2 - Data Link part 1

- -

🌎  Network Start Pack 2 part 2

🌎  Network Start Pack 3 part 1

🌎  Network Start Pack 3 part 2

🌎  Network Start Pack 4&5 part 1

🌎  Network Start Pack 4&5 part 2

🌎  Network Start Pack NAT part 1

🌎  Network Start Pack NAT part 2

🌎  Network Start Pack Subnetting part 1

🌎  Network Start Pack Subnetting part 2

🚫  Distributed Denial of Service Attack

🛣️. SSL and TLS