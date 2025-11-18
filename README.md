# TypeScript File Manager – AI-Enhanced File Management for Tech Teams

## Overview

TypeScript File Manager is an AI-enhanced file management system designed for development teams at startups and small-to-medium enterprises. The platform provides intelligent file organization, search capabilities, and automated workflows that help teams manage codebases and documentation more effectively.

Built for development teams that need better file organization and discovery, TypeScript File Manager combines traditional file management with Azure AI to deliver intelligent search, categorization, and workflow automation.

**Demo**: https://typescript-file-manager.shtrial.com

## Key Features

- **Intelligent File Organization**: AI-powered file categorization and tagging
- **Advanced Search**: Semantic search across codebases and documentation
- **Workflow Automation**: Automated file organization and cleanup
- **Code Analysis**: AI-powered insights on code structure and patterns
- **Team Collaboration**: Shared workspaces and file management
- **Version Control Integration**: Seamless integration with Git workflows

## Architecture

### Technology Stack

- **Frontend**: React, TypeScript, Vite
- **Backend**: Node.js, Express, TypeScript
- **Database**: Azure Database for PostgreSQL with pgvector
- **AI Services**: Azure OpenAI (Responses API), Azure AI Search
- **Storage**: Azure Blob Storage
- **Deployment**: Azure Static Web Apps / Azure App Service

### Shared Azure Infrastructure

TypeScript File Manager leverages shared Azure AI resources from `rg-shared-ai`:

- **Azure OpenAI**: `shared-openai-eastus2` for file analysis and categorization
- **Azure AI Search**: `shared-search-eastus2` for intelligent file search
- **PostgreSQL with pgvector**: Shared database for file embeddings
- **Azure Storage**: Shared storage account for file storage

## Configuration & Environment

### Required Environment Variables

```env
# Azure OpenAI Configuration
AZURE_OPENAI_ENDPOINT=https://shared-openai-eastus2.openai.azure.com/
AZURE_OPENAI_API_KEY=your_api_key
AZURE_OPENAI_DEPLOYMENT=gpt-4o
AZURE_OPENAI_API_VERSION=2024-02-15-preview

# Azure AI Search
AZURE_SEARCH_ENDPOINT=https://shared-search-eastus2.search.windows.net
AZURE_SEARCH_API_KEY=your_search_key
AZURE_SEARCH_INDEX_NAME=filemanager-index

# Database Configuration
DB_SERVER_HOST=your-postgres-server.postgres.database.azure.com
DB_NAME=filemanager
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_CONNECTION_STRING=postgresql://user:password@host:5432/database

# Azure Storage
AZURE_STORAGE_ACCOUNT=your_storage_account
AZURE_STORAGE_CONTAINER=filemanager-files
AZURE_STORAGE_CONNECTION_STRING=your_connection_string
```

**Note**: Secrets should be stored in Azure Key Vault or GitHub Secrets, never committed to git.

## Getting Started (Local Development)

### Prerequisites

- Node.js 20+
- pnpm package manager
- Azure subscription with access to shared resources

### Installation

1. **Clone the repository**

```bash
git clone https://github.com/shmindmaster/typescript-file-manager.git
cd typescript-file-manager
```

2. **Install dependencies**

```bash
pnpm install
```

3. **Configure environment**

```bash
cp .env.example .env.local
# Edit .env.local with your Azure service credentials
```

4. **Start development server**

```bash
pnpm dev
```

The application will be available at `http://localhost:3000`.

## Use Cases & Roadmap

### Current Use Cases

- **Development Teams**: Organize and search codebases and documentation
- **Documentation Teams**: Manage technical documentation and knowledge bases
- **Project Management**: File organization for project assets

### Planned Enhancements

- **Code Intelligence**: AI-powered code analysis and recommendations
- **Automated Refactoring**: Intelligent file restructuring suggestions
- **Team Insights**: Analytics on file usage and collaboration patterns
- **Integration Hub**: Connect with GitHub, GitLab, and other development tools

## License

Proprietary - All rights reserved
