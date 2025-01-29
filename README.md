# AI-Powered Search Interface

A modern web application that provides a chat-like interface for interacting with various search indexes and models through Anserini's search API.

## Features

### Search Models
- **MS MARCO Collection**
  - Base Indexes (V1/V2)
  - Neural Encodings:
    - SPLADE++ CoCondenser-EnsembleDistil
    - cos-DPR Distil (HNSW & quantized INT8)
    - BGE-base-en-v1.5 (HNSW & quantized INT8)
    - Cohere embed-english-v3.0 (HNSW & quantized INT8)
- **BEIR Collections**
  - Multiple collections (TREC-COVID, BioASQ, etc.)
  - Index types: Flat, Multifield, SPLADE++, BGE
- **CACM Collection**
  - Classic IR test collection

### Chat Interface
- Conversational interaction with search results
- Real-time streaming responses
- Support for both search and chat models
- Message history and chat persistence
- Vote/feedback system for results

## Architecture

### Core Components
- Next.js 13+ with App Router
- TypeScript for type safety
- Vercel AI SDK for streaming
- Server-side API routes for search functionality

### Search Integration
- Direct integration with Anserini's Java backend
- Support for multiple index types:
  - Traditional Lucene indexes
  - Neural HNSW indexes
  - Quantized (INT8) indexes
  - Impact indexes (SPLADE++)

### Data Flow
1. User sends query through chat interface
2. Query is processed by appropriate model
3. For search models:
   - Query is sent to Anserini backend
   - Results are formatted and streamed back
4. For chat models:
   - Interaction is handled by chat API
   - Responses are streamed in real-time

## Setup

1. Install dependencies:
```bash
npm install
```

2. Configure environment variables:
```bash
cp .env.example .env.local
```

3. Start the development server:
```bash
npm run dev
```

## Configuration

### Anserini Server
The application expects an Anserini server running at the configured host/port with the following settings:
```json
{
  "host": "localhost",
  "port": 8081,
  "apiVersion": "v1.0"
}
```

### Available Models
Models are configured in `lib/ai/models.ts` and include two types, search and chat:
- Chat models for query assistance
- Search with prebuilt indexes

## API Integration

See `API_INTEGRATION.md` for detailed information about integrating with the Anserini backend and available endpoints.

## Development

The application uses a modern React stack with:
- Next.js App Router for routing
- Server Components for improved performance
- Streaming for real-time updates
- TypeScript for type safety
