# Architecture
***

While we prefer in-code and live documentation over wiki pages, these are best suited to single services and we don't have a place to document broader processes that involve the interaction of several services. This section aims to provide that overview of how various services fit together.

## Supporter data flow

```mermaid
graph LR
  fundraiser-signups["Fundraiser Signups (Tom)"] --- event
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
  class fundraiser-signups,prize-platform green

  click fundraiser-signups "https://github.com/comicrelief/serverless-contact-store" "Click to go to Contact Store repo"
  click giftaid "https://github.com/comicrelief/serverless-giftaid" "Click to go to Giftaid repo"
  click prize-platform "https://github.com/comicrelief/serverless-prize-platform" "Click to go to Prize Platform repo"
  click psl "https://github.com/comicrelief/serverless-payments" "Click to go to Payments repo"
  click marketing-prefs "https://github.com/comicrelief/serverless-marketing-preferences" "Click to go to Marketing Preferences repo"

  click event "https://github.com/comicrelief/supporter-event-service" "Click to go to Supporter Events Service repo"
  click producer "https://github.com/comicrelief/supporter-event-service" "Click to go to Supporter Events Service repo"
  click consumer "https://github.com/comicrelief/supporter-event-service" "Click to go to Supporter Events Service repo"
  click action "https://github.com/comicrelief/supporter-event-service" "Click to go to Supporter Events Service repo"

  click user-service "https://github.com/comicrelief/serverless-user-service" "Click to go to User Service repo"
  click erp-service "https://github.com/comicrelief/serverless-erp-service" "Click to go to ERP Service repo"
```
