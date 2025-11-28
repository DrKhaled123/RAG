## Professional RAG System Implementation Plan: Medical & Academic Frontends with Backend Infrastructure

### Executive Summary

This comprehensive guide provides production-ready architecture for building dual-domain RAG systems (medical + academic) with optimal performance, stability, and accuracy. The system leverages **Ollama + Phi-3-mini + Redis + Qdrant** containerized backend with **Next.js/SvelteKit** frontends, deployed via **Coolify/Dokploy** using MCP/CLI protocols.[1][2]

### PDF Text Extraction Tools

#### Arabic Text Extraction

**PyMuPDF (fitz)** - Recommended Primary Tool:[3][4][5]
- **Performance**: Fastest PDF parser, outperforms PyPDF2 by 4-5x
- **Arabic Support**: Excellent bidirectional text handling
- **Table Detection**: Built-in `find_tables()` method
- **Usage**:
```python
import fitz
doc = fitz.open("arabic_medical.pdf")
for page in doc:
    text = page.get_text("text")  # Preserves Arabic RTL
    tables = page.find_tables()
```

**Unstructured.io** - Advanced Structured Extraction:[6][3]
- **Multi-format**: Handles PDFs, DOCX, PPTX
- **Arabic Capability**: Works with Arabic through layout detection
- **Metadata Preservation**: Extracts headers, footers, page numbers
- **Installation**: `pip install unstructured[all-docs]`

**MinerU** - High-Precision Alternative:[6]
- **Open-source**: Free, high-accuracy extraction
- **Mathematical Content**: Excellent for scientific documents
- **Multi-page Processing**: Handles long documents seamlessly

**Arabic-Specific Preprocessing**:
```python
import arabic_reshaper
from bidi.algorithm import get_display

def process_arabic_text(text):
    # Only use when displaying, NOT for storage
    reshaped = arabic_reshaper.reshape(text)
    return get_display(reshaped)
```

**Critical Note**: Never use `arabic_reshaper` when storing to database - it scrambles text. Use only for display purposes.[7][8]

#### English Text Extraction

**PyMuPDF** - Primary Choice:[9][3]
- **Speed**: 10-15x faster than alternatives
- **Accuracy**: 95%+ text extraction accuracy
- **Code Example**:
```python
doc = fitz.open("english_academic.pdf")
full_text = ""
for page in doc:
    full_text += page.get_text()
```

**Nougat** - Academic Document Specialist:[10][11]
- **Use Case**: Academic papers with complex layouts
- **LaTeX Output**: Converts to markup language
- **Limitation**: Struggles with PubMed tables[11]
- **Installation**: `pip install nougat-ocr`

**olmOCR** - Modern VLM-Based Parser:[12]
- **Technology**: Fine-tuned 7B VLM on 260K pages
- **Preservation**: Maintains sections, tables, equations
- **Output**: Clean linearized text in natural reading order
- **Open-source**: Available on GitHub

### Scientific Content Extraction (Equations, Diagrams, Chemical Formulas)

#### Mathematical Equations

**Mathpix** - Commercial Gold Standard:[13][14][15]
- **Accuracy**: PhD-level math, physics, statistics
- **Output**: LaTeX, DOCX, Markdown, Overleaf
- **Pricing**: Paid service with free tier
- **API**: `pip install mathpix`
- **Use Case**: Critical for engineering mathematics, calculus, statistics

**Nougat** - Free Alternative:[10]
- **Capability**: OCR for mathematical expressions
- **Format**: Outputs LaTeX markup
- **Training**: Trained on 8.2M academic pages
- **Command**: `nougat path/to/file.pdf -o output_dir`

**LaTeX Extraction Pipeline**:
```python
# Using Mathpix API
from mathpix import mathpix_api
result = mathpix_api.latex(
    src='equation_image.png',
    formats=['latex_styled']
)
```

#### Chemical Formulas & Diagrams

**Mathpix Chemistry**:[16]
- **Formats**: SMILES, InChI, InChI Key, MOL
- **Extraction**: Chemical formulas, structures, diagrams
- **Integration**: Works with ChemDraw

**ChemScraper** - PDF Primitive Parser:[17]
- **Technology**: Leverages PDF graphics instructions
- **Speed**: Fast, accurate born-digital parsing
- **Open-source**: Free alternative to commercial tools

