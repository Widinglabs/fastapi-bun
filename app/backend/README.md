# Product Catalog API - Module 1 Exercise

**Goal**: Experience the difference between fumbling (90%) and systematic (5%) AI coding.

## Quick Start

```bash
# Install dependencies
uv venv --python 3.12
uv add fastapi uvicorn pydantic pydantic-settings pytest httpx

# Run the API
uv run python run_api.py

# Test it (in another terminal)
curl http://localhost:8000/api/products

# Run tests
uv run pytest tests/test_products_basic.py -v
```

## Exercise Instructions

See **[EXERCISE.md](./EXERCISE.md)** for complete instructions.

## Project Structure

```
04_exercise/
├── EXERCISE.md              # Complete exercise instructions
├── SETUP_CANVAS.md          # Context for systematic attempt
├── pyproject.toml          # Project dependencies
├── run_api.py              # Development server
│
├── app/
│   ├── main.py             # FastAPI app initialization
│   ├── models/
│   │   ├── product.py      # Product and response models
│   │   └── error.py        # Error response model
│   ├── api/
│   │   └── products.py     # Product API endpoints
│   ├── services/
│   │   └── product_service.py  # Business logic
│   ├── core/
│   │   ├── config.py       # App configuration
│   │   └── logging_config.py   # JSON logging setup
│   └── data/
│       └── seed_products.py    # 30 sample products
│
└── tests/
    ├── conftest.py         # Test fixtures
    ├── test_products_basic.py      # Basic tests (passing ✅)
    └── test_products_filtering.py  # Filtering tests (stubs 📝)
```

## Key Features

### AI-Friendly Code

This codebase demonstrates best practices for AI-assisted development:

✅ **Verbose, clear names**: `product_price_usd`, `filter_products_by_category_and_price_range()`
✅ **Explicit types**: All functions have complete type hints
✅ **Structured logging**: JSON logs to stdout for AI debugging
✅ **Comprehensive docs**: Docstrings with examples on all functions
✅ **Clear patterns**: Service layer architecture, Pydantic validation

### Structured JSON Logging

All logs output as JSON to stdout:

```json
{
  "timestamp": "2025-01-15T10:30:45.123456Z",
  "level": "INFO",
  "logger_name": "app.services.product_service",
  "message": "retrieving_all_products",
  "total_products_in_database": 30,
  "operation": "get_all_products"
}
```

This makes it easy for AI to:
- Read error messages
- Understand application flow
- Debug issues
- See filter parameters

## The Exercise

You'll add filtering functionality to `GET /api/products` **twice**:

1. **Attempt 1 (Fumbling)**: Vague prompt, no context → frustrating
2. **Attempt 2 (Systematic)**: Rich setup context → smooth success

The goal is to **FEEL** the difference between the 90% and the 5%.

## What's Already Implemented

- ✅ FastAPI app with CORS and error handling
- ✅ Product model (30 sample products across 5 categories)
- ✅ GET /api/products endpoint (returns all products)
- ✅ Structured JSON logging to stdout
- ✅ Error response format
- ✅ Complete test suite demonstrating patterns

## What You'll Add

- 📝 Query parameter model (`ProductFilterParameters`)
- 📝 Filtering service function (`filter_and_search_products`)
- 📝 Update endpoint to accept filters
- 📝 Make 8 filtering tests pass

## Available Endpoints

### GET /health
Health check endpoint

### GET /api/products
Get all products (will support filtering after your implementation)

**Query Parameters (to be added):**
- `min_price_usd`: Minimum price filter
- `max_price_usd`: Maximum price filter
- `category`: Filter by category
- `search_keyword`: Search in name/description
- `sort_by`: Sort results

## Testing

```bash
# Run basic tests (should pass ✅)
uv run pytest tests/test_products_basic.py -v

# Run filtering tests (will fail until you implement ❌)
uv run pytest tests/test_products_filtering.py -v

# Run all tests
uv run pytest tests/ -v
```

## Development

```bash
# Start development server
uv run python run_api.py

# Access interactive API docs
open http://localhost:8000/docs
```

## Code Quality

This project uses [Ruff](https://docs.astral.sh/ruff/) for linting and formatting:

```bash
# Check code for issues (with auto-fix)
uv run ruff check app/ --fix

# Format code
uv run ruff format app/

# Check without fixing (for CI/CD)
uv run ruff check app/

# Run both check and format
uv run ruff check app/ --fix && uv run ruff format app/
```

**Configuration:**
- Line length: 120 characters
- Target: Python 3.12+
- Rules: pycodestyle, pyflakes, isort, pep8-naming, pyupgrade, flake8-bugbear, and more

See `pyproject.toml` for full configuration.

## Key Learning Points

1. **Setup is everything** - Same AI, different setup, 10x different results
2. **Context engineering** - Rich context → better code
3. **Validation matters** - Types and tests catch issues
4. **Logging is for AI too** - Structured logs help AI debug

Ready to start? Head to **[EXERCISE.md](./EXERCISE.md)**!
