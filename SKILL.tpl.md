---
name: goframe-v2
description: "GoFrame v2 development skill. Use only when the target Go project uses or is explicitly adopting GoFrame v2: the nearest go.mod requires github.com/gogf/gf/v2, existing Go files import github.com/gogf/gf/v2 or any github.com/gogf/gf/v2/... component package, or the user asks to scaffold, migrate, or build with GoFrame. Trigger for GoFrame-backed Go work such as APIs/controllers/services, middleware, routing/config, ORM/DAO/DO/entity/database operations, gf CLI/codegen, HTTP/gRPC services, and microservice conventions. Do not trigger for generic Go projects without GoFrame evidence, frontend-only work, shell scripts, or unrelated infrastructure tasks."
license: Apache-2.0
metadata:
  author: gogf
  version: "1.0.0"
compatibility: Requires Go 1.18+. Scaffolding commands (`gf init`, `gf gen`, `gf build`, `gf run`, `gf docker`, `gf pack`, `gf up`) need the gf CLI v2.4+ installed.
---

# How to Navigate References and Examples

This skill ships with **380+ reference docs** under `./references/` and **50+ runnable example projects** under `./examples/`. Use the routing map below **before writing code** to find the right entry point — do not rely on training-data guesses.

## Intent → Resource Routing Map

| User intent / topic | Read first |
|---|---|
| New project scaffolding (`gf init`), project layout | `./references/开发工具/项目创建-init.md`, `./references/框架设计/工程开发设计/工程目录设计.md` |
| HTTP routes / middleware / Cookie / Session / request-response | `./references/WEB服务开发/` |
| gRPC / service discovery / load balancing / microservice scaffolding | `./references/微服务开发/` |
| ORM / DAO / DO / Entity / chained query / transactions / soft delete | `./references/核心组件/数据库ORM/` |
| Logging (`glog`), structured JSON logging, log rotation | `./references/核心组件/日志组件/` |
| Configuration (`gcfg`), YAML/TOML/INI formats, hot reload | `./references/核心组件/配置管理/` |
| Error handling (`gerror`), error codes, stack traces | `./references/核心组件/错误处理/` |
| Cache (`gcache`), Redis adapter, memory cache | `./references/核心组件/缓存管理/` |
| Data validation (`gvalid`), struct tags, custom rules | `./references/核心组件/数据校验/` |
| Type conversion (`gconv`), JSON (`gjson`), encoding | `./references/核心组件/类型转换/`, `./references/组件列表/编码解码/` |
| CLI tools (`gf init`, `gf gen`, `gf build`, `gf run`, `gf docker`, `gf pack`, `gf up`) | `./references/开发工具/` |
| Observability / tracing / metrics / monitoring | `./references/服务可观测性/` |
| Deployment (Docker / Nginx / supervisor / standalone) | `./references/项目部署/` |
| Templates, i18n, command-line, resource packing | `./references/核心组件/` |
| Collection / network / system utility components | `./references/组件列表/` |
| Quick-start tutorials, "Hello World", middleware basics | `./references/快速开始/` |
| Step-by-step project scaffolding (`gf init` → Step 1-7) | `./references/项目脚手架/` |
| Common questions / FAQ | `./references/常见问题-FAQ.md` |

## End-to-End Example Projects

For full runnable projects, consult:

- **HTTP canonical**: `./examples/practices/user-http-service/` — RESTful user service with Session, middleware auth, OpenAPI docs
- **gRPC canonical**: `./examples/practices/user-grpc-service/` — gRPC user CRUD with MySQL
- **Single-feature demos**: `./examples/{httpserver,grpc,database,nosql,observability,balancer,config,registry}/<topic>/`

## All Example Projects by Category

The `./examples/` directory contains **40+ single-feature demos** organized into **9 categories** (full index at [`./examples/README.MD`](./examples/README.MD)). Use this map to find the closest reference project before writing code.

### `./examples/balancer/` — Service-side load balancing
- `http` — HTTP load balancing with etcd registration
- `polaris` — HTTP load balancing via Polaris service mesh

### `./examples/config/` — Distributed configuration centers
- `apollo` — Apollo configuration center
- `consul` — HashiCorp Consul KV
- `kubecm` — Kubernetes ConfigMap
- `nacos` — Alibaba Nacos
- `polaris` — Tencent Polaris

