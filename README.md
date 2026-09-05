# Peppol BIS Billing 3.0 & EN 16931 E-Invoice Engine — TypeScript / JavaScript SDK

[![npm version](https://img.shields.io/npm/v/@stanzaapi/peppol-validator.svg)](https://www.npmjs.com/package/@stanzaapi/peppol-validator)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> Sub-5ms Peppol BIS Billing 3.0 & EN 16931 e-invoice validation and XML-to-JSON parsing supporting OASIS UBL 2.1 and UN/CEFACT CII.

Official, zero-dependency Node.js and TypeScript client for **Peppol BIS Billing 3.0 & EN 16931 E-Invoice Engine**, powered by the [Stanza Micro-API Network](https://stanzaapi.com). Delivers deterministic, sub-5ms V8 isolate execution directly to your application without 3rd-party proxies.

* 🌐 **Live Web Sandbox:** [Try interactive queries online](https://stanzaapi.com/tools/peppol-validator)
* 📚 **API Reference:** [Read complete OpenAPI specification](https://stanzaapi.com/tools/peppol-validator)
* ⚡ **Platform Overview:** [Discover the Stanza Edge Portfolio](https://stanzaapi.com)

---

## 📦 Installation

```bash
npm install @stanzaapi/peppol-validator
# or
pnpm add @stanzaapi/peppol-validator
# or
yarn add @stanzaapi/peppol-validator
```

---

## 🚀 Quickstart

```typescript
import { PeppolValidatorClient } from '@stanzaapi/peppol-validator';

// Initialize client (API key optional for sandbox tier evaluation)
const client = new PeppolValidatorClient({
  apiKey: process.env.STANZA_API_KEY,
});

async function main() {
  const result = await client.validate('<Invoice xmlns="urn:oasis:names:specification:ubl:schema:xsd:Invoice-2">...</Invoice>');

  if (result.success) {
    console.log('Verification Success:', result.data);
  } else {
    console.error('Validation Error:', result.error, result.code);
  }
}

main().catch(console.error);
```

---

## 📄 Example JSON Response

```json
{
  "success": true,
  "data": {
    "valid": true,
    "profile": "urn:fdc:peppol.eu:2017:poacc:billing:01:1.0",
    "invoice_number": "INV-2026-001"
  }
}
```

---

## ⚙️ Client Configuration Options

| Option | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `apiKey` | `string` | `process.env.STANZA_API_KEY` | Your [Stanza API Key](https://stanzaapi.com). Required for high-throughput production tiers. |
| `baseUrl` | `string` | `https://stanzaapi.com` | Edge API endpoint base URL. Configurable for private enterprise enclaves. |
| `timeoutMs` | `number` | `15000` | Request timeout in milliseconds (uses native `AbortSignal.timeout`). |


---

## 🛡️ Response Envelope & Error Handling

All responses return a typed envelope:

```typescript
export interface ApiResponse<T> {
  success: boolean;
  data?: T;
  error?: string;
  code?: 'VALIDATION_ERROR' | 'UNAUTHORIZED' | 'PAYLOAD_TOO_LARGE' | 'RATE_LIMITED' | 'INTERNAL_ERROR';
}
```

---

## 🔗 Related Resources

* [Peppol BIS Billing 3.0 & EN 16931 E-Invoice Engine Interactive Playground](https://stanzaapi.com/tools/peppol-validator)
* [Stanza Microservices Directory](https://stanzaapi.com)
* [Report an Issue on GitHub](https://github.com/stanzaapi/peppol-validator-typescript/issues)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).
