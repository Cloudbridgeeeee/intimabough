# IntimaBough — proposed AWS architecture

IntimaBough uses AWS to read supplier documents, extract and normalise product facts, and keep a reviewed, traceable catalogue — privately for each organisation.

## Request flow

1. Supplier documents
2. Amazon S3
3. Textract
4. Bedrock
5. DynamoDB
6. Merchandiser review
7. Catalogue export

## Services

### Amazon Textract

**Role:** Read supplier documents

Extracts text, tables and key-value pairs from spec sheets, PDFs and images, so product facts can be captured from any supplier format.

### Amazon Bedrock

**Role:** Extract, normalise and draft

Maps supplier wording to your vocabulary, extracts attributes and drafts accessible descriptions — with guardrails that block explicit language and medical claims.

### Amazon S3

**Role:** Store source documents

Keeps supplier documents encrypted and versioned, so every attribute can be traced to the exact document it came from.

### Amazon DynamoDB

**Role:** Hold the product catalogue

Stores products, attributes, source references, completeness scores and review decisions for fast catalogue browsing and export.

### AWS Lambda

**Role:** Run enrichment and exports

Orchestrates extraction, enrichment and checks for each upload, and generates exports for retailers’ ecommerce platforms.

## Principles

- **Approved sources only** — We enrich from supplier-approved documentation, nothing else.
- **Guardrails on language** — Bedrock Guardrails keep drafts factual and non-explicit.
- **Private by default** — Catalogue data is isolated per organisation.

## Safeguards

- **Your team approves** — Every enriched product is reviewed before export.
- **No medical claims** — Health or therapeutic claims are flagged and excluded from drafts.
- **Facts from sources** — Attributes link to the supplier document they came from.
- **Discreet and private** — No shopper data is processed; catalogue data is encrypted and isolated.

## MVP scope

Choose a product range and its supplier documents. We extract, normalise and enrich the products to your schema, your team reviews them, and we deliver a clean export for your shop.

- Supplier document upload
- Attribute extraction with sources
- Terminology normalisation
- Completeness checks
- Reviewed CSV / platform export
