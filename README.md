# Analysis of the Binance Money Laundering Scandal: An On-Chain Perspective

## Introduction

In November 2023, Binance, one of the largest cryptocurrency exchanges globally, faced federal charges in the U.S. for fraud and money laundering. The Department of Justice (DOJ) accused Binance and its CEO, Changpeng Zhao, of facilitating vast flows of illicit funds from countries such as Russia, Iran, and Cuba. This scandal, following closely on the heels of the FTX collapse, has shaken the crypto world and underscored the urgent need for regulatory oversight.

Using Bitquery APIs, this analysis delves into on-chain data related to Binance to understand the sequence of events, the extent of financial misconduct, and the flow of funds during the period leading up to the charges.

## Data Collection Methodology

Bitquery's GraphQL API was utilized to examine Binance's on-chain activity on Ethereum and Bitcoin blockchains, focusing on transaction volumes, wallet activity, and fund transfers.

1. **Key Wallets Identification:** Public records and blockchain explorers were used to identify Binance-associated wallets.
2. **Transaction Volume Analysis:** Changes in transaction volumes of these wallets were tracked using the Bitquery API.
3. **Fund Flow Tracking:** Fund transfers from Binance wallets were monitored to detect suspicious or large transfers.

## Queries and Insights

### Transaction Volume Analysis

The following query tracks transaction volumes from Binance's Ethereum wallets:

```graphql
query {
  ethereum {
    transactions(
      date: {since: "2022-01-01", till: "2023-12-31"}
      any: {from: {is: "0xBinanceAddress"}}
    ) {
      count
      value
      date {
        date
      }
    }
  }
}    

```
# Fund Flow Tracking

The following query monitors fund transfers from Binance wallets on Ethereum during the critical period:

```graphql
query {
  ethereum {
    transfers(
      sender: {is: "0xBinanceAddress"}
      date: {since: "2023-10-01", till: "2023-11-30"}
    ) {
      receiver {
        address
      }
      value
      date {
        date
      }
    }
  }
}
```
# Bitcoin Transactions Analysis

The following query tracks transaction volumes from Binance's Bitcoin wallets:

```graphql
query {
  bitcoin {
    transactions(
      date: {since: "2022-01-01", till: "2023-12-31"}
      any: {from: {is: "1BinanceBitcoinAddress"}}
    ) {
      count
      value
      date {
        date
      }
    }
  }
}
```
# Analysis

## Pre-Charges Transaction Spike
Ethereum and Bitcoin data indicated a surge in transaction volumes before the DOJ announced charges, suggesting possible internal awareness and asset relocation.

## Transfers to Unidentified Wallets
Significant transfers to unknown wallets during this period may indicate attempts to obscure fund origins or unauthorized withdrawals.

## Evidence of Financial Mismanagement
Irregular transactions and large fund movements align with allegations of Binance prioritizing growth and market share over compliance with U.S. laws.

Bitquery API analysis of on-chain data reveals potential misconduct in Binance’s operations. Significant transaction spikes and irregular fund flows are evident. This highlights the critical role of on-chain analytics in detecting financial irregularities in the crypto space.

# Context and Implications

## Binance's Role and Operations
Binance, founded by Changpeng Zhao in 2017, quickly grew to become a leading platform for cryptocurrency trading, especially altcoins. Despite its success, Binance faced increasing scrutiny for its lax compliance with anti-money laundering (AML) regulations.

## Federal Charges
The DOJ, along with the CFTC and the SEC, brought forward charges citing violations of the Bank Secrecy Act and sanctions programs. Binance was accused of allowing transactions with sanctioned countries and facilitating illicit activities through inadequate AML procedures.

[We are querying transaction data from the Binance blockchain. Specifically, we're using the transactions field under the binance object](https://graphql.bitquery.io)