**ChemDataExtractor** - Specialized Tool:[18]
- **Capability**: Chemical entity recognition from PDFs
- **Template-based**: Semantic information extraction
- **Output**: Structured chemical data

#### Engineering Drawings & Diagrams

**YOLO + OCR Pipeline**:[19][20]
- **Detection**: Dimension lines, geometric shapes, text legends
- **OCR Engine**: Tesseract or EasyOCR for text
- **Output**: CSV coordinates, SVG, CAD formats
- **Process**:
  1. Edge detection (Canny filtering)
  2. Line extraction (Hough transforms)
  3. Curve identification (Hough circles)
  4. Text extraction (OCR)
  5. Export to CAD/SVG

**Vector Graphics Extraction**:
```python
import cv2
from pdf2image import convert_from_path

# Convert PDF to images
images = convert_from_path('drawing.pdf')
# Apply YOLO object detection for components
# Extract text with Tesseract OCR
```

#### Medical Images (DICOM, Radiology)

**DICOM Metadata Extraction**:[21][22]
- **Format**: DICOM headers contain patient, acquisition data
- **Tools**: `pydicom` library
- **Annotations**: DicomAnnotator for bounding boxes, labels
- **Code Example**:
```python
import pydicom
ds = pydicom.dcmread("scan.dcm")
patient_name = ds.PatientName
acquisition_params = ds[0x0018]  # Acquisition group
```

**Image Processing Pipeline**:
- **Storage**: Keep DICOM format for metadata preservation
- **Compression**: JPEG 2000 for quality retention
- **Annotations**: Store separately in database linked by study ID

### Chunking Strategies

#### Semantic Chunking (Recommended for Both Arabic & English)

**LangChain RecursiveCharacterTextSplitter**:[23][24][25]
- **Algorithm**: Hierarchical splitting (paragraph → sentence → word)
- **Advantages**: Preserves semantic context, doesn't break mid-word
- **Parameters**:
```python
from langchain.text_splitter import RecursiveCharacterTextSplitter

text_splitter = RecursiveCharacterTextSplitter(
    chunk_size=512,  # Optimal for medical/academic
    chunk_overlap=128,  # 25% overlap for continuity
    separators=['\n\n', '\n', '. ', ' ', ''],
    length_function=len
)
chunks = text_splitter.split_text(text)
```

**Arabic-Specific Configuration**:
```python
# Arabic sentence boundaries
arabic_splitter = RecursiveCharacterTextSplitter(
    chunk_size=512,
    chunk_overlap=128,
    separators=['\n\n', '\n', '。', '؟', '!', '. ', ' ', '']
)
```

#### Sentence-Aware Chunking for Medical Content

**Best Practice**:[26][27]
- **Medical Context**: Preserves clinical terminology integrity
- **Implementation**: Use spaCy sentence boundary detection
- **Advantage**: 15-20% better context recall than fixed-size

**Advanced: Semantic Splitting**:[28]
- **Concept**: Groups semantically similar sentences
- **Tool**: LangChain SemanticChunker
- **Use Case**: Complex academic papers with thematic sections

### Embedding Models

#### Multilingual (Arabic + English Support)

**BGE-M3** - Top Choice:[29][26]
- **Performance**: Best overall for multilingual RAG
- **Dimensions**: 1024-dimensional embeddings
- **Languages**: 100+ including Arabic, English
- **Installation**: `sentence-transformers/BGE-M3`
- **Code**:
```python
from sentence_transformers import SentenceTransformer
model = SentenceTransformer('BAAI/bge-m3')
embeddings = model.encode(chunks)
```

**Multilingual-E5-large**:[29][26]
- **Context Recall**: Excellent for Arabic
- **Dimensions**: 1024
- **Model**: `intfloat/multilingual-e5-large`
- **Usage**: Academic content with high precision needs

#### Arabic-Specific Models

**Swan Models**:[30]
- **Specialization**: Dialect-aware Arabic embeddings
- **Coverage**: MSA + regional dialects
- **Performance**: Superior for Arabic-only applications

**AraVec**:[31]
- **Variations**: CBOW and Skip-Gram
- **Medical**: Tested on health tweets classification
- **Size**: Multiple dimensions (100, 300)

#### Medical Domain-Specific

**PubMedBERT Embeddings**:[32][31]
- **Training**: Biomedical literature corpus
- **Advantage**: Medical terminology understanding
- **Implementation**: `microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract`

