---
description: Getting started with setting up the redeem API to your app
---

# Getting Started

## First Steps

Hey there, lets get started with setting up our integration with Nuqtah's API

Firstly you need to subscribe to one of our plans OR simply claim this awesome NFT and get a 30 day free trial with no credit card information required!\


<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Choose a plan</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Claim your free trial token</p></figcaption></figure>

After you claim your free trial token ( or buy a plan), you will gain access to the console.&#x20;

The console will be your go-to interface to manage the tokens you issue for user and all your settings and information will be there, including your API keys that  you will use to integrate with Nuqtah's API.



<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Nuqtah's Console</p></figcaption></figure>



## Generate an API Key&#x20;

To be able to generate an API Key to use to integrate with Nuqtah's API, simply click on the API Key button in the bottom left of the drawer shown in the figure below.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Generate API Key</p></figcaption></figure>

Here you can generate your <mark style="color:red;">API Secret Key.</mark> You MUST keep this key a secert and add it to your .env secret variables in your application. <mark style="color:red;">**DO NOT SHARE THIS KEY WITH ANYONE**</mark>.&#x20;

<mark style="color:red;">**Please save this code in your BackEnd secret/env variables so it is not visible from developer tools in the browser.**</mark>



## Can I change my API Key?

Absolutely!&#x20;

For security reasons if you forget your API Key you wont be able to recover it but you can easily with a click of a button generate a new one from the dashboard here. Nuqtah's team decided for security purposes it wouldnt be a good idea to store or view the original form of the API Key, so you simply need to generate a new one if you happen to forget your own.

After obtaining this API key be sure to use it in your requests as instructed in the next sections of this documentation.



## Creating a Digital Gift-able Token

Now lets try to create a digital token and gift it to one of our users for a discount!

Navigate to the create new token page on the top left drawer:

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Create new token</p></figcaption></figure>

&#x20; Now when you are filling this form, make sure to select the redeemable checkbox and input the data as follows:\


<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Create redeemable token</p></figcaption></figure>

You can fiddle with the settings and customize it as you like, however some things to consider:

* Unlimited/Limited supply dictates how many copies of this NFT you can send/distribute among users
* Unlimited/limited redeems dictates how many times can a single copy be redeemed/used
* Be sure to choose online redeem and add your website's url in the redemption link field
* In the discount value, you can set it to whatever string you need it to be and catch it in the response and apply any logic you need on your website. So for example it could be discountValue: "Vanilla ice-cream discount" or mabye "20%".&#x20;
*
* However you wanna do it, this is up to how you wanna handle the checkout logic from your side when you get the nft



Great! now you successfully created an online redeemable nft template. Now you can start sending it your users that you wanna give discounts!



## Gifting a Digital Token to user(s)

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Gifting an nft to users</p></figcaption></figure>

Now you can send to single email, or upload a csv file for bulk sending to a bunch of emails.

When you use this feature, the NFT will get copied and minted on the blockchain and sent to this user via his email. So when the user signs in using this email to your website, you will be able to fetch his NFTs via Nuqtah's API and redeem it offering him discounts on your platform!

