# Product Catalog Frontend

E-commerce product catalog frontend - Module 1 Exercise

## Tech Stack

- **Runtime**: [Bun](https://bun.sh/) v1.2+
- **Framework**: React 19
- **Language**: TypeScript
- **UI Components**: [shadcn/ui](https://ui.shadcn.com/) (New York theme)
- **Styling**: Tailwind CSS v4
- **Code Quality**: [Biome](https://biomejs.dev/) (linting + formatting)
- **Form Handling**: React Hook Form + Zod

## Quick Start

```bash
# Install dependencies
bun install

# Start development server (with hot reload)
bun dev
# → http://localhost:3000

# Production build
bun run build

# Production server
bun start
```

## Project Structure

```
src/
├── types/
│   ├── product.ts        # Product types (matches backend models EXACTLY)
│   └── error.ts          # Error types (ErrorResponse, ApiError)
├── lib/
│   ├── logger.ts         # Structured JSON logging (mirrors backend)
│   ├── api-client.ts     # Type-safe API client
│   └── utils.ts          # Utility functions (Tailwind merge)
├── components/
│   ├── ui/               # shadcn components (Button, Card, etc.)
│   ├── ProductCard.tsx   # Single product display
│   └── ProductGrid.tsx   # Responsive grid with loading/empty states
├── App.tsx               # Main application component
└── index.tsx             # Bun server entry point
```

## Code Quality

This project uses [Biome](https://biomejs.dev/) for linting and formatting:

```bash
# Check code (lint + format)
bun run check

# Check and fix issues
bun run check:fix

# Lint only
bun run lint

# Lint with auto-fix
bun run lint:fix

# Format only
bun run format

# Format with write
bun run format:fix

# CI mode (for GitHub Actions, etc.)
bun run ci
```

**Configuration:**
- Line length: 120 characters (matching backend)
- Indent: 2 spaces
- Quotes: Double quotes
- Semicolons: Always
- Accessibility: a11y rules enabled

See `biome.json` for full configuration.

## Type Safety

All TypeScript types match the backend Pydantic models EXACTLY:

**Backend (Python)**:
```python
class Product(BaseModel):
    product_id: int
    product_name: str
    product_description: str
    product_price_usd: Decimal  # Serialized as string in JSON
    product_category: ProductCategory
    product_in_stock: bool
```

**Frontend (TypeScript)**:
```typescript
interface Product {
  product_id: number;
  product_name: string;
  product_description: string;
  product_price_usd: string; // Decimal from backend
  product_category: ProductCategory;
  product_in_stock: boolean;
}
```

## Structured Logging

Logging matches the backend pattern for AI readability:

```typescript
import { logger } from "@/lib/logger";

logger.info("fetching_products", {
  endpoint: "/api/products",
  operation: "fetchProducts",
});
```

**Output (JSON to console)**:
```json
{
  "timestamp": "2025-10-13T13:22:55.007Z",
  "level": "INFO",
  "logger_name": "frontend",
  "message": "fetching_products",
  "endpoint": "/api/products",
  "operation": "fetchProducts"
}
```

## Backend Integration

**API Base URL**: `http://localhost:8000` (configurable in `src/lib/api-client.ts`)

**Endpoints**:
- `GET /api/products` - Get all products
- `GET /health` - Health check

**Start backend**:
```bash
cd ../backend
uv run python run_api.py
```

## Key Patterns

### 1. Type Safety (Core Rule)
- All types match backend models EXACTLY
- Use `Decimal` → `string` for money values
- Complete type annotations everywhere

### 2. Structured Logging
- JSON logs to console (AI-readable)
- Include operation context
- Add `fix_suggestion` in errors

### 3. Error Handling
- Use `ApiError` for backend errors
- Use `Error` for network errors
- Consistent `ErrorResponse` structure

### 4. Component Patterns
- shadcn for UI consistency
- Proper accessibility (aria-labels, roles)
- Loading/empty/error states

### 5. Code Quality
- Biome for linting and formatting
- Line length 120 (matches backend)
- Accessibility rules enabled

## Development Tips

1. **HMR is enabled** - Changes reload automatically
2. **Console logs are JSON** - Easy for AI debugging
3. **Types are strict** - Follow backend models exactly
4. **Use shadcn** - Don't create custom UI components
5. **Run Biome** - Before committing code

## Troubleshooting

### Backend connection fails
1. Check backend is running: `cd ../backend && uv run python run_api.py`
2. Verify URL in `src/lib/api-client.ts`
3. Check CORS is enabled in backend

### Type errors
1. Compare types with backend models in `app/backend/app/models/`
2. Ensure Decimal fields are strings in frontend
3. Run `bun run check` for diagnostics

### Biome errors
```bash
# See what's wrong
bun run check

# Auto-fix most issues
bun run check:fix

# Apply unsafe fixes if needed
bunx biome check --write --unsafe src/
```

## Resources

- [Bun Documentation](https://bun.sh/docs)
- [React 19 Documentation](https://react.dev/)
- [shadcn/ui Documentation](https://ui.shadcn.com/)
- [Biome Documentation](https://biomejs.dev/)
- [Tailwind CSS Documentation](https://tailwindcss.com/)
