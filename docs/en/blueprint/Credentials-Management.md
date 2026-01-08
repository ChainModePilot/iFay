Here, "Credential" is a generalized concept. For a natural person user, most of the time, the user must hold one or more tickets to have the right to use hardware or software. The following 7 types are collectively referred to as credentials (more types may be added with iterations):

![Credential Management](../images/blueprint/438c8285-8499-449c-aaae-fbc88daf8460.png)

- [Identity (FayID)](./Credentials-Management#identityfayid)
- [Account / Password](./Credentials-Management#account--password)
- [Certificate](./Credentials-Management#certificate)
- [Authorization](./Credentials-Management#authorization)
- [Access Token](./Credentials-Management#access-token)
- [Smart Contract](./Credentials-Management#smart-contract)
- [Digital tokens (MeriTokens)](./Credentials-Management#digital-tokens-meritokens)

<br>

Attention: Initially, all these tickets come from the host user. For greater security and easier management, all credentials from the host will be exchanged for a copy corresponding to the original credential. iFay uses this copy for login and authentication.

Of course, we do not believe that iFay cannot have its own credentials while the host cannot use them. Therefore, each type of credential will indicate whether its original owner is the host or iFay itself.

For example: When we need to verify the authenticity of personal information provided by someone, we may authorize iFay to directly log into the database for inquiry. To prevent the leakage of private data, iFay only needs to feedback whether it is true or false.



# Identity（FayID - an independent open-source project）

FayID is the unique and persistent identifier assigned to each iFay and coFay.
It is designed to be globally unique, human-recognizable, and machine-readable, enabling smooth identity migration when an iFay evolves from a personal assistant to an autonomous social actor.

Since each iFay is tied to at least one human, the total number of Fays will inevitably exceed the global human population by multiple orders of magnitude.
Any terminal device or software can serve as a Fay runtime environment. Over time, every independent device may be “ possessed” by a Fay (iFay or coFay), making the total number of Fays far greater than the number of devices themselves.

To enable seamless Fay-to-Fay communication, we need a universal, high-capacity, and developer-friendly encoding scheme—one that can scale with massive identity growth while remaining efficient and easy to use.

‼️ Therefore, we’ve launched [FayID as an independent open-source project](https://github.com/ChainModePilot/FayID), aiming to develop a universal identity recognition system.

For more details, please refer to the → [FayID documentation](https://github.com/ChainModePilot/FayID/wiki).


<br>

# Account / Password


<br>

# Certificate


<br>

# Authorization


<br>

# Access Token


<br>

# Smart Contract


<br>

# Digital tokens ([MeriTokens](https://github.com/ChainModePilot/Global-Merit-Chain/wiki))