### `./examples/database/` — Database driver extensions
- `encoded-pass` — Custom MySQL driver with AES-encrypted password

### `./examples/grpc/` — gRPC service patterns
- `basic` — gRPC server/client basics (proto definition + service impl)
- `ctx` — gRPC context and metadata propagation
- `balancer` — gRPC client-side load balancing strategies
- `resolver` — etcd-based service discovery
- `rawgrpc` — Native gRPC without GoFrame wrapper

### `./examples/httpserver/` — HTTP server features
- `basic-auth` — HTTP Basic authentication
- `jwt` — JWT authentication middleware
- `proxy` — Reverse proxy / API gateway
- `rate-limit` — Rate limiting (token bucket / sliding window)
- `sse` — Server-Sent Events streaming
- `mcp-http` / `mcp-sse` — Model Context Protocol server (HTTP / SSE)
- `swagger-auth` — Swagger UI with auth
- `upload-file` — Multipart file upload
- `response-json-array` — JSON array responses

### `./examples/nosql/` — NoSQL databases
- `redis` — Redis cache, session, pub/sub
- `mongodb` — MongoDB document store

### `./examples/observability/` — Observability tooling
- `metric/` — Prometheus + OpenTelemetry metrics (counter, histogram, gauge, callback, etc.)
- `trace/` — Distributed tracing (HTTP, gRPC, OTLP, Jaeger, in-process, multi-process)

### `./examples/practices/` — End-to-end reference projects
- `user-http-service` — canonical RESTful user service
- `user-grpc-service` — canonical gRPC user service
- `quick-demo` — minimal HTTP CRUD demo
- `mvc-demo-chat` — MVC chat app with WebSocket
- `injection` — dependency injection with the `do` package

### `./examples/registry/` — Service registries
- `consul` — HashiCorp Consul service discovery
- `etcd` — etcd with TTL and watch
- `nacos` — Alibaba Nacos service discovery
- `polaris` — Tencent Polaris service mesh
- `file` — file-based registry (dev / test / offline)

## Workflow Phases

Apply these conventions phase-by-phase:

1. **Project bootstrap** — `gf init` → read `./references/开发工具/项目创建-init.md` + `./references/框架设计/工程开发设计/工程目录设计.md`. Mirror `./examples/practices/user-http-service` for layout.
2. **API definition & codegen** — write `api/.../*.go`, then run `gf gen ctrl` (see `./references/开发工具/代码生成-gen/接口规范-gen ctrl.md`); for ORM run `gf gen dao` (see `./references/开发工具/代码生成-gen/数据规范-gen dao.md`). DAO/DO/Entity files are auto-generated — **never hand-edit** them.
3. **Business logic** — implement in `internal/service/` (or `internal/logic/` if explicitly requested). Reference `./examples/practices/user-http-service` for layering patterns.
4. **Observability & deploy** — `./references/服务可观测性/` + `./references/项目部署/`.

# When to Apply

Apply the conventions in this skill when the project imports `github.com/gogf/gf/v2` and the user is doing any of:

- Scaffolding a new HTTP/gRPC service with `gf init`
- Implementing controllers, services, DAOs in an existing GoFrame codebase
- Reviewing or refactoring generated vs. hand-written code
- Database queries using `gdb` with DO objects (NOT `g.Map`)
- Configuring routing, logging, error handling, cache, or service observability
- Generating code with the `gf gen` CLI (DAO, controller, protobuf, enums)

Do **NOT** apply when:

- The project's `go.mod` does not require `github.com/gogf/gf/v2`
- The user is doing frontend, shell scripts, or pure Go libraries
- The user explicitly asks for Gin / Echo / Fiber / Chi — defer to that framework's skill

# Example Prompts This Skill Handles

