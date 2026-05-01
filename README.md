# Aurora-Py v1.0

Aurora-Py is an **enterprise-grade, offline-first agentic code generation platform** that transforms natural language prompts into production-ready Python code using local LLMs and retrieval-augmented generation.

## 🎯 Core Value Proposition

✅ **100% Local Execution** – No external APIs, no cloud dependencies  
✅ **Multi-Agent Orchestration** – Planner, Generator, Reviewer, Validator agents working in concert  
✅ **Production Quality** – Type hints, error handling, security hardening, comprehensive testing  
✅ **Real LLM Support** – Quantized GGUF models via `llama-cpp-python`  
✅ **RAG-Ready** – Knowledge base + semantic search for context enrichment  
✅ **Security-First** – Input validation, sanitization, static analysis, security audits  
✅ **Comprehensive Testing** – Auto-generated tests, coverage reporting, quality gates  

## 🚀 Quick Start

### Installation

```bash
# Clone and setup
git clone https://github.com/4Moon2Rox0/ara.git
cd ara
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

### Basic Usage

```bash
# Generate code from natural language
python aurora_orchestrator.py --prompt "Build a FastAPI CRUD app with SQLite"
```

**Output** will be in `./workspace/`:
- `aurora_report.json` – Execution summary and metrics
- `plan.py` – Requirements analysis
- `design.py` – Architecture patterns
- `implement.py` – Core implementation
- `test.py` – Test suite
- `secure.py` – Security hardening
- `review.py` – Code review findings
- `validate.py` – Validation & quality gates

### With Local LLM

```bash
# Download a model first (e.g., Mistral-7B GGUF from HuggingFace)
# Then:
python aurora_orchestrator.py \
  --prompt "Your request" \
  --model ./models/mistral-7b-instruct-v0.1.Q4_K_M.gguf
```

## 📋 Architecture

```
User Prompt (CLI)
    ↓
[Planner Agent] → Decompose into task DAG
    ↓
[RAG Service] → Retrieve relevant context + best practices
    ↓
[Generator Agents] → LLM-based code generation (parallel)
    ↓
[Reviewer Agent] → Static analysis (bandit, mypy, security)
    ↓
[Validator Agent] → Test execution, coverage analysis
    ↓
Production-Ready Code + Reports + Logs
```

## 🏗️ Core Modules

| Module | Purpose |
|--------|---------|
| `aurora_orchestrator.py` | Main orchestration engine |
| `config.py` | Configuration management |
| `rag.py` | Knowledge base + retrieval |
| `agent_utils.py` | Shared utilities (validation, subprocess, analysis) |
| `tests/` | Comprehensive test suite |

## 🔐 Security Features

- **Input Validation** – XSS, SQL injection, path traversal detection
- **Sanitization** – HTML escaping, control character removal
- **Subprocess Hardening** – Timeouts, isolated execution
- **Code Analysis** – Security audits, type checking, style validation
- **Secure Defaults** – No hardcoded credentials, least privilege

## 📊 Quality Metrics

| Metric | Target |
|--------|--------|
| Test Coverage | ≥85% |
| Type Hint Coverage | 100% |
| Code Generation Time | <30s |
| Full Pipeline | <2 min |
| Security Scan | 0 critical issues |

## 🛠️ Advanced Usage

### Custom Configuration

Create `.env` file:

```env
AURORA_LOG_LEVEL=INFO
AURORA_MAX_WORKERS=4
AURORA_TEST_COVERAGE_MIN=85
AURORA_DEFAULT_MODEL_SIZE=7b
```

### Running Tests

```bash
pytest tests/ -v --cov
```

### Extending with Custom Agents

```python
from aurora_orchestrator import AuroraOrchestrator

class CustomOrchestrator(AuroraOrchestrator):
    def custom_agent(self, task):
        """Add your custom agent logic."""
        pass
```

## 📚 Documentation

- **[QUICKSTART.md](./QUICKSTART.md)** – Installation and setup guide
- **[aurora_orchestrator.py](./aurora_orchestrator.py)** – Core engine with inline docs
- **[tests/](./tests/)** – Test suite with usage examples

## 🎓 Design Principles

Aurora-Py is built on enterprise software engineering best practices:

1. **SOLID Principles** – Single responsibility, open/closed, dependency injection
2. **Clean Code** – Readable, maintainable, well-documented
3. **Defensive Programming** – Comprehensive error handling, input validation
4. **Security-First** – Defense in depth, principle of least privilege
5. **Test-Driven** – 85%+ coverage, automated quality gates
6. **Performance** – Optimized algorithms, parallel execution where safe
7. **Extensibility** – Plugin points for Phase 2+ enhancements

## 🔮 Roadmap

### Phase 1 (Next)
- Full LLM integration (llama-cpp-python prompting)
- Advanced RAG (FAISS + semantic search)
- Refined CLI with progress bars
- Extended agent suite

### Phase 2
- Electron UI with rich code editor
- PyInstaller packaging (Windows MSI, macOS DMG)
- FastAPI backend for remote execution
- Plugin system for custom agents

### Phase 3
- Tree-sitter AST transformations
- Advanced security policies
- Performance profiling & optimization
- Enterprise telemetry (optional)

## 🤝 Contributing

Contributions welcome! See issues and discussions in the repo.

**Development setup:**
```bash
pip install -e ".[dev]"  # Install in editable mode
pytest --watch          # Run tests on file changes
```

## 📝 License

MIT License – See `LICENSE` file

## ⚡ Performance Tips

1. **Use smaller models (7B)** for faster generation
2. **Enable GPU** via `llama-cpp-python[cuda]` if available
3. **Batch operations** – Generate multiple code pieces in one run
4. **Tune timeouts** – Adjust based on your hardware
5. **Monitor RAM** – Check available memory before large runs

## 🐛 Troubleshooting

**ImportError for llama-cpp-python?**
```bash
pip install llama-cpp-python --no-binary :all:
```

**Subprocess timeouts?**
Increase timeout in `aurora_orchestrator.py` or use `--workers 2`

**Out of memory?**
Switch to a smaller model (3B/5B GGUF)

## 📞 Support

- **Issues:** https://github.com/4Moon2Rox0/ara/issues
- **Discussions:** https://github.com/4Moon2Rox0/ara/discussions

---

**Aurora-Py v1.0** – Enterprise-grade agentic code generation, running entirely on your machine.

Built with ❤️ for developers who value quality, security, and independence.