**Arabic Medical Embeddings**:[32]
- **Model**: Contextual Arabic biomedical embeddings
- **Transformer-based**: BERT architecture
- **Use Case**: Arabic medical question classification

### Backend Architecture

#### Container Stack (Docker Compose)

**docker-compose.yml Structure**:
```yaml
version: '3.8'

services:
  # Vector DB - Medical Domain
  qdrant-medical:
    image: qdrant/qdrant:latest
    ports:
      - "6333:6333"
      - "6334:6334"
    volumes:
      - ./qdrant_medical:/qdrant/storage
    environment:
      - QDRANT__SERVICE__GRPC_PORT=6334
    restart: always
    
  # Vector DB - Academic Domain
  qdrant-academic:
    image: qdrant/qdrant:latest
    ports:
      - "6335:6333"
      - "6336:6334"
    volumes:
      - ./qdrant_academic:/qdrant/storage
    restart: always
    
  # Redis Cache
  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    volumes:
      - ./redis_data:/data
    command: redis-server --appendonly yes
    restart: always
    
  # LLM Server (Ollama)
  ollama:
    image: ollama/ollama:latest
    ports:
      - "11434:11434"
    volumes:
      - ./ollama_models:/root/.ollama
    environment:
      - OLLAMA_MODELS=/root/.ollama/models
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: 1
              capabilities: [gpu]  # If GPU available
    restart: always
    
  # RAG Backend API - Medical
  rag-medical:
    build: ./backend-medical
    ports:
      - "8001:8000"
    environment:
      - QDRANT_URL=http://qdrant-medical:6333
      - REDIS_URL=redis://redis:6379
      - OLLAMA_URL=http://ollama:11434
      - DOMAIN=medical
    volumes:
      - ./data/medical:/app/data
    depends_on:
      - qdrant-medical
      - redis
      - ollama
    restart: always
    
  # RAG Backend API - Academic
  rag-academic:
    build: ./backend-academic
    ports:
      - "8002:8000"
    environment:
      - QDRANT_URL=http://qdrant-academic:6333
      - REDIS_URL=redis://redis:6379
      - OLLAMA_URL=http://ollama:11434
      - DOMAIN=academic
    volumes:
      - ./data/academic:/app/data
    depends_on:
      - qdrant-academic
      - redis
      - ollama
    restart: always

networks:
  default:
    name: rag-network
```

#### Backend API Implementation (FastAPI)

**backend-medical/main.py**:
```python
from fastapi import FastAPI, UploadFile, File
from fastapi.middleware.cors import CORSMiddleware
from fastapi.responses import StreamingResponse
from qdrant_client import QdrantClient
from sentence_transformers import SentenceTransformer
import redis
import httpx
import json
from typing import AsyncIterator

app = FastAPI()

# CORS for frontend connection
app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],  # Configure specific origins in production
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

# Initialize clients
qdrant = QdrantClient(url="http://qdrant-medical:6333")
redis_client = redis.from_url("redis://redis:6379")
embedding_model = SentenceTransformer('BAAI/bge-m3')
COLLECTION_NAME = "medical_knowledge"

# SSE Streaming Response
async def generate_rag_response(query: str) -> AsyncIterator[str]:
    # 1. Check semantic cache
    cache_key = f"query:{hash(query)}"
    cached = redis_client.get(cache_key)
    if cached:
        yield f"data: {json.dumps({'source': 'cache', 'text': cached.decode()})}\n\n"
        return
    
    # 2. Generate query embedding
    query_embedding = embedding_model.encode(query).tolist()
    
    # 3. Search Qdrant
    search_results = qdrant.search(
        collection_name=COLLECTION_NAME,
        query_vector=query_embedding,
        limit=5
    )
    
    # 4. Build context
    context = "\n\n".join([hit.payload['text'] for hit in search_results])
    
    # 5. Stream LLM response
    prompt = f"Context: {context}\n\nQuestion: {query}\n\nAnswer:"
    
    async with httpx.AsyncClient() as client:
        async with client.stream(
            'POST',
            'http://ollama:11434/api/generate',
            json={'model': 'phi3:mini', 'prompt': prompt, 'stream': True},
            timeout=120.0
        ) as response:
            full_response = ""
            async for line in response.aiter_lines():
                if line:
                    chunk = json.loads(line)
                    text = chunk.get('response', '')
                    full_response += text
                    yield f"data: {json.dumps({'text': text})}\n\n"
    
    # 6. Cache response
    redis_client.setex(cache_key, 3600, full_response)

@app.post("/query")
async def query_endpoint(query: str):
    return StreamingResponse(
        generate_rag_response(query),
        media_type="text/event-stream"
    )

@app.post("/upload")
async def upload_pdf(file: UploadFile = File(...)):
    # PDF processing logic
    # Extract, chunk, embed, store in Qdrant
    pass

@app.get("/health")
async def health_check():
    return {"status": "healthy"}
```

