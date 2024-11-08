# 🔐 多签钱包 概述

---

**语言**：[English](./README.md) | [中文](./README_zh.md)  

---
## 🌐 多重签名技术起源
多重签名技术源于密码学中的“门限签名”（Threshold Signatures），这一概念早在区块链出现之前就已被提出。门限签名允许多个密钥共同参与签名过程，只有达到一定的密钥数量（即门限值），签名才能被验证通过。这一技术最早在银行和金融机构中被用于批准高风险交易或保护重要资产。

*比特币中的应用* - 随着比特币和区块链技术的出现，多签技术被引入到区块链钱包中，用于增强资金管理的安全性。比特币是最早实现多签功能的区块链项目之一。在比特币区块链中，可以通过“n-of-m”的多重签名方案来管理一个钱包。比如，3-of-5的多签方案意味着需要5个密钥中的3个才能发起交易。比特币协议在其脚本中支持OP_CHECKMULTISIG操作码，允许实现这种多签机制。

## 🔐 多重签名步骤
1. 设定定义签名人列表和门限值(n-of-m): 智能合约中存储一个数组来保存授权的签名人地址，并定义一个门限值变量。
2. 交易提案和批准流程：多签钱包的交互者首先在智能合约中提出交易提案，其他签名人可以通过调用特定函数对该提案进行签名。每次签名人的签名都会记录在链上。
3. 检查签名数量：当交易的签名数量达到门限值时，智能合约会自动执行交易，发送资金或调用其他合约。

## 🔑 关键函数
1. 提案提交函数：用户可以通过此函数向合约提交交易提案，并附带交易的目标地址、金额和其他参数。
2. 批准函数：签名人可以调用该函数批准交易提案，合约会记录下签名人的同意。
3. 执行函数：当提案获得足够的签名后，合约通过执行函数来完成交易或操作。
4. 状态查询函数：为了方便用户查看交易状态，合约中一般也包含查询函数，用于显示提案的当前签名数量、剩余的待签名数量等信息。

## 🚨 安全性与防护措施
1. 重放保护：每个交易提案带有唯一的ID或Nonce，以防止交易的重复提交或签名的重放。
2. 权限控制：只有合约定义的签名人才能对交易提案进行批准，防止非授权用户的恶意操作。
3. 时间锁：一些多签钱包加入了时间锁，规定交易提案需经过一段时间的“冷静期”才能执行，以防止紧急情况下的错误或恶意操作。

## 🚫 局限性
1. 交易费用：每次签名和提案的操作都需要消耗Gas费，随着签名数量的增加，费用也会同步显著上升。
2. 复杂度：多签逻辑较为复杂，稍有不慎可能导致漏洞风险。

## 📝 应用
1. 比特币的多签方案
2. EVM生态的Gnosis Safe合约钱包，广泛用于DAO和DeFi项目。
3. Cosmos、Polkadot等链上也实现了多签功能，用于社区资金管理和项目治理。

---

## 📚 引用

### 开源代码
- **Gnosis多签钱包** - [Gnosis_0.4.x版本(Solidity)](https://github.com/gnosis/MultiSigWallet)
- **Gnosis_Safe合约** - [Gnosis_新版](https://github.com/safe-global/safe-contracts)**

### 相关资料