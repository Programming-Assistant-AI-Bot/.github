# Programming Assistant AI Bot

A comprehensive AI-powered programming assistant system featuring a VS Code extension, web interface, and FastAPI backend for intelligent code analysis, generation, and assistance.

## 🚀 Overview

This project provides a complete ecosystem for AI-assisted programming, specializing in Perl development but extensible to other languages. The system combines real-time code analysis, intelligent suggestions, error detection, and multi-modal content processing through three integrated components.

## 🏗️ Architecture

```
git_check/
├── backend/           # FastAPI backend server
├── frontend/          # React web interface  
├── VsCodeExtension/   # VS Code extension
└── README.md         # This file
```

## 🎯 Key Features

- **🤖 AI-Powered Code Generation**: Convert comments to functional code
- **🔍 Intelligent Error Detection**: Real-time code analysis and error highlighting
- **📋 Alternative Code Suggestions**: Multiple implementation approaches for any code block
- **💬 Interactive Chat Interface**: Web-based AI programming assistant
- **📁 Multi-Modal Processing**: Analyze repositories, PDFs, and web content
- **🔐 Secure Authentication**: JWT-based user management
- **🔄 Real-time Streaming**: Live AI responses in both web and IDE
- **🧠 Vector-Based Search**: Semantic code matching using LanceDB embeddings and FAISS indexing
- **📚 Persistent Session Storage**: FAISS-powered document storage for conversation context

## 📦 Components

### 🖥️ Backend ([`backend/`](backend/))
FastAPI-based server providing AI integration and content processing.

**Tech Stack**: FastAPI, MongoDB, FAISS, Ollama LLM, JWT Authentication

**Key Features**:
- AI chat with session management
- Comment-to-code generation
- Repository and PDF analysis
- Error detection and code validation
- FAISS vector storage for semantic search and document persistence
- HuggingFace embeddings (all-MiniLM-L6-v2) for document indexing

**Quick Start**:
```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

### 🌐 Frontend ([`frontend/`](frontend/))
Modern React web interface for interacting with the AI assistant.

**Tech Stack**: React 19, Vite, Tailwind CSS, Radix UI

**Key Features**:
- Interactive chat interface
- Multi-session management with FAISS-backed document storage
- File upload and repository integration
- Real-time streaming responses
- Code syntax highlighting
- Persistent conversation context using vector embeddings

**Quick Start**:
```bash
cd frontend
npm install
npm run dev
```

### 🔧 VS Code Extension ([`VsCodeExtension/`](VsCodeExtension/))
Integrated development environment extension for seamless coding assistance.

**Key Features**:
- Real-time code suggestions
- Error detection and highlighting
- Sidebar alternative suggestions
- Context-aware code generation
- LanceDB vector search integration for semantic code matching

**Quick Start**:
```bash
cd VsCodeExtension
npm install
# Press F5 in VS Code to launch Extension Development Host
```

## 🧠 Vector Storage & Embeddings

The system uses advanced vector storage technologies for intelligent content retrieval:

- **FAISS (Facebook AI Similarity Search)**: High-performance similarity search for document storage and retrieval
- **HuggingFace Embeddings**: Uses `all-MiniLM-L6-v2` model for generating semantic embeddings
- **Persistent Session Storage**: User-specific and session-specific document indexes for maintaining conversation context
- **LanceDB Integration**: Additional vector database support in VS Code extension for semantic code search
- **Document Management**: Automatic indexing, filtering, and removal of documents based on metadata

## 🚦 Getting Started

### Prerequisites
- **Node.js**: 14.0+
- **Python**: 3.9+
- **MongoDB**: 4.4+
- **Ollama**: With perlbot3:latest model
- **VS Code**: 1.60.0+ (for extension)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd git_check
   ```

2. **Start Backend**
   ```bash
   cd backend
   pip install -r requirements.txt
   cp .env.example .env  # Configure environment variables
   uvicorn main:app --reload --port 8000
   ```

