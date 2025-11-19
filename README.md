# Synapse – The AI-Native Knowledge OS

## Overview

**Synapse** is an intelligent asset manager that transforms your local file system into a queryable knowledge base. Using Azure OpenAI, Synapse performs semantic analysis on your documents, understands their content, auto-tags them, generates summaries, and allows you to chat with your documents using RAG (Retrieval Augmented Generation).

Instead of just moving files, Synapse understands what they contain and helps you organize, discover, and interact with your knowledge assets.

**Tagline**: "Turn your file system into a queryable knowledge base."

## Key Features

- **🧠 AI-Powered File Analysis**: Automatically generates summaries, tags, and categorization suggestions
- **💬 Document Chat (RAG)**: Ask questions about your documents and get AI-powered answers based on content
- **🔍 Smart Search**: Hybrid keyword and semantic search across your file system
- **🏷️ Auto-Tagging**: AI generates technical and thematic tags for intelligent organization
- **🔒 Sensitivity Detection**: Identifies files containing PII or sensitive information
- **📁 Intelligent Categorization**: Suggests optimal folder structures based on content
- **⚡ Real-time Scanning**: Progress tracking with live updates during file discovery
- **🎨 Modern UI**: Clean, responsive interface with dark mode support

## Architecture

### Technology Stack

- **Frontend**: React, TypeScript, Vite, Tailwind CSS
- **Backend**: Node.js, Express
- **AI Services**: Azure OpenAI (GPT-4/GPT-4o) with chat completions
- **File Processing**: textract for multi-format text extraction
- **UI Components**: lucide-react for icons

### Azure AI Integration

Synapse leverages Azure OpenAI services for intelligent file operations:

- **Chat Completions**: File analysis, summarization, and conversational Q&A
- **JSON Mode**: Structured responses for file metadata extraction
- **RAG Pattern**: Document context injection for accurate Q&A

## Configuration & Environment

### Required Environment Variables

Create a `.env` file in the root directory with the following configuration:

```env
# Azure OpenAI Core Configuration
AZURE_OPENAI_ENDPOINT=https://your-resource.openai.azure.com/
AZURE_OPENAI_KEY=your_api_key
AZURE_OPENAI_CHAT_DEPLOYMENT=gpt-4o
AZURE_OPENAI_CHAT_API_VERSION=2024-02-15-preview

# Optional: Server Configuration
PORT=3001
```

**Security Note**: Never commit `.env` files to git. Use `.env.example` as a template and store actual secrets in Azure Key Vault or secure environment variables.

## Getting Started

### Prerequisites

- Node.js 20+ or compatible version
- npm or pnpm package manager
- Azure OpenAI API access with a deployed model (gpt-4, gpt-4o, or compatible)
- Access to local file system for scanning

### Installation

1. **Clone the repository**

```bash
git clone https://github.com/shmindmaster/Synapse.git
cd Synapse
```

2. **Install dependencies**

```bash
npm install
```

3. **Configure environment**

```bash
cp .env.example .env
# Edit .env with your Azure OpenAI credentials
```

4. **Start the backend server**

```bash
npm run server
```

The server will start on `http://localhost:3001`.

5. **Start the frontend (in a new terminal)**

```bash
npm run dev
```

The application will be available at `http://localhost:5173`.

## Usage

### Basic Workflow

1. **Configure Directories**: 
   - Set input sources (directories to scan)
   - Set sort destinations (where files should be organized)

2. **Define Keywords**: 
   - Create keyword configurations for automatic file detection
   - Map keywords to destination folders

3. **Scan Files**: 
   - Initiate a scan across your configured directories
   - Watch real-time progress as files are analyzed

4. **AI Interactions**:
   - **Analyze**: Click "Analyze" on any file card to get:
     - Executive summary (2 sentences)
     - Semantic tags (5 technical/thematic tags)
     - Suggested category/folder
     - Sensitivity level (High/Low)
   
   - **Chat**: Click "Chat" to ask questions about the document:
     - Ask about specific content
     - Request clarifications
     - Get context-aware answers

5. **File Actions**:
   - Move or copy files to configured destinations
   - Automatic routing based on keyword matches

## API Endpoints

### POST `/api/search`
Scans directories for files matching keyword configurations.

**Request Body**:
```json
{
  "baseDirectories": [{"path": "/path/to/scan"}],
  "keywordConfigs": [{"keywords": ["keyword1"], "destinationFolder": "/dest"}]
}
```

### POST `/api/analyze`
Performs AI analysis on a specific file.

**Request Body**:
```json
{
  "filePath": "/path/to/file.txt"
}
```

**Response**:
```json
{
  "success": true,
  "analysis": {
    "summary": "Two sentence summary...",
    "tags": ["tag1", "tag2", "tag3", "tag4", "tag5"],
    "category": "Suggested Folder Name",
    "sensitivity": "Low"
  }
}
```

### POST `/api/chat`
Chat with a document using RAG.

**Request Body**:
```json
{
  "filePath": "/path/to/file.txt",
  "message": "What is this document about?",
  "history": []
}
```

**Response**:
```json
{
  "success": true,
  "reply": "Based on the document content..."
}
```

### POST `/api/file-action`
Move or copy a file to a destination.

**Request Body**:
```json
{
  "file": {"name": "file.txt", "path": "/source/file.txt"},
  "action": "move",
  "destination": "/dest/folder"
}
```

## Use Cases

- **Personal Knowledge Management**: Organize personal documents, research papers, and notes
- **Code Documentation**: Analyze and categorize technical documentation
- **Research & Analysis**: Quickly understand and query large document collections
- **Content Curation**: Auto-tag and organize downloaded articles and PDFs
- **Compliance & Security**: Identify sensitive files and ensure proper storage

## Roadmap

### Planned Enhancements

- **Vector Search**: Semantic similarity search using embeddings
- **Batch Processing**: Analyze multiple files simultaneously
- **Custom Prompts**: User-defined analysis templates
- **Export Features**: Save analysis results and chat history
- **Cloud Storage Integration**: Support for Azure Blob, S3, Google Drive
- **Multi-language Support**: Enhanced text extraction for international documents
- **Advanced RAG**: Chunk-based retrieval with citation

## Development

### Build for Production

```bash
npm run build
```

### Project Structure

```
Synapse/
├── src/
│   ├── components/
│   │   ├── shared/
│   │   │   ├── SmartFileCard.tsx    # AI-enhanced file display
│   │   │   └── InsightDrawer.tsx     # AI interaction panel
│   │   ├── KeywordSearch.tsx
│   │   ├── ConfigurationPanel.tsx
│   │   └── ...
│   ├── App.tsx                       # Main application
│   └── types.ts                      # TypeScript definitions
├── server.js                         # Express backend with AI
├── package.json
└── .env.example
```

## Contributing

This project is currently maintained by shmindmaster. Contributions, issues, and feature requests are welcome!

## License

Proprietary - All rights reserved

---

**Built with ❤️ using Azure OpenAI**