#### Qdrant Index Configuration

**Optimal Settings for 24GB RAM**:
```python
from qdrant_client.models import VectorParams, Distance, HnswConfigDiff

qdrant.create_collection(
    collection_name="medical_knowledge",
    vectors_config=VectorParams(
        size=1024,  # BGE-M3 dimensions
        distance=Distance.COSINE
    ),
    hnsw_config=HnswConfigDiff(
        m=16,  # Number of connections
        ef_construct=128,  # Index build quality
        full_scan_threshold=10000
    ),
    optimizers_config={
        "indexing_threshold": 20000
    }
)
```

**Payload Indexing for Fast Filtering**:
```python
qdrant.create_payload_index(
    collection_name="medical_knowledge",
    field_name="category",
    field_schema="keyword"
)
```

### Frontend Architecture

#### Next.js Implementation (Recommended for Medical)

**Key Features**:[33][34][35]
- **SSR + SSE**: Server-side rendering with streaming events
- **Performance**: Modular rendering, adaptive hydration
- **Stability**: Production-ready, extensive ecosystem

**pages/api/stream.ts** (API Route):
```typescript
import type { NextApiRequest, NextApiResponse } from 'next';

export default async function handler(
  req: NextApiRequest,
  res: NextApiResponse
) {
  res.setHeader('Content-Type', 'text/event-stream');
  res.setHeader('Cache-Control', 'no-cache');
  res.setHeader('Connection', 'keep-alive');

  const { query } = req.body;
  
  const response = await fetch('http://backend-medical:8000/query', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ query })
  });

  const reader = response.body?.getReader();
  const decoder = new TextDecoder();

  while (true) {
    const { done, value } = await reader!.read();
    if (done) break;
    
    const chunk = decoder.decode(value);
    res.write(chunk);
  }
  
  res.end();
}
```

**components/MedicalChat.tsx**:
```typescript
'use client';
import { useState, useEffect } from 'react';

export default function MedicalChat() {
  const [query, setQuery] = useState('');
  const [response, setResponse] = useState('');
  const [isLoading, setIsLoading] = useState(false);

  const handleQuery = async () => {
    setIsLoading(true);
    setResponse('');
    
    const eventSource = new EventSource(
      `/api/stream?query=${encodeURIComponent(query)}`
    );

    eventSource.onmessage = (event) => {
      const data = JSON.parse(event.data);
      setResponse(prev => prev + data.text);
    };

    eventSource.onerror = () => {
      eventSource.close();
      setIsLoading(false);
    };
  };

  return (
    <div className="medical-chat">
      <input
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        placeholder="Ask medical question..."
      />
      <button onClick={handleQuery} disabled={isLoading}>
        {isLoading ? 'Processing...' : 'Submit'}
      </button>
      <div className="response-area">
        {response}
      </div>
    </div>
  );
}
```

#### SvelteKit Implementation (Recommended for Academic)

**Key Advantages**:[36][37]
- **Lightweight**: Smaller bundle size, faster load times
- **SSE Native**: Built-in streaming support
- **Developer Experience**: Simple, intuitive API

**src/routes/api/query/+server.ts**:
```typescript
import { json } from '@sveltejs/kit';
import type { RequestHandler } from './$types';

export const POST: RequestHandler = async ({ request }) => {
  const { query } = await request.json();
  
  const stream = new ReadableStream({
    async start(controller) {
      const response = await fetch('http://backend-academic:8000/query', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ query })
      });

      const reader = response.body?.getReader();
      const decoder = new TextDecoder();

      while (true) {
        const { done, value } = await reader!.read();
        if (done) break;
        
        const chunk = decoder.decode(value);
        controller.enqueue(`data: ${chunk}\n\n`);
      }
      
      controller.close();
    }
  });

  return new Response(stream, {
    headers: {
      'Content-Type': 'text/event-stream',
      'Cache-Control': 'no-cache'
    }
  });
};
```