3. **Start Frontend**
   ```bash
   cd frontend
   npm install
   npm run dev  # Runs on http://localhost:5173
   ```

4. **Install VS Code Extension**
   ```bash
   cd VsCodeExtension
   npm install
   npm install -g vsce
   vsce package
   # Install the generated .vsix file in VS Code
   ```

### Configuration

**Backend Environment** (`.env`):
```env
MONGODB_URL=mongodb://localhost:27017
DATABASE_NAME=archelon_ai
JWT_SECRET_KEY=your-secret-key
OLLAMA_MODEL=perlbot3:latest
OLLAMA_BASE_URL=http://localhost:11434
```

**Frontend**: Automatically connects to `http://localhost:8000`

**VS Code Extension**: Configure through VS Code settings (`perlCodeGeneration.*`)

## 🎯 Usage Examples

### Comment-to-Code Generation
```perl
# Create a subroutine that validates email addresses
# AI generates:
sub validate_email {
    my ($email) = @_;
    return $email =~ /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
}
```

### Web Chat Interface
- Start conversations with the AI assistant
- Upload files, analyze repositories
- Get real-time streaming responses
- Manage multiple chat sessions with persistent context
- FAISS-powered document retrieval for relevant conversation history

### VS Code Integration
- Select code blocks for alternative suggestions
- Automatic error detection and highlighting
- Context-aware code completion
- Semantic search through codebase using vector embeddings

## 📡 API Documentation

Once the backend is running:
- **Swagger UI**: http://localhost:8000/docs
- **ReDoc**: http://localhost:8000/redoc

### Key Endpoints
- `POST /chats/chat` - AI chat interaction with vector-based context retrieval
- `POST /commentCode/suggest` - Code generation
- `POST /validate/error` - Error detection
- `POST /upload` - File processing with FAISS indexing
- `POST /analyze-repo` - Repository analysis

## 🧪 Development

### Running Tests
```bash
# Backend
cd backend && python -m pytest tests/

# Frontend  
cd frontend && npm test

# VS Code Extension
cd VsCodeExtension && npm test
```

### Building for Production
```bash
# Frontend
cd frontend && npm run build

# VS Code Extension
cd VsCodeExtension && vsce package
```

## 🔍 Troubleshooting

### Common Issues

1. **Backend Connection Failed**
   - Ensure MongoDB is running
   - Verify Ollama model is installed: `ollama pull perlbot3:latest`
   - Check environment variables in `.env`

2. **FAISS Index Issues**
   - Verify write permissions to session storage directory
   - Check for sufficient disk space for vector indexes
   - Ensure HuggingFace model downloads correctly

3. **VS Code Extension Not Working**
   - Verify backend is running on port 8000
   - Check extension logs in VS Code Output panel
   - Ensure workspace contains Perl files

4. **Frontend API Errors**
   - Confirm backend server is accessible
   - Check browser console for CORS issues
   - Verify authentication tokens

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open Pull Request

## 📋 Requirements Summary

| Component | Requirements |
|-----------|-------------|
| **Backend** | Python 3.9+, MongoDB 4.4+, Ollama, FAISS, 8GB+ RAM |
| **Frontend** | Node.js 14+, Modern browser |
| **VS Code Extension** | VS Code 1.60+, Node.js 14+, LanceDB |
| **System** | 10GB+ storage, Internet connection |

## 📄 License

This project is licensed under [LICENSE]. See individual component directories for specific licensing information.

## 🔗 Related Resources

- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [VS Code Extension API](https://code.visualstudio.com/api)
- [React Documentation](https://react.dev/)
- [Ollama Models](https://ollama.ai/library)
- [FAISS Documentation](https://faiss.ai/)
- [LanceDB Documentation](https://lancedb.github.io/lancedb/)

---

**Built with ❤️ using modern AI and web technologies**

*For detailed component documentation, see the README files in each subdirectory.*