---
title: PGP公钥
tags: []
categories: []
sticky: false
mermaid: false
date: 2025-10-05 23:56:25
cover:
comments:
copyright:
sponsor:
---


# PGP 公钥
## Q&A
### 这是什么？
PGP（Pretty Good Privacy）是一套用于讯息加密、验证的应用程序。  
[GPG](https://gnupg.org/)（GNU Privacy Guard）是一套开源的加密与签名工具。它可以让你在互联网上安全地传输信息，避免中间人篡改或窃听。

### 这有什么用？
- 你可以使用我的公钥来加密消息或文件，加密之后将只有我可以解密。
- 你可以使用我的公钥来验证我签名的信息确实是由我发出的，而没有经过任何篡改。
- 当通信双方互相拥有对方公钥之后，可以使用对方的公钥加密信息，并使用自己的私钥签名，实现端对端加密。

### 应该如何使用？
>1. 从[附录](https://blog.nhir.top/2025/10/05/GPG%E5%85%AC%E9%92%A5/#%E9%99%84%E5%BD%95)中获取我的私钥并导入
> ```bash 
> gpg --import public.asc
> ```
> 其中 public.asc 是一个二进制文本文件，里面写有我的完整公钥。或者使用公钥服务器导入
> ```bash
> gpg --keyserver hkps://keys.openpgp.org --search-keys nhirsama@outlook.com
> ```
> 2. 验证公钥[指纹](https://blog.nhir.top/2025/10/05/GPG%E5%85%AC%E9%92%A5/#%E6%8C%87%E7%BA%B9)
> ```bash
> gpg --fingerprint nhirsama@outlook.com
> ```
> 请务必对照导入的公钥指纹与附录中提供的指纹是否一致，以确保公钥未经篡改。
> 3. 加密信息
> ```bash
> echo "需要加密的信息" | gpg --encrypt --armor --recipient nhirsama@outlook.com
> ```
> 或直接加密文件
> ```bash
> gpg --encrypt --recipient nhirsama@outlook.com secret.txt
> ```
> 4. 验证签名
> ```bash
> gpg --verify file.sig file.txt
> ```
> 5. 使用在线加密
> 访问 [PGP Tool](https://pgpcn.github.io/pgp/simple.html)，选择加密，将[附录](https://blog.nhir.top/2025/10/05/GPG%E5%85%AC%E9%92%A5/#%E9%99%84%E5%BD%95)中的公钥复制至左侧“收信人的公开密钥”栏，在右侧“要发送的信息”栏填写要加密的信息，之后加密信息并将下方“加密后的 PGP 信息”栏**全部**复制并发送至我的[邮箱](mailto:nhirsama@outlook.com)。
> 注:哪怕网页完全在本地浏览器运行，也仍不建议使用使用此网站加密隐私数据。
### 我为何要这么做
在隐私泄漏愈发频繁的当下，我们必须使用零信任原则来保护我们的隐私安全。
很多通讯软件底层设计对用户透明，且没有公开其源代码。
我们无法确保数据在传输过程中被加密，即使加密传输我们也无法确保在哪一步被解密。  
当然，我们的很多聊天信息即使泄漏也不会造成什么危害，但是当我们要传递账号密码等关乎人身财产安全数据的时候，也要无条件信任那些企业吗？  
因此我们需要显式加密与解密信息，以此来保护我们的隐私安全。
## 附录
### 公钥
```asc
-----BEGIN PGP PUBLIC KEY BLOCK-----

mDMEaOCwHRYJKwYBBAHaRw8BAQdAMnQTvzoYCyJ4fXNO2hibYkN5oP5pcYbteqvR
9Gg4HVq0G2xpbmcgPG5oaXJzYW1hQG91dGxvb2suY29tPoiQBBMWCgA4FiEESphO
MjDKzhc1FsczQaagloo4zswFAmjgsB0CGwMFCwkIBwIGFQoJCAsCBBYCAwECHgEC
F4AACgkQQaagloo4zsw4nAEA1NhY41watg+tzaBwVsjH2qimEevjR8aquBCwUZE3
BdoA/1Po5iRnwG/v/j4CKufqBgICGLd86KvU6VAwcfnctF8MuDgEaOCwHRIKKwYB
BAGXVQEFAQEHQB6dvoOe8vBOAX1BbgYVuL7GP6psysur9Kntc8PQJiZwAwEIB4h4
BBgWCgAgFiEESphOMjDKzhc1FsczQaagloo4zswFAmjgsB0CGwwACgkQQaagloo4
zszhZgEAuW3ILDdsmV93jtvHZRzbnEDF+1qkiOFYtbRx8eqUtWcBAOP0du8/Tf8y
jskNsjmCN4+79AaVFHf72BWVh8fbpBkOuDMEaOkK0xYJKwYBBAHaRw8BAQdAV8CW
ohMexpuje76Y6iKwKPHyn68aeDhHwM9D4u7B31qI9QQYFgoAJhYhBEqYTjIwys4X
NRbHM0GmoJaKOM7MBQJo6QrTAhsCBQkJZgGAAIEJEEGmoJaKOM7MdiAEGRYKAB0W
IQQRwGo4vvZxEEkeupu98uJkGyYLKAUCaOkK0wAKCRC98uJkGyYLKN/yAQCJwyK/
SBszZa2Mcup2Vt01j9XXjYO0X0p73XCk1mVknwD+I/UORAaQLCNu+T6ZeEMwgF2V
kxUgmjGgPQ/IskKgTgj3rgD/X1oWhmOJ0AXr0hQi0Ny6aJOVnVutdrT7Gnu2mr6T
WosBAMBLTT33plKjGOOy6GQZWey2Rek+kg3OQvoGvUTHEfMP
=19V8
-----END PGP PUBLIC KEY BLOCK-----
```

### 指纹
```fingerprint
pub   ed25519 2025-10-04 [SC]
      4A98 4E32 30CA CE17 3516  C733 41A6 A096 8A38 CECC
uid             [ 绝对 ] ling <nhirsama@outlook.com>
sub   cv25519 2025-10-04 [E]
sub   ed25519 2025-10-10 [S] [有效至：2030-10-09]
```

### 公钥服务器
在 [公钥服务器](https://keys.openpgp.org) 搜索 [4A984E3230CACE173516C73341A6A0968A38CECC](https://keys.openpgp.org/search?q=4A984E3230CACE173516C73341A6A0968A38CECC)。