| User prompt (paraphrased) | Open this resource |
|---|---|
| "Build a user service with GoFrame, RESTful CRUD" | `./examples/practices/user-http-service/` |
| "Quick-start a minimal HTTP demo" | `./examples/practices/quick-demo/` |
| "Use dependency injection in my GoFrame service" | `./examples/practices/injection/` |
| "Add JWT authentication to my GoFrame project" | `./examples/httpserver/jwt/` |
| "Add HTTP Basic authentication" | `./examples/httpserver/basic-auth/` |
| "Add rate limiting to a GoFrame HTTP endpoint" | `./examples/httpserver/rate-limit/` |
| "Build a reverse proxy / API gateway" | `./examples/httpserver/proxy/` |
| "Protect Swagger docs with auth" | `./examples/httpserver/swagger-auth/` |
| "Handle file uploads (multipart)" | `./examples/httpserver/upload-file/` |
| "Build a chat app with WebSocket" | `./examples/practices/mvc-demo-chat/` |
| "Add SSE streaming to my endpoint" | `./examples/httpserver/sse/` |
| "Set up MCP server for AI integration" | `./examples/httpserver/mcp-http/` or `./examples/httpserver/mcp-sse/` |
| "Build a gRPC service with etcd service discovery" | `./examples/grpc/resolver/` |
| "Use gRPC client-side load balancing" | `./examples/grpc/balancer/` |
| "Propagate context/metadata across gRPC" | `./examples/grpc/ctx/` |
| "Use raw gRPC without GoFrame wrapper" | `./examples/grpc/rawgrpc/` |
| "Connect to Apollo / Nacos / Consul / Polaris / k8s ConfigMap" | `./examples/config/{apollo,consul,nacos,polaris,kubecm}/` |
| "Implement service registry with etcd" | `./examples/registry/etcd/` |
| "Use file-based registry for dev/test" | `./examples/registry/file/` |
| "Encrypt database password in MySQL connection" | `./examples/database/encoded-pass/` |
| "Use Redis for cache / session / pub-sub" | `./examples/nosql/redis/` |
| "Use MongoDB document store" | `./examples/nosql/mongodb/` |
| "Set up Prometheus metrics + OpenTelemetry" | `./examples/observability/metric/` |
| "Set up distributed tracing with OpenTelemetry" | `./examples/observability/trace/` + `./references/服务可观测性/服务链路跟踪/` |
| "Use etcd for HTTP service load balancing" | `./examples/balancer/http/` |
| "Why isn't my `CreatedAt` saving?" | `Soft Delete & Time Maintenance` section below |
| "Generate DAO code for a new MySQL table" | `./references/开发工具/代码生成-gen/数据规范-gen dao.md` |
| "Configure structured JSON logging" | `./references/核心组件/日志组件/日志组件-JSON格式.md` |
| "Add Redis caching to my service" | `./references/核心组件/缓存管理/缓存管理-Redis缓存.md` + `./examples/nosql/redis/` |
| "Switch from `g.Map` to DO objects in my DAO" | `Component Usage Standards` section below |
| "Reverse-proxy my GoFrame service with Nginx" | `./references/项目部署/代理部署.md` |
| "Containerize my GoFrame app with Docker" | `./references/项目部署/容器部署.md` |
| "Walk me through project creation (gf init)" | `./references/快速开始/` + `./references/项目脚手架/` |
| "I hit an unusual error in GoFrame" | `./references/常见问题-FAQ.md` |

# Critical Conventions

## Project Development Standards
- For complete projects (HTTP/microservices), install GoFrame CLI and use `gf init` to create project scaffolding. See [Project Creation - init](./references/开发工具/项目创建-init.md) for details.
- Auto-generated code files (dao, do, entity) MUST NOT be manually created or modified per GoFrame conventions.
- Unless explicitly requested, do NOT use the `logic/` directory for business logic. Implement business logic directly in the `service/` directory.
- Reference complete project examples:
  - HTTP service best practice: [user-http-service](./examples/practices/user-http-service)
  - gRPC service best practice: [user-grpc-service](./examples/practices/user-grpc-service)

## Component Usage Standards
- Before creating new methods or variables, check if they already exist elsewhere and reuse existing implementations.
- Use the `gerror` component for all error handling to ensure complete stack traces for traceability.
- When exploring new components, prioritize GoFrame built-in components and reference best practice code from examples.
- **Database Operations MUST use DO objects** (`internal/model/do/`), never `g.Map` or `map[string]interface{}`. DO struct fields are `interface{}`; unset fields remain `nil` and are automatically ignored by the ORM:
  ```go
  // Good - use DO object
  dao.Users.Ctx(ctx).Where(cols.Id, id).Data(do.User{Uid: uid}).Update()

  // Good - conditional fields, unset fields are nil and ignored
  data := do.User{}
  if password != "" { data.PasswordHash = hash }
  if isAdmin != nil { data.IsAdmin = *isAdmin }
  dao.Users.Ctx(ctx).Where(cols.Id, id).Data(data).Update()

  // Good - explicitly set a column to NULL using gdb.Raw
  dao.Instances.Ctx(ctx).Where(cols.Id, id).Data(do.Instance{IdleSince: gdb.Raw("NULL")}).Update()

  // Bad - never use g.Map for database operations
  dao.Users.Ctx(ctx).Data(g.Map{cols.Uid: uid}).Update()
  ```