**src/routes/+page.svelte**:
```svelte
<script lang="ts">
  import { source } from 'sveltekit-sse';
  
  let query = '';
  let response = '';
  
  async function handleQuery() {
    const connection = source('/api/query', {
      options: {
        method: 'POST',
        body: JSON.stringify({ query })
      }
    });
    
    connection.select('message').subscribe((data) => {
      response += data;
    });
  }
</script>

<div class="academic-interface">
  <textarea bind:value={query} placeholder="Academic question..." />
  <button on:click={handleQuery}>Search</button>
  <div class="results">{response}</div>
</div>
```

### File Upload & Processing Pipeline

#### Server-Side File Management

**Upload to Backend Container**:
```python
# In backend API
@app.post("/upload-batch")
async def upload_batch(files: list[UploadFile]):
    for file in files:
        # Save to container volume
        file_path = f"/app/data/{file.filename}"
        with open(file_path, "wb") as f:
            f.write(await file.read())
        
        # Process asynchronously
        await process_pdf_task.delay(file_path)
    
    return {"status": "uploaded", "count": len(files)}
```

**Processing Pipeline** (Celery/Background Task):
```python
from celery import Celery
import fitz

celery_app = Celery('tasks', broker='redis://redis:6379')

@celery_app.task
def process_pdf_task(file_path: str):
    # 1. Extract text
    doc = fitz.open(file_path)
    full_text = "".join([page.get_text() for page in doc])
    
    # 2. Chunk
    chunks = text_splitter.split_text(full_text)
    
    # 3. Generate embeddings
    embeddings = embedding_model.encode(chunks)
    
    # 4. Store in Qdrant
    points = [
        {
            "id": i,
            "vector": embedding.tolist(),
            "payload": {
                "text": chunk,
                "source": file_path,
                "page": i // chunks_per_page
            }
        }
        for i, (chunk, embedding) in enumerate(zip(chunks, embeddings))
    ]
    
    qdrant.upsert(
        collection_name="medical_knowledge",
        points=points
    )
```

#### Local Development Workflow

**Sync Files to Container**:
```bash
# Using Docker volume mount
docker cp ./local-pdfs/medical/ container_id:/app/data/medical/

# Or using docker-compose volume
# Already mapped in docker-compose.yml:
# volumes:
#   - ./data/medical:/app/data
```

**Direct Processing from Local**:
```bash
# Enter container
docker exec -it rag-medical bash

# Navigate to data directory
cd /app/data

# Run processing script
python process_documents.py --directory ./medical --collection medical_knowledge
```

### Deployment with Coolify

#### Coolify MCP Protocol

**MCP Server Configuration**:[38][39]
```json
{
  "mcpServers": {
    "coolify-rag": {
      "command": "npx",
      "args": ["-y", "@coolify/mcp-server"],
      "env": {
        "COOLIFY_URL": "https://your-coolify.instance",
        "COOLIFY_API_TOKEN": "your-token"
      }
    }
  }
}
```

**Deploy via MCP**:
```bash
# Using Claude Desktop or MCP client
# Command: Deploy RAG backend to Coolify

# MCP will execute:
# 1. Build Docker images
# 2. Push to registry
# 3. Create resources in Coolify
# 4. Configure environment variables
# 5. Deploy containers
```

#### Coolify CLI Deployment

**Install Coolify CLI**:
```bash
npm install -g @coolify/cli
coolify login
```

**Deploy Backend**:
```bash
# Create project
coolify projects create --name rag-system

# Deploy medical backend
coolify deploy \
  --project rag-system \
  --name backend-medical \
  --image ghcr.io/yourusername/rag-medical:latest \
  --port 8000 \
  --env QDRANT_URL=http://qdrant-medical:6333 \
  --env REDIS_URL=redis://redis:6379 \
  --volume ./data/medical:/app/data

# Deploy academic backend
coolify deploy \
  --project rag-system \
  --name backend-academic \
  --image ghcr.io/yourusername/rag-academic:latest \
  --port 8000 \
  --env QDRANT_URL=http://qdrant-academic:6333

# Deploy Qdrant instances
coolify deploy \
  --project rag-system \
  --name qdrant-medical \
  --image qdrant/qdrant:latest \
  --port 6333 \
  --volume ./qdrant_medical:/qdrant/storage
```

