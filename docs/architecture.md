# Architecture
***

While we prefer in-code and live documentation over wiki pages, these are best suited to single services and we don't have a place to document broader processes that involve the interaction of several services. This section aims to provide that overview of how various services fit together.

## Supporter data flow

```mermaid
graph LR
  fundrasing-signups["Fundraising Sign-ups (Tom)"] --- event
  giftaid["Giftaid (Corin)"] --- event
  prize-platform["Prize Platform (William)"] --- event
  sms[SMS] --- event
  psl["Payment Service Layer (Labib)"] --- event
  justgiving[JustGiving] --- event
  mobilise[Mobilise] --- event
  marketing-prefs["Marketing Preferences (Adam)"] --- event
  esu["ESU (Adam)"] --- event
  rtbf[Right to be Forgotten] --- event
  shop["Shop (Seb)"] --- event

  event(Supporter event) --> producer

  subgraph supporter-event-service
    producer[Producer] -. SQS .-> consumer[Consumer]
    consumer --> action[Action]
  end

  action -- 1 --> user-service[User Service]
  action -- 2 --> erp-service[ERP Service]

  classDef green fill:#8fd04e,stroke:#70a63b,stroke-width:2px;
  class fundrasing-signups,prize-platform green
```
