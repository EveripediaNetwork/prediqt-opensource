# PredIQt White Paper:

_Prediction marketplaces built on EOS._

## Intro

PredIQt is a new, EOS-based prediction market protocol that is part of the IQ Network of dApps.

Prediction markets​ are platforms where users can ​trade​ ​the outcomes of events​. This allows for financially incentivized predictions, which ​tend to be more accurate​ than non-incentivized forecasts.

Prediction markets have the potential to be extremely effective information tools, but they have traditionally been limited as a result of their centralized architecture. Blockchain technology allows us, for the first time ever, to create prediction markets that don’t rely on centralized parties and thus avoid many of the problems that have plagued these markets in the past. This allows users to finally unleash the massive potential that prediction markets hold. As Ben Davidow points out in ​this article​, prediction markets have the power to predict the future, persuade and incentivize real world outcomes, and prepare for the future by building hedges against various types of events.

We believe that EOS is the first decentralized smart contract platform capable of hosting high-volume, high-throughput, user-facing dApps. We believe that a prediction market built on top of EOS can offer a seamless experience to the end user while also maintaining the decentralization needed to make a blockchain-based prediction market successful.

Below we offer a short overview of the design and architecture of PredIQt.

## Background

Prediction markets allow users to predict the outcomes of events by purchasing tradable shares in those outcomes. Traditionally, prediction markets have been operated by centralized entities; companies that ran the markets on their own servers and reported on the outcomes of the events being traded. However, this created many issues. Users were required to trust that the company would accurately report on events and pay out earnings to winning users, and the companies themselves often faced legal liabilities and draconian regulation, leading to restrictions and ​shutdowns​.

Structuring a prediction market as a ​decentralized protocol​ allows users to avoid many of those issues, as there is no entity that controls the market. The core code lives on the blockchain and is usable by anyone globally. Further, users’ funds are deposited into smart contracts, meaning that no company has the ability to take control of or steal those funds.
  
A number of prediction markets have already been built on blockchain technology, most prominently ​Augur​ and ​Gnosis​. While Augur has seen some measure of success since its launch, it suffers from serious issues around usability and performance. Ethereum, the platform upon which Augur is built, has low throughput, high latency, unpredictable fees, and other issues that negatively impact user experience. These issues have prevented Augur and other Ethereum dApps from reaching critical mass.

We believe that PredIQt is the first prediction market capable of solving the issues posed by both centralized prediction markets and previous blockchain-based iterations.

## Oracles and Market Resolutions

Blockchain-based prediction markets need to integrate information from the outside world in order to resolve markets. Most of the events being predicted take place off-chain (for example, the outcome of a presidential election), so there needs to be some way for that information to be recorded on the blockchain to trigger the payout of the smart contract. This is known as ​the oracle problem​, and it is the central challenge facing all decentralized prediction markets.

We recognize that there are many ways of designing and implementing oracles and that different types of oracles​ may be better for different types of markets. Augur, for example, allows market creators to specify a market resolver, but also allows for those resolutions to be challenged by users and eventually resolved by a fully distributed oracle maintained by an incentivized group of REP token holders. This is a highly fault-tolerant system, but it can take weeks to resolve contentious markets and may not be necessary or ideal in all cases.

Using the ​EOSIO account system​, the PredIQt protocol is able to offer maximum flexibility to market creators and users. Each market that is created must specify an EOS account that will act as the resolver. Because EOS accounts are highly configurable, this resolver could be a single individual, a multi-sig, a DAC, a smart contract, a ​LiquidApps​ DSP, or a secure data feed like ​Oraclize​. This allows market creators and users to choose the resolution models that make the most sense for each type of market. Market creators can experiment with different levels of trust and decentralization, and users can choose whether or not to participate in markets based on their confidence in the resolution system.

The goal of PredIQt is not to build a single resolution system that is used by all markets. Rather, the goal is to create a platform where anyone globally can create a resolution system, any of which can be easily plugged into any market on PredIQt. We believe that new decentralized business models will appear where distributed organizations specialize in resolving markets for users, earning resolver fees in the process. The organizations that offer the most reliable and trustless resolution services will be chosen by market creators for the most important markets, and the markets resolved by the most reputable sources will attract the most interest, participation, and liquidity. Because both market creators and market resolvers can profit from popular markets, this creates a positive feedback loop that drives proper incentives on both sides. For high-profile and high-stakes markets, market creators can even specify an oracle system that requires multiple independent resolvers to reach the same decision before a payout can be triggered.

Under the PredIQt system, market creators can choose to resolve markets using anything from a single resolver to a fully distributed system like that of Augur. We believe that this offers more customizability to users and better reflects the realities of prediction markets, where one resolution model may not be ideal for every different type of market.

At launch, most PredIQt markets will likely be resolved using multi-signature contracts or secure data feeds like Oraclize. As the market develops, we believe that we’ll see more sophisticated models like for-profit DACs that specialize in market resolution.

## How PredIQt Works

