# Chat485 — Full-Stack Conversational Web Application

## Overview

Chat485 is a conversational web application built iteratively across three projects. The work focused on the full web stack: dependable content generation, server-side application design, relational data modeling, authentication, RESTful APIs, and a responsive client-side interface.

The final product lets anonymous visitors or signed-in users create and manage private conversations, exchange messages with a configured chat-completion service, and browse chat history in a polished single-page interface.

| Project | Focus | Outcome |
| --- | --- | --- |
| **1. Static Site Generator** | Template rendering and command-line tooling | A reusable generator that turns templates, configuration data, and static assets into a complete static website. |
| **2. Server-Rendered Chat App** | Backend architecture, persistence, and authentication | A Flask application with account management, session-aware conversations, protected routes, and persisted message history. |
| **3. Client-Side Chat App** | REST API design and interactive frontend engineering | A React-powered chat client with asynchronous updates, pagination, account flows, and Markdown-rich messages. |

## Highlights

- Built a complete progression from static content generation to a database-backed, client-rendered web product.
- Designed conversations to work for both anonymous visitors and registered users, including migration of a visitor’s chats after sign-in.
- Enforced conversation ownership so that users and browser sessions can access only their own data.
- Integrated a configurable chat-completions service and preserved full message history for each conversation.
- Added user-focused touches: automatic conversation titles, message-history pagination, optimistic message rendering, model selection, Markdown support, syntax highlighting, and account settings.
- Developed with automated backend and end-to-end browser test coverage for core account, conversation, and chat flows.

## Project 1 — Templated Static Site Generator

Created a command-line static-site generator using Python, Click, and Jinja. It renders a configuration-driven set of pages, supports nested URL paths, and copies static assets into the generated site.

**Notable implementation work**

- Configuration-based page generation with per-page template context
- Jinja template rendering with HTML/XML auto-escaping
- Nested route-to-file output mapping
- Static-asset copying as part of the build process
- Clear handling for existing output directories, missing inputs, malformed configuration, and template-rendering errors
- Verbose build output for traceable generation

## Project 2 — Server-Rendered Chat Application

Built the first dynamic version of Chat485 with Flask, Jinja templates, and SQLite. This stage established the application’s relational data model and core user flows.

**Notable implementation work**

- Modeled users, sessions, conversations, and messages in a normalized SQLite database with foreign-key constraints
- Supported anonymous sessions as well as registered accounts
- Implemented registration, login, logout, session rotation, and account updates
- Stored salted password hashes and protected routes with authorization checks
- Persisted conversations and message history, including automatic titles derived from the first user message
- Implemented paginated history retrieval and graceful error pages for unauthorized or missing resources
- Connected user prompts to a chat-completion endpoint and stored assistant responses alongside user messages

## Project 3 — React Client and REST API

Rebuilt the experience as an interactive single-page application. The React client communicates with a Flask REST API and updates the interface without full-page navigation.

**Notable implementation work**

- Designed REST endpoints for accounts, sessions, conversations, messages, and available models
- Returned consistent JSON data and meaningful HTTP error responses for validation, authorization, conflict, missing-resource, and upstream-service failures
- Built reusable React components for the conversation sidebar, chat history, message composer, and account modals
- Managed client state for the signed-in user, selected conversation, conversation list, messages, pagination, and UI modals
- Added asynchronous conversation creation and deletion, automatic title updates, and optimistic message rendering
- Implemented “Load More” message-history pagination and automatic scroll behavior
- Rendered GitHub-flavored Markdown with code syntax highlighting in chat responses
- Added browser-level end-to-end tests for account flows, conversation management, and sending a chat message

## Technology

**Backend:** Python, Flask, Jinja, SQLite, REST APIs, HTTP Basic Authentication, cookie-based sessions  
**Frontend:** React, JavaScript/JSX, Webpack, CSS, Fetch API, React Markdown  
**Tooling & quality:** Click, Jinja, pytest, Cypress, ESLint, Prettier, Ruff

## Engineering Takeaways

This work strengthened our ability to design a web application across the stack: translating product flows into data models and HTTP contracts, separating client and server concerns, handling state and asynchronous UI updates, and building for both functionality and user experience.