**Deploy Frontend**:
```bash
# Medical frontend (Next.js)
coolify deploy \
  --project rag-system \
  --name frontend-medical \
  --build-pack nextjs \
  --domain medical.yourdomain.com \
  --env NEXT_PUBLIC_API_URL=https://api-medical.yourdomain.com

# Academic frontend (SvelteKit)
coolify deploy \
  --project rag-system \
  --name frontend-academic \
  --build-pack sveltekit \
  --domain academic.yourdomain.com \
  --env PUBLIC_API_URL=https://api-academic.yourdomain.com
```

### Deployment with Dokploy

#### Dokploy CLI Setup

**Installation**:[40]
```bash
# Install Dokploy CLI
npm install -g dokploy-cli

# Authenticate
dokploy login --url https://your-dokploy.instance
```

#### Deploy Using Docker Compose

**Method 1: Upload Compose File**:[41][42]
```bash
# Upload docker-compose.yml
dokploy stacks create \
  --name rag-system \
  --compose-file ./docker-compose.yml

# Deploy stack
dokploy stacks deploy --name rag-system
```

**Method 2: CLI Commands**:[43]
```bash
# Create individual services
dokploy services create \
  --name qdrant-medical \
  --image qdrant/qdrant:latest \
  --port 6333:6333 \
  --volume qdrant_medical:/qdrant/storage \
  --restart always

dokploy services create \
  --name redis \
  --image redis:7-alpine \
  --port 6379:6379 \
  --volume redis_data:/data \
  --command "redis-server --appendonly yes"

dokploy services create \
  --name ollama \
  --image ollama/ollama:latest \
  --port 11434:11434 \
  --volume ollama_models:/root/.ollama \
  --gpu nvidia  # If GPU available

# Deploy backend from Git
dokploy apps create \
  --name backend-medical \
  --git-url https://github.com/yourusername/rag-backend \
  --branch main \
  --build-pack docker \
  --port 8000 \
  --env QDRANT_URL=http://qdrant-medical:6333 \
  --env REDIS_URL=redis://redis:6379 \
  --env OLLAMA_URL=http://ollama:11434
```

#### Dokploy Web Interface Method

**Step-by-Step**:[42]
1. Navigate to Dokploy dashboard
2. Click "New Stack" → "Import Compose"
3. Upload `docker-compose.yml`
4. Configure environment variables in UI
5. Set resource limits (CPU: 2 cores, RAM: 8GB for backend)
6. Click "Deploy Stack"

**Monitoring**:
```bash
# View logs
dokploy logs --service backend-medical --follow

# Check resource usage
dokploy stats --service backend-medical

# Access container terminal
dokploy exec --service backend-medical --command /bin/bash
```

### Frontend-Backend Connection Architecture

#### Communication Protocols

**Server-Sent Events (SSE)** - Recommended:[34][44][35]
- **Use Case**: LLM streaming responses
- **Advantages**: Automatic reconnection, simpler than WebSockets
- **Implementation**: Native browser EventSource API

**WebSockets** - Alternative:[45][46]
- **Use Case**: Bidirectional real-time updates
- **Complexity**: Requires connection management
- **When to Use**: Collaborative features, live updates from multiple sources

**REST API** - Fallback:
- **Use Case**: Non-streaming queries, file uploads
- **Simplicity**: Standard HTTP requests
- **Caching**: Easier to cache with CDN

#### Cross-Origin Configuration

**Backend CORS Settings** (FastAPI):
```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=[
        "https://medical.yourdomain.com",
        "https://academic.yourdomain.com",
        "http://localhost:3000"  # Development
    ],
    allow_credentials=True,
    allow_methods=["GET", "POST", "PUT", "DELETE"],
    allow_headers=["*"],
)
```

**Frontend Environment Variables**:
```env
# Next.js (.env.local)
NEXT_PUBLIC_MEDICAL_API=https://api-medical.yourdomain.com
NEXT_PUBLIC_ACADEMIC_API=https://api-academic.yourdomain.com

# SvelteKit (.env)
PUBLIC_API_URL=https://api-academic.yourdomain.com
```

#### Load Balancing & High Availability

**Nginx Reverse Proxy Configuration**:
```nginx
upstream medical_backend {
    server backend-medical-1:8000;
    server backend-medical-2:8000;
    server backend-medical-3:8000;
}

server {
    listen 443 ssl;
    server_name api-medical.yourdomain.com;
    
    location / {
        proxy_pass http://medical_backend;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        
        # SSE specific settings
        proxy_buffering off;
        proxy_cache off;
        proxy_set_header Connection '';
        proxy_http_version 1.1;
        chunked_transfer_encoding off;
    }
}
```