At its core, the PredIQt protocol is quite simple. Any user can create a market for any event, and then other users can purchase and trade shares in the outcomes. The EOS used to purchase the shares is stored in the market’s smart contract. Once the event happens, the outcome is reported by an account specified by the market creator, and the EOS stored in the smart contract is distributed to the winners. Users on the winning side can cash in their shares for a profit, paying a small fee that is split between the market creator and the market resolver. Shares on the losing side of the market become worth zero, since they can’t be redeemed for anything.

The PredIQt Market features three primary classes of users:

- Market creators

- Market resolvers

- Predictors

Market creators​, as the name suggests, are the users who create the markets. Market creators must pay a ​market creation fee​, denominated in ​IQ​. This fee serves as an anti-spam mechanism that prevents users from creating markets that are superfluous or unresolveable. The initial fee for market creation is set at 25,000 IQ (currently ~\$100). When a market creator pays the market creation fee, that IQ is burned.

Although market creators must pay a fee to create a market, they also stand to earn money in the case that the market becomes successful; users pay a small fee upon cashing out, part of which is paid to the market creator. If a creator’s market attracts significant open interest, then their payout upon resolution can be high. This incentivizes market creators to create high-quality markets that attract many users. Because the cost of creating a market is non-trivial and non-refundable, it incentivizes users to create high-quality markets with clearly defined outcomes that will attract users. Creators who publish low-quality or unresolvable markets will be unlikely to earn back their market creation fee.

Market resolvers ​are those who report the outcomes of various markets. When a market creator first creates a market, they must specify an EOS account that will report on the outcome. This account can be anything from an individual to a distributed group of token holders. Initially, all PredIQt markets will be binary. Resolvers can specify either side of the market as a winner, or they can declare the market invalid. If a market is declared invalid, then all of the shares are refunded equally.

Predictors ​are the main users of the prediction market— those who predict outcomes and buy and sell shares in those outcomes. Users can purchase outcome shares using EOS. When a new set of shares is created, the EOS used to purchase those shares is stored in the market’s smart contract. Once created, those shares become tradeable. When a market is resolved, the shares of users on the losing side go to zero. Users on the winning side earn the difference between the price paid for their shares and 1, since each share set adds up to 1. Users on the winning side are then able to trade in their shares for a pro-rata portion of the EOS held in the smart contract, minus a small fee that is split between the market creator and the market resolver.

## Unresolved and Invalid Markets

In certain cases, some markets may be unresolveable. This can happen due to circumstances that invalidate the original market, or because the market creator has not properly defined the market.

It is up to the resolvers of the market to determine whether or not the market is invalid. The first version of PredIQt will feature binary markets. Market resolvers can specify the outcome as one of the two binary outcomes, or as invalid. In the case that a market is declared invalid, all shares are refunded equally. Users should be careful to only participate in markets with a clearly defined outcome, and market creators should define their markets very specifically in order to attract significant interest.

In other cases, it’s possible that markets go entirely unresolved. All markets have an expiration date when the market ends. After the market expiration, there is a 15-day window in which the market resolver must specify the outcome. If the market resolver fails to do so in this time period, then the market automatically becomes invalid, and all shares are paid out equally.

## Fee Model

The PredIQt protocol uses a basic fee model designed to incentivize and compensate market creators, market resolvers, and IQ Network stakeholders.

Market creation fees​ are paid in IQ (the native token of the IQ Network) by market creators. The market creation fee is initially set at 20K IQ, or about \$100. All market creation fees are burned when the market is created. Market creation fees are initially set by a multi-sig managed by the Everipedia team, but will later be controlled by the IQ Network’s governance module.

Market creator fees​ and ​market resolver fees​ are paid by ​winning​ shareholders in the market when they cash out their shares for EOS upon market resolution. When a winning users cashes out, the smart contract automatically charges a fee of 0.5% that is split between the market creator and the market resolver equally. This fee will also be variable and will be controlled by the IQ Network governance module.

## Evolution and Roadmap

The PredIQt protocol will be built and released in stages, allowing users and developers to gradually take advantage of a more full suite of features. The initial release will offer basic functionality but will not be fully feature-complete. The goal of PredIQt upon launch is to offer a quality user experience while also allowing users maximum flexibility around resolution models.

Any EOS development team can build on top of the PredIQt protocol. The first interface for the protocol will be designed and released by the Everipedia team. Further details around the interface and the resolution model will be released soon!

One the PredIQt protocol is proven to be stable and safe, the development team will continue to release new features and functionality. Below is a list of features that will be integrated in later PredIQt protocol releases:

- Addition of non-binary markets

- Addition of markets denominated in stablecoins

- Introduction of fees paid to market resolvers but not market creators in the case of
  invalid markets

- Introduction of a market creator bond that is slashed for unresolved markets

- Introduction of the ability for market creators to set a backup resolver in the case that the
  designated resolver doesn’t show up by the end of the resolution window

- Addition of “invalid” as a purchase-able outcome for all markets, allowing users to place
  bets on whether a market will be deemed invalid

- Integration of the IQ governance module to govern the protocol and set key parameters