## Code Style Standards
- **Variable Declarations**: When defining multiple variables, use a `var` block to group them for better alignment and readability:
  ```go
  // Good - aligned and clean
  var (
      authSvc       *auth.Service
      bizCtxSvc     *bizctx.Service
      k8sSvc        *svcK8s.Service
      notebookSvc   *notebook.Service
      middlewareSvc *middleware.Service
  )

  // Avoid - scattered declarations
  authSvc := auth.New()
  bizCtxSvc := bizctx.New()
  k8sSvc := svcK8s.New()
  ```
- Apply this pattern when you have 3 or more related variable declarations in the same scope.

## Soft Delete & Time Maintenance

GoFrame provides **automatic** soft delete and time maintenance features. When a table contains `created_at`, `updated_at`, or `deleted_at` fields, the ORM handles these automatically.

### Automatic Time Fields

| Field | Auto Behavior |
|-------|---------------|
| `created_at` | Auto-written on `Insert/InsertAndGetId`, never modified afterward |
| `updated_at` | Auto-written on `Insert/Update/Save` |
| `deleted_at` | Auto-written on `Delete` (soft delete), auto-filtered on queries |

### Critical Rules

**1. NEVER manually set time fields** - GoFrame handles these automatically:
```go
// WRONG - redundant manual time setting
dao.User.Ctx(ctx).Data(do.User{
    Name:      "john",
    CreatedAt: gtime.Now(),  // REDUNDANT! Framework handles this
    UpdatedAt: gtime.Now(),  // REDUNDANT! Framework handles this
}).Insert()

// CORRECT - let framework handle time fields
dao.User.Ctx(ctx).Data(do.User{
    Name: "john",
}).Insert()
```

**2. NEVER manually add `WhereNull(cols.DeletedAt)`** - GoFrame auto-adds soft delete filter:
```go
// WRONG - redundant soft delete condition
dao.User.Ctx(ctx).
    Where(do.User{Status: 1}).
    WhereNull(cols.DeletedAt).  // REDUNDANT! Framework auto-adds this
    Scan(&list)

// CORRECT - framework auto-adds deleted_at IS NULL
dao.User.Ctx(ctx).
    Where(do.User{Status: 1}).
    Scan(&list)
```

**3. Use `Delete()` for soft delete** - Framework converts to `UPDATE SET deleted_at = NOW()`:
```go
// CORRECT - use Delete(), framework handles soft delete
dao.User.Ctx(ctx).Where(do.User{Id: id}).Delete()
// Actual SQL: UPDATE `sys_user` SET `deleted_at`=NOW() WHERE `id`=?

// WRONG - manual Update with deleted_at
dao.User.Ctx(ctx).
    Where(do.User{Id: id}).
    Data(do.User{DeletedAt: gtime.Now()}).  // REDUNDANT!
    Update()
```

### Field Type Support

The `deleted_at` field supports multiple types:
- **DateTime/Timestamp**: Default, stores deletion time
- **Integer**: Stores Unix timestamp (seconds)
- **Boolean**: Stores 0/1 for deleted state

### Configuration (Optional)

Time field names can be customized in `config.yaml`:
```yaml
database:
  default:
    createdAt: "created_at"   # Custom field name
    updatedAt: "updated_at"
    deletedAt: "deleted_at"
    timeMaintainDisabled: false  # Set true to disable this feature
```

# GoFrame Documentation
Complete GoFrame development resources covering component design, usage, best practices, and considerations: see the full index at [./references/README.MD](./references/README.MD).

# GoFrame Code Examples
Rich practical code examples covering HTTP services, gRPC services, and various project types: see the full index at [./examples/README.MD](./examples/README.MD)
