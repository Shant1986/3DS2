# 3DS2 Introduction

>The New Authentication Protocol in the Payment Industry

## 1: What is 3DS2?

- [EMVCo](https://www.emvco.com/emv-technologies/3d-secure/) is the global technical body that facilitates the worldwide interoperability and acceptance of secure payment transactions by managing and evolving the **EMV® Specifications** and related testing processes
- EMVCo made up of six major card networks (*namely American Express, Discover, JCB, Mastercard, UnionPay, and Visa*) has recently released a new version of 3D Secure. Each brand adopts the current 3D secure protocol into their services and has branded this service differently for e.g. Visa is Verified by Visa, Mastercard is Mastercard SecureCode, American Express is SafeKey, etc.
- 3D Secure 2 (*EMV 3-D Secure, 3D Secure 2.0 or 3DS2 or 3DS2.0*) aims to address many of the shortcomings of 3D Secure 1 (3DS1) by introducing less disruptive authentication and a better user experience
- It has been implemented across EU region on 14th of September 2019

### 1.2 Vulnerabilities in 3DS1

- **Redirection:** In a 3DS 1 flow, the customer is redirected to an authentication page on their bank’s website, where they are prompted to enter a password associated with the card or a verification code sent to their phone
- **Payment Dropouts:** While it is a solid authentication step, this redirect flow is tedious (*it's not supported natively in app and in web flows*) and is confusing to customers. As a result, legitimate customers drop out of the payment flow thereby impacting the acceptance rates and bottom lines

### 1.3 The need for 3DS2
On 23 February 2017, EBA in cooperation with the European Central Bank (ECB) published a Draft [Regulatory Technical Standards](https://eba.europa.eu/documents/10180/1761863/Final+draft+RTS+on+SCA+and+CSC+under+PSD2+%28EBA-RTS-2017-02%29.pdf) (RTS) on **Strong Customer Authentication** (SCA) and common & secure communication under [Article 98](http://www.privacy-regulation.eu/en/article-98-review-of-other-union-legal-acts-on-data-protection-GDPR.htm) of [Directive 2015/2366](https://eur-lex.europa.eu/eli/dir/2015/2366/oj) (*Payment Service Directive* **PSD2**) (EU GDPR) which specifies:

1. The requirements of Strong Customer Authentication (SCA) (*especially for the verification of customer’s identity **in the card not present transactions***)
2. The **exemptions** from the application of SCA
3. The requirements with which security measures have to comply to protect the confidentiality and integrity of the users’ personalised security credentials
4. The requirements for common and secure open standards of communication (CSC) between account servicing payment service providers (ASPSPs), payment initiation service providers (PISPs), account information service providers (AISPs), payers, payees and other payment service providers (PSPs)

## 2: Strong Customer Authentication (SCA)

<div style="width: 400px; height: 200px; margin: 10px; position: relative;"><iframe allowfullscreen frameborder="0" style="width:400px; height:200px" src="https://www.lucidchart.com/documents/embeddedchart/01fc702d-edf2-4028-8ec9-5579ecdd074f" id="9EcxWS-ld~cA"></iframe></div>

[Diagram Source](https://www.lucidchart.com/documents/embeddedchart/01fc702d-edf2-4028-8ec9-5579ecdd074f)

### 2.1 Explanation of SCA

SCA is an "authentication based on the use of **two or more elements** known as `Knowledge` (*something only the user knows*), `Possession` (*something only the user possesses*) and `Inherence` (*something the user is*) that are independent, and it is to protect the confidentiality of the authentication data". The diagram above shows that the transaction must verify at least two (or more) elements to be a successful authentication as described in [EBA Guidelines](https://eba.europa.eu/sites/default/documents/files/documents/10180/2622242/4bf4e536-69a5-44a5-a685-de42e292ef78/EBA%20Opinion%20on%20SCA%20elements%20under%20PSD2%20.pdf). The list of each of the elements are:

### 2.2 Exemptions to SCA
SCA must also be applied to all electronic payments, unless one of the exemptions applies:

1. There are circumstances in which we want to exempt a customer from an SCA flow. For example, a merchant-initiated transaction (MIT) with a user's stored card credentials (*in this case the SCA flow has already been completed as part of the consent transaction*)
2. Other examples include transactions identified as low-risk or transactions with a low value. This helps in increasing the chances that the transaction will proceed frictionless (*that is, without an additional authentication step*) and thus decreasing the user dropouts
3. To exempt a user from an SCA flow, we also need to indicate our intention to do so in the `Create Authorization` or `Create Charge` request. It is the card issuer who decide whether to grant the exemption and if granted, the chargeback liability shifts back to the merchant

## 3: 3DS2 Frictionless Authentication
3DS2 allows businesses and their payment provider to send more data elements on each transaction to the cardholder’s bank. This includes payment-specific data like the shipping address, as well as contextual data, such as the customer’s device ID or previous transaction history.

<div style="width: 400px; height: 200px; margin: 10px; position: relative;"><iframe allowfullscreen frameborder="0" style="width:400px; height:200px" src="https://www.lucidchart.com/documents/embeddedchart/002adeab-8afb-488f-b5da-ec931d05c1b0" id="LCcxcZK3Va-a"></iframe></div>

[Diagram Source](https://www.lucidchart.com/documents/embeddedchart/002adeab-8afb-488f-b5da-ec931d05c1b0)

#### 3.1 3DS2 Risk Assessment
The cardholder’s bank can use this information to assess the risk level of the transaction and select an appropriate response:

- If the data is enough for the bank to trust that the real cardholder is making the purchase, the transaction goes through the *“frictionless”* flow and the authentication is completed without any additional input from the cardholder
- If the bank decides it needs further proof, the transaction is sent through the *“challenge”* flow and the customer is asked to provide additional input to authenticate the payment

## 4: Benefits of 3DS2
One of the solutions for providing SCA, is 3DS2. As the successor to 3DS1, it has been designed to provide for a more secure and user-friendly Authentication experience. With 3DS2, data (**such as device information**) transmitted in the background is mostly enough to authenticate without an extra step for the customer. It’s only when the provided information does not suffice to determine the risk-level of the transaction that an extra authentication step may be required.

1. It helps comply with new SCA mandates which has two-factor authentication as a requirement for all electronic payments
2. Protects the operations with robust security, and has the potential to fight cases of fraud
3. Provides a great customer experience. Frictionless customer identification has the potential to contribute to a shortened check-out process and to reduce cart abandonment
4. Increases authorization rates as authentication is quick and can take place on the same page
5. Allows to easily build authentication flows natively into Apps or websites
6. Helps to **shift liability** away from the merchant (the issuing bank assumes the risk)
