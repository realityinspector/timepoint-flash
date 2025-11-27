# HANDOFF - TIMEPOINT Flash v2.0 Rebuild

**Status**: Phase 1 Complete ✅ | Phase 2 Ready to Start 🚀
**Date**: 2025-11-27
**Branch**: `main` (clean slate)

---

## What's Done

✅ GitHub cleanup complete (destructive operation executed)
✅ v1.0 archived → `archive/v1-legacy` branch + `v1.0.0-legacy` tag
✅ v1.0 docs archived → `archive/` directory
✅ Clean `main` branch with fresh start
✅ v2.0 README published
✅ REFACTOR.md plan written (26KB, comprehensive)

---

## Current State

**Repository Structure:**
```
timepoint-flash/
├── README.md              # v2.0 status, links to archive
├── REFACTOR.md            # 8-week rebuild plan (READ THIS FIRST)
└── archive/               # v1.0 docs (README, QUICKSTART, TESTING)
```

**Branches:**
- `main` - Clean slate (3 commits total)
- `archive/v1-legacy` - Full v1.0 codebase (preserved)

**Environment:**
- `.venv/` exists locally (from v1.0, may need rebuild)
- `.env` exists locally (has real API keys - preserve!)
- Database files cleaned (will need fresh setup)

---

## Next: Phase 2 - Core Infrastructure

**Your Mission**: Build foundational architecture for v2.0

### Tasks (see REFACTOR.md section 8.2 for details)

1. **Project Setup**
   - [ ] Create `pyproject.toml` (FastAPI, Pydantic, Mirascope, pytest)
   - [ ] Create `requirements.txt` (fallback)
   - [ ] Create `.gitignore`
   - [ ] Create `.env.example`

2. **Directory Structure**
   ```
   app/
   ├── main.py              # FastAPI app
   ├── config.py            # Settings with ProviderConfig
   ├── models.py            # SQLAlchemy (SQLite + PostgreSQL)
   ├── database.py          # DB connection
   ├── core/
   │   ├── providers.py     # Base classes
   │   ├── llm_router.py    # Mirascope integration
   │   └── providers/
   │       ├── google.py    # Google Gen AI SDK
   │       └── openrouter.py # OpenRouter API
   tests/
   ├── conftest.py          # Fixtures, markers
   └── unit/
       ├── test_providers.py
       └── test_llm_router.py
   ```

3. **Provider Abstraction** (priority)
   - [ ] `app/core/providers.py` - `LLMProvider`, `ProviderType`, `ProviderConfig`
   - [ ] `app/core/providers/google.py` - Google Gen AI SDK integration
   - [ ] `app/core/providers/openrouter.py` - OpenRouter API client
   - [ ] `tests/unit/test_providers.py` - Unit tests (mock API calls)

4. **LLM Router** (priority)
   - [ ] `app/core/llm_router.py` - Mirascope-powered routing with fallback
   - [ ] `tests/integration/test_llm_router.py` - Integration tests

5. **Database Setup**
   - [ ] `app/models.py` - Basic Timepoint model
   - [ ] `app/database.py` - SQLite + PostgreSQL support
   - [ ] Alembic migrations (optional for Phase 2)

6. **Testing Framework**
   - [ ] `tests/conftest.py` - pytest fixtures, markers (fast/integration/e2e)
   - [ ] Verify: `pytest -m fast` works (no API calls)

---

## Key Resources

**Must Read:**
1. `REFACTOR.md` - Complete 8-week plan (sections 3-8 most relevant)
2. Google Gemini API docs - https://ai.google.dev/gemini-api/docs
3. OpenRouter API docs - https://openrouter.ai/docs
4. Mirascope docs - https://mirascope.com/docs

**Reference v1.0:**
- Branch: `git checkout archive/v1-legacy`
- Useful files: `app/services/google_ai.py`, `app/services/openrouter.py`
- Don't copy/paste - redesign with clean architecture

**API Keys (in `.env`):**
```bash
GOOGLE_API_KEY=AIzaSyCuiMJrVPCist4IseTi919O1C2GOyL-goA  # Valid, working
OPENROUTER_API_KEY=sk-or-v1-...                         # Valid, working
```

---

## Success Criteria (Phase 2)

✅ `pytest -m fast` passes (5-10 unit tests)
✅ Provider abstraction works (Google + OpenRouter)
✅ LLM Router handles fallback correctly
✅ Database supports SQLite + PostgreSQL
✅ `pyproject.toml` installs cleanly
✅ Basic FastAPI app runs (`uvicorn app.main:app`)

**Time Budget**: Week 2 (5-7 days)

---

## Quick Commands

```bash
# Install dependencies (once you create pyproject.toml)
pip install -e .

# Run fast tests
pytest -m fast

# Run integration tests (requires API keys)
pytest -m integration

# Start FastAPI server (once main.py exists)
uvicorn app.main:app --reload

# Access v1.0 for reference
git checkout archive/v1-legacy
# Return to v2.0
git checkout main
```

---

## Important Notes

⚠️ **Don't reinstall from scratch** - `.venv/` and `.env` exist, reuse them
⚠️ **Test with real API keys** - both Google and OpenRouter keys work
⚠️ **Follow REFACTOR.md** - it's comprehensive and well-researched
⚠️ **Use Mirascope** - not LangChain abstractions
⚠️ **Commit often** - small, focused commits with descriptive messages

---

## Questions?

- Check `REFACTOR.md` sections 3-4 (architecture) and 8.2 (Phase 2 tasks)
- Reference `archive/v1-legacy` for working examples (redesign, don't copy)
- Google Gemini 3 Pro (`gemini-3-pro-preview`) is latest model
- No Gemini 3 Flash - use Gemini 2.5 Flash instead

---

**Ready to Build.** Start with `pyproject.toml` and `app/core/providers.py`.

**Next Handoff**: After Phase 2 complete → Phase 3 (Temporal System)