### Performance Optimization Strategies

#### Caching Layers

**1. Embedding Cache** (Redis):
```python
def get_cached_embedding(text: str):
    cache_key = f"embedding:{hash(text)}"
    cached = redis_client.get(cache_key)
    
    if cached:
        return pickle.loads(cached)
    
    embedding = embedding_model.encode(text)
    redis_client.setex(cache_key, 86400, pickle.dumps(embedding))
    return embedding
```

**2. Semantic Query Cache**:
```python
def semantic_cache_lookup(query_embedding, threshold=0.95):
    # Store query embeddings in Redis with vector search
    # If similar query found (cosine > threshold), return cached response
    pass
```

**3. LLM Response Cache**:
```python
@app.post("/query")
async def query_with_cache(query: str):
    cache_key = f"llm:{hash(query)}"
    cached = redis_client.get(cache_key)
    
    if cached:
        return {"response": cached.decode(), "source": "cache"}
    
    # Generate new response...
    redis_client.setex(cache_key, 3600, response)
```

#### Indexing Optimization

**Qdrant HNSW Tuning**:[47][48]
```python
# For 24GB RAM with millions of vectors
hnsw_config = HnswConfigDiff(
    m=32,  # Higher = better accuracy, more memory
    ef_construct=256,  # Construction quality
    ef_search=128,  # Search quality (runtime parameter)
)

# Adjust at search time
search_results = qdrant.search(
    collection_name="medical_knowledge",
    query_vector=embedding,
    limit=10,
    search_params={"hnsw_ef": 64}  # Lower for speed, higher for accuracy
)
```

**Payload Filtering for Fast Retrieval**:
```python
from qdrant_client.models import Filter, FieldCondition, MatchValue

# Filter by category before vector search
filter_condition = Filter(
    must=[
        FieldCondition(
            key="category",
            match=MatchValue(value="cardiology")
        )
    ]
)

results = qdrant.search(
    collection_name="medical_knowledge",
    query_vector=embedding,
    query_filter=filter_condition,
    limit=5
)
```

#### Hybrid Search Implementation

**Combine Vector + Keyword Search**:[48][49]
```python
from qdrant_client.models import ScoredPoint
import numpy as np

def hybrid_search(query: str, collection: str):
    # 1. Vector search
    query_embedding = embedding_model.encode(query)
    vector_results = qdrant.search(
        collection_name=collection,
        query_vector=query_embedding,
        limit=20
    )
    
    # 2. Keyword search (BM25-like)
    keyword_results = qdrant.search(
        collection_name=collection,
        query_vector=query_embedding,
        query_filter=Filter(
            must=[
                FieldCondition(
                    key="text",
                    match=MatchValue(value=query)
                )
            ]
        ),
        limit=20
    )
    
    # 3. Reciprocal Rank Fusion
    def rrf_score(rank, k=60):
        return 1.0 / (k + rank)
    
    scores = {}
    for rank, result in enumerate(vector_results):
        scores[result.id] = scores.get(result.id, 0) + rrf_score(rank)
    
    for rank, result in enumerate(keyword_results):
        scores[result.id] = scores.get(result.id, 0) + rrf_score(rank)
    
    # Return top combined results
    sorted_results = sorted(scores.items(), key=lambda x: x[1], reverse=True)
    return sorted_results[:5]
```

### Error Handling & Stability

#### Backend Resilience

**Retry Logic**:
```python
from tenacity import retry, stop_after_attempt, wait_exponential

@retry(
    stop=stop_after_attempt(3),
    wait=wait_exponential(multiplier=1, min=2, max=10)
)
async def call_ollama_with_retry(prompt: str):
    async with httpx.AsyncClient() as client:
        response = await client.post(
            'http://ollama:11434/api/generate',
            json={'model': 'phi3:mini', 'prompt': prompt},
            timeout=120.0
        )
        return response.json()
```

**Circuit Breaker Pattern**:
```python
from pybreaker import CircuitBreaker

ollama_breaker = CircuitBreaker(
    fail_max=5,
    timeout_duration=60
)

@ollama_breaker
def call_ollama(prompt):
    # If fails 5 times, opens circuit for 60s
    return ollama_client.generate(prompt)
```

