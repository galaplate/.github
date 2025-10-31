# Galaplate 🚀

**A modern Go REST API boilerplate ecosystem with powerful tooling and code generation capabilities.**

## 🏗️ Architecture Overview

Galaplate is organized into three main repositories that work together to provide a complete development experience:

```
┌─────────────────┐    ┌─────────────────┐     ┌─────────────────┐
│       Core      |    │       CLI       │     │    Galaplate    │
│                 │    │                 │     │                 │
│ Framework &     │◄───│ Project         │────►│ Example         │
│ Libraries       │    │ Generator       │     │ Implementation  │
│                 │    │                 │     │                 │
│ • Fiber Router  │    │ • Templates     │     │ • Live Demo     │
│ • GORM Database │    │ • Scaffolding   │     │ • Documentation │
│ • Console Cmds  │    │ • Cross-platform│     │ • Best Practices│
│ • Job Queue     │    │                 │     │                 │
└─────────────────┘    └─────────────────┘     └─────────────────┘
```

## Repository Guide

### [galaplate/galaplate](https://github.com/galaplate/galaplate)
The reference implementation and documentation hub. Contains a fully working REST API with authentication, database operations, background jobs, and comprehensive documentation.

**Use this to:**
- See working examples of all features
- Learn best practices and patterns  
- Access complete documentation
- Get started quickly with a full-featured API

### [galaplate/core](https://github.com/galaplate/core)
The foundational library containing all reusable components and utilities. This is the heart of the Galaplate ecosystem.

**Features:**
- **Fiber-based HTTP router** with middleware support
- **GORM integration** for MySQL and PostgreSQL
- **Console command system** with built-in generators
- **Background job queue** with cron scheduling
- **Structured logging** with rotation
- **Validation & DTO** support
- **Authentication utilities**

### [🛠️ galaplate/cli](https://github.com/galaplate/cli)
The command-line tool for generating new projects and scaffolding code. Cross-platform binary for Linux, macOS, and Windows.

**Templates Available:**
- **API** ✅ - REST API with database integration
- **Full** 🚧 - Full-stack with frontend (coming soon)
- **Micro** 🚧 - Lightweight microservice (coming soon)

## 🚀 Quick Start

### 1. Install the CLI
```bash
# Quick install to /usr/local/bin
curl -s https://raw.githubusercontent.com/galaplate/cli/main/install.sh -o /tmp/install.sh && chmod +x /tmp/install.sh && sudo /tmp/install.sh

# Or install to custom directory
curl -s https://raw.githubusercontent.com/galaplate/cli/main/install.sh -o /tmp/install.sh && chmod +x /tmp/install.sh && sudo /tmp/install.sh -d ~/.local/bin
```

### 2. Generate a New Project
```bash
# Create a new API project
galaplate new my-api

# With custom database
galaplate new my-app --template=api --db=mysql

# Custom module name
galaplate new my-project --module=github.com/myuser/my-project
```

### 3. Start Development
```bash
cd my-api

# Setup database
go run main.go console db:up

# Generate code
go run main.go console make:model User
go run main.go console make:controller UserController

# Start development server
make dev
```

## Key Features

### Powerful Console Commands
Built-in generators for rapid development:
```bash
go run main.go console make:model User       # Generate models
go run main.go console make:controller API   # Generate controllers  
go run main.go console make:job EmailJob     # Generate background jobs
go run main.go console make:dto UserRequest  # Generate DTOs
go run main.go console db:up                 # Run migrations
```

### Background Processing
Robust job queue system with cron scheduling:
```go
// Queue jobs
queue.Dispatch(&jobs.EmailNotification{
    To: "user@example.com",
    Subject: "Welcome!",
})

// Schedule recurring tasks
scheduler.AddFunc("@daily", func() {
    // Daily cleanup task
})
```

### Database Integration
Seamless database operations with GORM:
```go
// Auto-migrations
db.AutoMigrate(&User{})

// Or create migration using dbmate
go run main.go console db:create create_users_table
Creating migration: db/migrations/20250831001745_create_users_table.sql
go run main.go console db:up

// Query with pagination
users := pagination.Paginate(db, &User{}, page, limit)
```

### Production Ready
- Structured logging with rotation
- Input validation and DTOs
- Authentication utilities
- Environment configuration
- Docker support
- Cross-platform builds

## Project Status

| Component | Status | Version | Language |
|-----------|--------|---------|-----------|
| **Core** | :x: Stable | v0.0.20 | Go 1.22+ |
| **CLI** | :x: Stable | v0.1.0 | Go 1.22+ |
| **Galaplate** | :x: Active | v0.0.8 | Go 1.22+ |

## 🗺️ Roadmap

### Current (v0.1.x)
- [x] Core framework with essential features
- [x] CLI tool with API template
- [x] Cross-platform releases
- [x] Comprehensive documentation
- [ ] Test setup and framework integration

### Next (v0.2.x)
- [ ] Full-stack template with frontend
- [ ] Microservice template
- [ ] Interactive project setup
- [ ] Template customization

### Future (v0.3.x)
- [ ] Custom template support
- [ ] Plugin system architecture
- [ ] Advanced monitoring tools
- [ ] Kubernetes deployment helpers

## Contributing

We welcome contributions! Each repository has its own contribution guidelines:

- **Core**: Framework improvements, new features, bug fixes
- **CLI**: Template enhancements, new generators, platform support
- **Galaplate**: Documentation, examples, tutorials

## License

MIT License - see individual repositories for details.

---

<div align="center">

**Built with ❤️ for the Go community**

[Documentation](https://github.com/galaplate/galaplate/tree/main/docs) • [Examples](https://github.com/galaplate/galaplate) • [CLI Releases](https://github.com/galaplate/cli/releases)

</div>
