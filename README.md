# @ericyangchen/npmyangtest



#### 安装

```javascript
// 插件名称待定
npm i xxx
```



#### 使用

##### 发送验证信息

```javascript
import { sendUserInfo } from 'xxxx'

/***
params
{
  appId: string,
  backDoc: string,
  country: string,
  docId: string,
  docType: string,
  frontDoc: string,
  name: string,
  ownerDid: string,  sdk 方法生成
}
**/

await sendUserInfo({...params}, apiKey)

/***
returnType 
成功发送 return true
异常 Throw error message
***/
```



##### 获取用户 `credential`

```javascript
import { getVcList } from 'xxxx'

/**
params
ownerDid: string,  sdk 方法生成
**/

const result = await getVcList(ownerDid);

/**
return 
{
      authId: '0348xxxx-xxxx-4317-xxxx-8d6f6166a65b',
      appId: 'tesxxxx01',
      credentialContext: 'credential:sfp_passport_authentication',
      description: 'My Shuftipro Passport Authentication',
      txHash: '9494568336a4c2xxxxxxxxxxxxxxxxbaa066e1585fe47',
      status: 1,
      encryptOriginData: 'xxxxxxx', // credential 主要信息
      requestTime: 1622156645
    }
    
    status
    1 ---- 成功
    2 ---- 验证中
    0 ---- 验证失败
**/
```



#### `utils` 方法

##### `countryList`

```javascript
import { utils } from 'xxxx'

utils.countryList

/**
return array

[
  { name: 'Afghanistan', alias: 'AF' },
  { name: 'Aland Islands', alias: 'AX' },
  ...
]

name ----- country name
alias ---- abbreviation, 用户选择的 country value

**/

```



`generateId`

```javascript
import { utils } from 'xxxx'

/**
params
ETH Address
**/
const ownerDid = utils.generateId('0xaaaaaaaaaaaaa');

/**
return 
did string
**/
```



`base64Decode`

```javascript
import { utils } from 'xxxx'

/**
params
encryptOriginData of credential result
base64 hash string
**/
const result = utils.deserialize(string)


/**
return type

{
      '@context': [
        'https://www.w3.org/20xxxxxxxxxxxx',
        'https://ontid.ont.i20xxxxxxxxxxxx',
        'credential:sfp_passport_authentication'
      ],
      id: 'urn:uuid:861cbae4-xxxx-4844-xxxx-8c8xxxx7052',
      type: [ 'VerifiableCredential' ],
      issuer: 'did:ont:APc8FBxxxxxxxxxxxxxxSUFX2HAnBuBna',
      issuanceDate: '2021-05-28T07:04:23.000Z',
      expirationDate: '2022-05-28T07:04:23.000Z',
      credentialStatus: {
        id: '4f7f159ac4xxxxxxxxxxx5f61b7d0cc6',
        type: 'AttestContract'
      },
      credentialSubject: {
        Name: 'xxxxxxxx',
        BirthDay: 'xxxx-03-09',
        ExpirationDate: 'xxxx-03-12',
        IDDocNumber: 'xx26xxxx86',
        IssuerName: 'Shxxxxro',
        user_did: 'did:ont:5cxxxxxxxx701CbBExxxxx29b'
      },
      proof: {
        type: 'JWT',
        verificationMethod: 'did:ont:APcxxxxxxxxq2BSUFX2xxxxxna#keys-1',
        created: '2021-05-28T07:04:23Z',
        proofPurpose: 'assertionMethod',
        jws: 'ARyjxxxxxxxxxxxxxxxxxxGDisGMJdFE/4erXIazh3n8ipPotTFA+Z4hS09GlhVaio=\\'
      }
    }

**/
```