#### Frontend Error Handling

**SSE Reconnection**:
```typescript
function connectSSE(query: string, maxRetries = 3) {
  let retries = 0;
  
  function connect() {
    const eventSource = new EventSource(`/api/stream?query=${query}`);
    
    eventSource.onerror = () => {
      eventSource.close();
      
      if (retries < maxRetries) {
        retries++;
        setTimeout(connect, 2000 * retries);  // Exponential backoff
      } else {
        showError("Connection failed. Please try again.");
      }
    };
    
    return eventSource;
  }
  
  return connect();
}
```

### Critical Semantic Keywords for AI Code Generation

When prompting AI assistants to generate code, use these **specific technical terms** for accurate results:

#### Architecture Keywords
- **RAG pipeline**: Retrieval-Augmented Generation workflow
- **Vector database**: Qdrant, embedding storage, HNSW index
- **Semantic search**: Cosine similarity, ANN, dense retrieval
- **Dual-domain architecture**: Medical + Academic separation
- **Containerized microservices**: Docker Compose, isolated services

#### PDF Processing Keywords
- **PyMuPDF extraction**: fitz library, Arabic RTL text
- **Chunking strategy**: RecursiveCharacterTextSplitter, semantic boundaries
- **Nougat OCR**: Academic document, LaTeX equations
- **Mathpix API**: Mathematical formula extraction
- **DICOM metadata**: Medical image headers, pydicom

#### Embedding Keywords
- **BGE-M3**: Multilingual sentence transformer
- **Sentence-aware chunking**: Context preservation
- **1024-dimensional vectors**: Embedding size specification
- **Batch encoding**: Efficient embedding generation

#### Backend Keywords
- **FastAPI SSE**: Server-sent events, streaming responses
- **Async generators**: Python AsyncIterator, streaming
- **Redis caching**: Semantic cache, query cache, LRU
- **Qdrant points**: Vector payload, metadata filtering
- **Ollama streaming**: phi3:mini model, token streaming

#### Frontend Keywords
- **EventSource API**: Native browser SSE client
- **Next.js API routes**: Server-side streaming
- **SvelteKit endpoints**: +server.ts, ReadableStream
- **CORS configuration**: Cross-origin resource sharing
- **Real-time rendering**: Progressive display, chunk updates

#### Deployment Keywords
- **Docker Compose stack**: Multi-container orchestration
- **Coolify MCP**: Model Context Protocol deployment
- **Dokploy CLI**: Remote container management
- **Volume mounting**: Persistent storage, bind mounts
- **GPU passthrough**: NVIDIA runtime, CUDA support

#### Performance Keywords
- **HNSW parameters**: m, ef_construct, ef_search tuning
- **Hybrid search**: Vector + keyword, RRF fusion
- **Connection pooling**: Database clients, async pools
- **Batch processing**: Bulk upsert, parallel embeddings
- **Response streaming**: Chunked transfer encoding

### Production Checklist

#### Pre-Deployment
- [ ] Test PDF extraction on sample Arabic + English documents
- [ ] Validate chunking preserves semantic coherence
- [ ] Benchmark embedding generation speed (should be <500ms per document)
- [ ] Configure Qdrant collections with proper indexing
- [ ] Set up Redis persistence (AOF + RDB)
- [ ] Pull Ollama models (`ollama pull phi3:mini`)
- [ ] Test SSE streaming on slow connections
- [ ] Implement rate limiting (10 requests/minute per user)
- [ ] Configure HTTPS certificates for domains
- [ ] Set up monitoring (Prometheus + Grafana)

#### Post-Deployment
- [ ] Verify frontend-backend connectivity across networks
- [ ] Test file upload workflow end-to-end
- [ ] Monitor memory usage (should stay under 22GB of 24GB)
- [ ] Check Qdrant query latency (<100ms for vector search)
- [ ] Validate cache hit rates (>40% for production traffic)
- [ ] Test failover scenarios (container restarts)
- [ ] Benchmark concurrent user handling (target: 50+ simultaneous)
- [ ] Review logs for errors or warnings
- [ ] Test backup and restore procedures
- [ ] Document API endpoints and usage

This comprehensive guide provides production-ready architecture with optimal tools and configurations for building high-performance, stable RAG systems serving medical and academic domains.[50][51][2][1][26]

.......................................................................................................................................................
.....................................................................

