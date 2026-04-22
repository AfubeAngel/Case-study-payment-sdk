# Payment Gateway SDK - Case Study

A fintech case study showcasing a shared payment SDK that unifies fragmented payment rails across five downstream products.

## What this case study covers

- The core problem: fragmented payment rails that needed a single integration layer across multiple product surfaces.
- The six payment methods supported: card payments with OTP/3DS, bank transfer with virtual account generation and polling, QR code checkout with real-time status updates, OPay wallet redirect flow, Google Pay Web API tokenized checkout, and Apple Pay JS session merchant validation.
- The SDK architecture: a clean transaction initialization API, a rail router that selects and validates payment methods, provider adapters for each payment channel, and a transaction state machine that drives order states.
- The ecosystem: five products consuming the same SDK, including merchant storefront, payment pages, merchant portal, admin back office, and a Next.js marketing website with an embedded pension payment flow. Addiitonally available for integration for payment collection.
- Outcomes: single source of truth for payments, consistent checkout UX, faster product shipping, and runtime merchant configuration without redeployment.
- Tech stack: TypeScript, Angular and integrations with payment provider APIs.

## Overview

The Payment Gateway SDK is the shared payment layer for a fintech platform. It is not a standalone checkout product; it is the embeddable payment engine used by multiple products with distinct domain needs.

## Challenge

The project solved a major engineering problem: every payment method came with its own integration contract, and five separate products were at risk of duplicating the same complex logic.

Key challenges included:

- Fragmented payment rails across providers
- Multi-product embedding across Angular apps and one Next.js site
- Merchant-specific runtime configuration for branding, fees, and available methods
- Regulatory and security requirements for OTP, PCI compliance, and provider tokens

## Solution

A single SDK was built to abstract provider-specific flows behind a unified API. Consuming applications initialize the SDK with transaction context, merchant config, and callback handlers. The SDK then:

- renders payment UI
- routes users to the correct payment rail
- handles polling, redirects, and callback events
- emits consistent success/failure/close events back to the host product

### Supported payment rails

1. **Card Payment** — full card entry with OTP challenge and 3DS support.
2. **Bank Transfer** — dynamic virtual account creation with confirmation polling.
3. **QR Code** — QR generation and real-time payment status listening.
4. **Pay with OPay** — wallet deep-link and redirect flow with callback handling.
5. **Google Pay** — Google Pay Web API integration with tokenized dispatch.
6. **Apple Pay** — Apple Pay JS session merchant validation and payment token handling.

## Architecture

The SDK is organized into clearly separated responsibilities:

- Transaction initialization entrypoint with merchant and transaction config
- Rail router for method selection, availability checks, and fee logic
- Provider adapters for card, transfer, OPay, Google Pay, and Apple Pay
- Shared transaction state machine
- Event callbacks

## Outcomes

- Single source of truth for payment logic across all products
- Consistent checkout experience across surfaces
- Faster product development because payments were already solved
- Merchant-configurable checkout behavior without rebuilds

## Tech stack

- TypeScript
- Angular
- Next.js (Pages Router)
- RxJS
- Google Pay Web API
- Apple Pay JS
- OPay SDK
- REST APIs
- Webhook and polling patterns
- Virtual account service and direct debit
- POS integration
