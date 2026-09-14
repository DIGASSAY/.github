# DIGASSAY

**Digital infrastructure for physical commodity trading — contracts, quality, logistics and settlement, built for the way these deals actually happen.**

## Origin

DIGASSAY grows out of two decades of hands-on involvement in physical commodity trading operations — oil, coal, LNG and metal concentrates. That experience surfaced the same gap again and again: the tooling available to run a physical trade rarely matches how the trade is actually executed. Contracts live as scanned PDFs. Quality schedules with dozens of chargeable and penalty terms get re-typed into spreadsheets by hand. Assay disputes are resolved over email threads with no durable record. Logistics plans exist only in the heads of the people who booked the vessel.

DIGASSAY is an attempt to close that gap — starting from the real structure of a physical trade (a genuine, publicly-filed concentrate sale agreement was used to design the core data model) rather than from a generic "ERP for commodities" template.

## The Ecosystem

DIGASSAY is designed as three layers. The first is live today; the other two are roadmap.

```mermaid
flowchart TB
    User(["Trading Desk / Operations Team"])

    subgraph PD["Pre-Digital — live today"]
        direction TB
        REG["Counterparty Registry\n(UK / FR / NO / GLEIF lookups)"]
        CON["Supply Contracts"]
        QUA["Quality Specification\n(chargeables, penalties, versioning)"]
        LOG["Delivery Diary & Logistics\n(route estimate, road/rail/sea legs)"]
        ASY["Assay Exchange\n(Seller/Buyer/Umpire assay, splitting limit)"]
        REG --> CON --> QUA
        CON --> LOG --> ASY
    end

    subgraph KB["Knowledge Base — roadmap"]
        direction TB
        DOC["Contract & Regulatory\nDocument Store"]
        RAG["Ask-the-Contract\n(retrieval-augmented Q&A)"]
        DOC --> RAG
    end

    subgraph PR["Predictive — roadmap"]
        direction TB
        HIST["Historical Delivery &\nDispute Data"]
        MODEL["Delay / Dispute / Exposure\nForecasting"]
        HIST --> MODEL
    end

    User --> PD
    PD -- "structured contract & delivery data" --> KB
    PD -- "structured contract & delivery data" --> PR
    KB -. "informs" .-> PR
```

**Pre-Digital** is the foundation: turning the physical trade lifecycle — counterparty due diligence, contract terms, quality specification, transport planning, delivery tracking, assay dispute resolution — into structured, queryable data instead of documents and spreadsheets. This is the layer digitising what has historically been a pre-digital, paper-and-email process.

**Knowledge Base** (not yet built) will sit on top of that structured data and the underlying contract documents themselves, letting a trader or ops analyst ask a question in plain language and get an answer grounded in the actual contract text and terms — not a generic search.

**Predictive** (not yet built) will use the growing body of real delivery and dispute history to anticipate problems before they happen: which deliveries are trending toward a late discharge, which counterparties or routes carry elevated dispute risk, where quality exposure is building up across an open book.

## Status

Everything under **Pre-Digital** is live and working end to end, built against real reference data (USGS mine registry, UN/LOCODE ports and rail terminals, GLEIF/company registries, a genuine SEC-filed concentrate sale agreement) rather than invented placeholders. It is a demonstration platform, not a production trading system — see the disclaimer on the live site.

A working demo is available at **[digassay.nrgpix.com](https://digassay.nrgpix.com)**.
