# Product Catalog Exercise - Baseline Assessment

## Overview

This is a fullstack feature implementation exercise designed to establish a baseline of your current AI-assisted coding skills. You'll add product filtering capabilities to both the backend API and frontend interface of an e-commerce product catalog.

**Important**: This is an assessment, not a test. Use AI coding assistants however you're most comfortable. There are no restrictions or requirements on how you use AI tools - work the way you normally would.

## Goals

1. **Implement a complete fullstack feature** from backend to frontend
2. **Establish your baseline** for time, effort, and confidence when using AI assistants
3. **Experience your current workflow** before learning optimization techniques

## The Task

You'll implement product filtering in two parts:

### Use AI However You Want

There are **no rules or restrictions** on AI usage:

- **Work exactly as you normally would if you got this task in a real project today**

### Part 1: Backend API Filtering (TASK1.md)

Add filtering capabilities to the FastAPI backend that allow filtering products by price, category, keyword search, and sorting.

### Part 2: Frontend Filtering UI (TASK2.md)

Build a React frontend interface that connects to your backend filtering API and provides users with filtering controls.

## Project Structure

```
course_project_1/
├── TASK1.md          # Backend filtering requirements
├── TASK2.md          # Frontend filtering requirements
├── app/
│   ├── backend/      # FastAPI backend application
│   │   ├── app/
│   │   │   ├── api/
│   │   │   ├── models/
│   │   │   ├── services/
│   │   │   └── ...
│   │   └── tests/    # Backend tests (make these pass!)
│   └── frontend/     # React frontend application
│       └── src/
│           ├── components/
│           ├── lib/
│           └── types/
```

## Getting Started

### 1. Review the Codebase

Familiarize yourself with:

- **Backend**: `app/backend/app/` - Note the existing patterns for models, services, and logging
- **Frontend**: `app/frontend/src/` - Review the existing components and API client
- **Tests**: `app/backend/tests/` - Examine `test_products_filtering.py` to see what needs to pass

### 2. Start Backend Development

```bash
cd app/backend

# Install dependencies
uv venv --python 3.12
uv sync


# Start development server
uv run python run_api.py
```

Read `TASK1.md` and implement the backend filtering feature. Use AI assistants in whatever way feels natural to you.

### 3. Start Frontend Development

Once your backend filtering is working:

```bash
cd app/frontend

# Install dependencies
bun install

# Start development server
bun dev
```

Read `TASK2.md` and implement the frontend filtering UI. Again, use AI however you normally would.

## What to Track

As you work, please track the following metrics:

### ⏱️ Time Tracking

- **Backend time**: How long did TASK1 take?
- **Frontend time**: How long did TASK2 take?
- **Total time**: Overall exercise duration

### 💬 AI Interaction

- **Number of prompts**: How many times did you prompt your AI assistant?
- **Types of requests**: Were you asking for code generation? Debugging? Explanations?
- **Iteration cycles**: How many back-and-forth exchanges did it take?

### 😊 Confidence Level

After completing both tasks, rate your confidence (1-10):

- How confident are you that the code is **correct**?
- How confident are you that the code follows **best practices**?
- How well do you **understand** the generated code?
- How **maintainable** is the resulting code?

### 🐛 Issues Encountered

- Did the AI make mistakes? What kinds?
- Did you need to debug generated code?
- Were there type errors or test failures?
- How much manual fixing was required?

## Success Criteria

You've completed the exercise when:

- ✅ All backend tests pass (`uv run pytest`)
- ✅ Backend API accepts and processes filter parameters correctly
- ✅ Frontend displays a working filter interface
- ✅ Filters can be applied and results update accordingly
- ✅ You can manually test the full filtering flow in the browser

## Important Notes

### This is Not a Competition

The goal is to establish **your personal baseline**, not to compete with others. Be honest about:

- Time taken (don't rush!)
- Prompts used (track them all)
- Confidence levels (be realistic)
- Issues encountered (document everything)

### Documentation is Key

After completing the exercise, you'll reflect on:

- What worked well in your AI workflow?
- What was frustrating or slow?
- Where did you get stuck?
- What would you want to improve?

This reflection will inform the learning modules that follow.

## After Completion

When you're done, you'll have:

1. A working fullstack filtering feature
2. Baseline metrics for your AI-assisted coding workflow
3. Awareness of your current strengths and pain points
4. Context for the optimization techniques you'll learn next

## Questions?

- Check `app/backend/README.md` for backend setup details
- Check `app/frontend/README.md` for frontend setup details
- Review existing code patterns in `app/backend/app/` and `app/frontend/src/`
- Run `/health` endpoint to verify backend is running

## Ready?

Start with `TASK1.md` and use AI coding assistants however you normally would. Track your time, prompts, and confidence as you go.

Good luck! 🚀
