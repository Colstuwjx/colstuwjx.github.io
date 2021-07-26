---
title: "[ 翻译 ] 去中心化组织"
date: 2021-06-14T10:00:00+08:00
tags: ["ethereum", "dao", "translate"]
categories: ["dao"]
comments: false
showMeta: false
showAction: false
aliases:
    - /translate-ethereum-dao-doc/
---

【编者按】以太坊官方于近期在他们的官方文档里上传了一篇介绍 dao（ decentralized autonomous organization ）的文章，本文翻译自[该篇文章](https://ethereum.org/en/dao/)。

<!--more-->

## 什么是 DAO ? {#what-are-daos}

DAO 是同全球志同道合的人一起工作的一种有效且安全的方式。

我们不妨把它们想象成是一个由其成员集体所有和管理的互联网原生企业。它们有自己的库房，未经集团批准，任何人都无权访问。各项决策通过提案和投票决定，以确保组织里的每个人都有发言权。

在这里，没有想一出是一出随意支配财政支出的 CEO ，也不会给狡猾的 CFO 操纵账本的机会。一切都是公开的，财政支出的相关规则会通过代码融入到 DAO 里。

## 为什么我们需要 DAO ? {#why-dao}

和某些人创办一个组织时，一旦涉及到资金和钱，就需要大家同他们一起工作的人之间拥有足够的信任。但是要想信任一个只在网上互动过的人其实很困难。借助 DAO，你无需信任集团里的其他任何人，只需要相信 DAO 的代码，它是 100% 透明的，而且任何人都可以验证它的可靠性。

这就为全球范围内的合作和协同开辟了诸多新的机会。

### 做个对比 {#dao-comparison}

| DAO                                                                                                                     | 一个传统组织                                                                       |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| 通常是扁平的，并且是充分民主的。                                                                   | 通常是层次分明的。                                                                          |
| 想要实施任何修改均需集团成员投票决定。                                     |  视具体组织架构而定，有时候可以是单方面要求的，也可以是投票决定的。    |
| 会自动统计票数，无需可信中介即可自动执行结果。         |  如果允许投票，票数会在内部统计，投票结果必须手动处理。 |
| 提供的服务以去中心化的方式自动处理（例如慈善基金的分配）。 |  需要人为介入，或者集中式控制的自动化处理，容易被操纵。         |
| 所有活动都是透明并且完全公开的。              | 活动一般是私人的，公众访问是受限的。             |

### DAO 案例 {#dao-examples}

为了帮助理解，这里提供了一些关于如何使用 DAO 的示例：

- 慈善机构 - 你可以接纳全球任何人的 DAO 成员资格及捐款，集团会决定如何使用这些捐款。

- 自由职业网络 - 你可以创建一个外包网络，将他们的资金集中用于办公空间和软件订阅。

- 风险投资和赠款 - 你可以创建一个风险基金，汇集投资资本然后通过投票的方式来决定风险投资。偿还的钱随后可以在 DAO 成员之间重新分配。

## DAO 成员 {#dao-membership}

针对 DAO 成员资格，这里有几种不同的模型。成员资格可以决定投票的运作方式以及 DAO 的其他关键部分。

### 基于 token 的成员 {#token-based-membership}

一般来说这完全无需授权许可，具体取决于它所使用的 token。在大多数情况下，这些治理代币可以无需授权许可便在去中心化交易所上进行交易。其他人则必须通过提供流动性或其他“工作证明”来赚取代币。无论哪种方式，只需持有 token 即可获得投票权。

_通常用于管理广泛的去中心化协议以及/或代币本身。_

#### 一个著名案例 {#token-example}

基于共享的 DAO 获得更多许可，但仍然非常开放。 任何潜在成员都可以提交加入 DAO 的提案，通常以代币或工作的形式提供某种价值的贡品。 股份代表直接投票权和所有权。 成员可以随时以其在国库中的比例份额退出。

[MakerDAO](https://makerdao.com) – MakerDAO's token MKR is widely available on decentralized exchanges. So anyone can buy into having voting power on the Maker protocol's future.

### 股份制的成员 {#share-based-membership}

基于共享的 DAO 获得更多许可，但仍然非常开放。 任何潜在成员都可以提交加入 DAO 的提案，通常以代币或工作的形式提供某种价值的贡品。 股份代表直接投票权和所有权。 成员可以随时以其在国库中的比例份额退出。

Share-based DAOs are more permissioned, but still quite open. Any prospective members can submit a proposal to join the DAO, usually offering tribute of some value in the form of tokens or work. Shares represent direct voting power and ownership. Members can exit at anytime with their proportionate share of the treasury.

_Typically used for more closer-knit, human-centric organizations like charities, worker collectives, and investment clubs. Can also govern protocols and tokens as well._

#### A famous example {#share-example}

[MolochDAO](http://molochdao.com/) – MolochDAO 专注于资助以太坊项目。 他们需要一份成员资格提案，以便小组可以评估您是否拥有必要的专业知识和资金来对潜在的受助人做出明智的判断。 你不能只在公开市场上购买 DAO 的访问权。

[MolochDAO](http://molochdao.com/) – MolochDAO is focused on funding Ethereum projects. They require a proposal for membership so the group can assess whether you have the necessary expertise and capital to make informed judgments about potential grantees. You can't just buy access to the DAO on the open market.

## DAO 是如何工作的 ? {#how-daos-work}

DAO 的支柱是它的智能合约。 合同定义了组织的规则并持有集团的金库。 一旦合约在以太坊上生效，除非通过投票，没有人可以改变规则。 如果有人试图做一些代码中的规则和逻辑没有涵盖的事情，它就会失败。 并且因为国库也是由智能合约定义的，这意味着未经该组织的批准，任何人都不能花钱。 这意味着 DAO 不需要中央权威。 相反，该小组集体做出决定，并在投票通过时自动授权付款。

The backbone of a DAO is its smart contract. The contract defines the rules of the organisation and holds the group's treasury. Once the contract is live on Ethereum, no one can change the rules except by a vote. If anyone tries to do something that's not covered by the rules and logic in the code, it will fail. And because the treasury is defined by the smart contract too that means no one can spend the money without the group's approval either. This means that DAOs don't need a central authority. Instead the group makes decisions collectively and payments are authorised automatically when votes pass.

This is possible because smart contracts are tamper-proof once they go live on Ethereum. You can't just edit the code (the DAOs rules) without people noticing because everything is public.

<DocLink to="/developers/docs/smart-contracts/" title="More on smart contracts" />

## Ethereum and DAOs {#ethereum-and-daos}

出于多种原因，以太坊是 DAO 的完美基础：

- 以太坊自己的共识是分布式和建立的，足以让组织信任网络。
- 智能合约代码一旦生效就无法修改，即使是其所有者也是如此。 这允许 DAO 按照其编程的规则运行。
- 智能合约可以发送/接收资金。 如果没有这个，您将需要一个值得信赖的中介来管理团体资金。
- 事实证明，以太坊社区的协作性强于竞争性，允许最佳实践和支持系统迅速出现。

Ethereum is the perfect foundation for DAOs for a number of reasons:

- Ethereum’s own consensus is distributed and established enough for organizations to trust the network.
- Smart contract code can’t be modified once live, even by its owners. This allows the DAO to run by the rules it was programmed with.
- Smart contracts can send/receive funds. Without this you'd need a trusted intermediary to manage group funds.
- The Ethereum community has proven to be more collaborative than competitive, allowing for best practices and support systems to emerge quickly.

## Join / start a DAO {#join-start-a-dao}

### Join a DAO {#join-a-dao}

- [Ethereum community DAOs](/community/#decentralized-autonomous-organizations-daos/community/#decentralized-autonomous-organizations-daos)
- [DAOHaus's list of DAOs](https://app.daohaus.club/explore)

### Start a DAO {#start-a-dao}

- [Summon a DAO with DAOHaus](https://app.daohaus.club/summon)
- [Create an Aragon-powered DAO](https://aragon.org/product)
- [Start a colony](https://colony.io/)
- [Build a DAO with DAOstack](https://daostack.io/)

## Further reading {#further-reading}

- [What's a DAO?](https://aragon.org/dao) – [Aragon](https://aragon.org/)
- [House of DAOs](https://wiki.metagame.wtf/docs/great-houses/house-of-daos) – [Metagame](https://wiki.metagame.wtf/)
- [What is a DAO and what is it for?](https://daohaus.substack.com/p/-what-is-a-dao-and-what-is-it-for) – [DAOhaus](https://daohaus.club/)
- [How to Start a DAO-Powered Digital Community](https://daohaus.substack.com/p/four-and-a-half-steps-to-start-a) – [DAOhaus](https://daohaus.club/)
