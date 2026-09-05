---
title: "Requirement Hierarchy Template"
draft: false
weight: 1
---

# Requirement Hierarchy Template

Template này mô tả **cấu trúc phân cấp requirement** (Module → Epic → Feature → Use Case/User Story → Acceptance Criteria → Test Scenario), không bắt buộc mọi User Story phải đi qua Use Case.

Template không gắn với một công cụ cụ thể — có thể triển khai bằng file Markdown (như example trong repo này), trang Confluence, hoặc issue/sub-task trong Jira. Mỗi "item" nói tới trong template (Module, Epic, Feature, Use Case, User Story, AC, Test Scenario) tương ứng với:

| Level | File-based (repo này) | Confluence | Jira |
|-------|------------------------|------------|------|
| Module | thư mục `module-xxx/` + `_index.md` | trang cha | Project hoặc Component |
| Epic | thư mục `epic-xxx/` + `_index.md` | trang con | Epic |
| Feature | thư mục `feat-xxx/` + `_index.md` | trang con | Epic con hoặc Feature label |
| Use Case | thư mục `uc-xxx/` + `_index.md` | trang con | Story (loại "Use Case") hoặc mô tả trong Epic |
| User Story | file `us-xxx.md` | section trong trang, hoặc trang con | Story |
| Acceptance Criteria | section `### AC-XXX` trong cùng file US | section trong cùng trang US | mô tả/AC field trong cùng issue Story (không tách issue riêng) |
| Test Scenario | section hoặc file riêng | trang/section riêng | Test case liên kết (Xray/Zephyr) hoặc sub-task |

Các quy tắc về **ID, Parent/Related, nơi đặt Business Rules, Glossary** áp dụng như nhau bất kể công cụ; chỉ cách "tách file" hay "tách issue/trang" là khác nhau theo công cụ.

```
Module  ──────────────►  Business Goal
  ↓
Epic (Feature Set)
  ↓
Feature ──────────────► Business Rule
  ├───────────────┐
  ↓               ↓
Use Case      User Story
  ↓               │
User Story ◄──────┘
  ↓
Acceptance Criteria
  ↓
Test Scenario
```

## Cách sử dụng

- Bắt đầu từ **Module**, sau đó tạo **Epic (Feature Set)**.
- **Business Goal luôn gắn 1-1 với Module**: mỗi Module bắt buộc phải khai báo field **Business Goal** riêng (mục tiêu nghiệp vụ tổng của cả module), không được bỏ trống hay chỉ khai báo ở cấp Epic — Business Goal của Epic chỉ là mục tiêu con, cụ thể hoá Business Goal của Module.
- Xem **Epic** như một **Feature Set**: nhóm nhiều Feature cùng phục vụ một mục tiêu nghiệp vụ lớn hơn.
- Trước khi tạo **Feature**, cần có **Từ điển thuật ngữ** để thống nhất ngôn ngữ nghiệp vụ. Các thuật ngữ quan trọng trong Feature, Rule, AC và Test Scenario phải dùng cùng một nghĩa.
- Sau đó tạo **Feature**, rồi chọn cách phân rã phù hợp: qua **Use Case** hoặc viết **User Story** trực tiếp dưới Feature.
- Xem **Use Case** và **User Story** là hai cách decomposition/representation hợp lệ ở cấp Feature. User Story có thể được sinh ra từ Use Case, hoặc nằm trực tiếp dưới Feature khi không cần UC đầy đủ.
- Mỗi item cần có **ID** và **Parent** để giữ traceability. Field **Related** chỉ dùng cho quan hệ ngang cấp, không dùng thay cho Parent.
- **Acceptance Criteria luôn nằm chung trong cùng item với User Story cha** (không tách thành item riêng — không tách file, không tách trang, không tách issue): mỗi AC là một section riêng, đặt ngay dưới phần Definition of Ready. Lý do: AC là điều kiện hoàn thành của đúng US đó, tách riêng dễ gây lệch version và khó đọc theo mạch US → AC.
- Rule/spec nào dùng chung cho nhiều item con thì đưa vào một chỗ dùng chung (`_common/` nếu là file, trang "Common" nếu là Confluence, mô tả chung ở Epic nếu là Jira) đặt ở tầng cha gần nhất.

## Từ điển thuật ngữ

Từ điển thuật ngữ giúp BA, Dev, QA và stakeholder dùng cùng một ngôn ngữ khi đọc requirement.

**Glossary luôn đặt duy nhất ở một chỗ dùng chung cấp Module** (`_common/glossary.md` nếu là file, một trang Glossary con của trang Module nếu là Confluence), không tạo thêm glossary riêng ở Epic hay Feature. Lý do: thuật ngữ nghiệp vụ cần thống nhất trong toàn Module để tránh một từ có nhiều nghĩa khác nhau giữa các Feature; nếu một thuật ngữ chỉ phát sinh trong 1 Feature, vẫn khai báo nó vào glossary chung của Module thay vì tách lẻ.

| Field | Value |
|-------|-------|
| ID | TERM-XXX |
| Term | |
| Business Meaning | |
| Example | |

| Term | Business Meaning |
|------|------------------|
| TERM-001 | |

## Cấu trúc phân cấp (ví dụ minh hoạ bằng file)

Ví dụ dưới đây minh hoạ containment bằng thư mục/file — nếu dùng Confluence thì thay bằng trang cha/trang con lồng nhau, nếu dùng Jira thì thay bằng Epic/Story/Sub-task liên kết qua field Parent:

```
module-xxx/                                               ← MOD-XXX
├── _index.md                                             (Module)
├── _common/
│   └── glossary.md                                       (thuật ngữ dùng chung toàn Module)
└── epic-xxx/                                             ← EPIC-XXX
    ├── _index.md                                         (Epic / Feature Set)
    └── feat-xxx/                                         ← FEAT-XXX
        ├── _index.md                                     (Feature)
        ├── _common/                                      ← rule/spec dùng chung (không đặt glossary ở đây)
        │   ├── business-rules.md
        │   └── field-spec.md
        ├── us-xxx.md                                     ← optional: direct Feature-level US (kèm AC trong cùng file)
        ├── uc-xxx/                                       ← optional: UC-driven decomposition
        │   ├── _index.md                                 (Use Case)
        │   └── us-xxx.md                                 (User Story + DoR + Acceptance Criteria)
        └── uc-yyy/
            └── ...
```

## Module

| Field | Value |
|-------|-------|
| ID | MOD-XXX |
| Name | |
| Description | |
| Business Goal | |
| Owner | |

↓ Epic: [EPIC-XXX — Epic name](/path/to/epic/)

## Epic (Feature Set)

↑ Parent: [MOD-XXX](/path/to/module/)
↓ Feature: [FEAT-XXX — Feature name](/path/to/feature/)

| Field | Value |
|-------|-------|
| ID | EPIC-XXX |
| Name | |
| Parent Module | MOD-XXX |
| Description | |
| Business Goal | |

> Epic là một Feature Set. Nếu nhiều Feature trong Epic dùng chung rule/spec, đưa rule/spec đó lên `_common/` tại thư mục Epic.

## Feature

↑ Parent: [EPIC-XXX](/path/to/epic/)

↓ Use Cases:
[UC-XXX — Use case name](/path/to/uc/)

↓ Direct User Stories:
[US-XXX — User story name](/path/to/us/)

Common:
[Business Rules — Feature-level](/path/to/feature/_common/business-rules/) ·
[Field Specification](/path/to/feature/_common/field-spec/)

| Field | Value |
|-------|-------|
| ID | FEAT-XXX |
| Name | |
| Parent Epic | EPIC-XXX |
| Description | |
| Scope — In scope | - |
| Scope — Out of scope | - |
| Scope — Assumptions | - |
| Scope — Constraints | - |
| Related Features | FEAT-YYY, FEAT-ZZZ |

## Use Case

↑ Parent: [FEAT-XXX](/path/to/feature/)
↓ User Story: [US-XXX — User story name](/path/to/us/)
Common: [Field Specification](/path/to/feature/_common/field-spec/)

| Field | Value |
|-------|-------|
| ID | UC-XXX |
| Name | |
| Parent Feature | FEAT-XXX |
| Primary Actor | |
| Secondary Actors | |
| Goal | |
| Trigger | |
| Preconditions | PRE-01. <br> PRE-02. |
| Postconditions | POST-01. <br> POST-02. |
| Main Flow | 1. <br> 2. <br> 3. |
| Alternate Flows | A1. <br> A2. |
| Exception Flows | E1. <br> E2. |
| Related Use Cases | UC-YYY, UC-ZZZ |

## Business Rules — riêng của Use Case này

Chỉ đặt rule ở đây nếu rule chỉ áp dụng cho đúng Use Case này. Nếu rule dùng chung cho nhiều UC/US trong cùng Feature, đưa lên `_common/` cấp Feature.

| ID | Description |
|----|-------------|
| BR-XXX | |
| BR-YYY | |

## User Story

### User Story sinh từ Use Case

↑ Parent: [UC-XXX](/path/to/uc/)
↓ Acceptance Criteria: [AC-XXX](#ac-xxx) · [AC-YYY](#ac-yyy) (section bên dưới, cùng file này)

| Field | Value |
|-------|-------|
| ID | US-XXX |
| Name | |
| Parent Use Case | UC-XXX |
| Parent Feature | FEAT-XXX |
| Story | Là một <role>, tôi muốn <goal>, để <benefit>. |
| Related Stories | US-YYY, US-ZZZ |

| INVEST | Đạt? | Justification |
|--------|------|----------------|
| Independent | [ ] | |
| Negotiable | [ ] | |
| Valuable | [ ] | |
| Estimable | [ ] | |
| Small | [ ] | |
| Testable | [ ] | |

### User Story trực tiếp dưới Feature

↑ Parent: [FEAT-XXX](/path/to/feature/)
↓ Acceptance Criteria: [AC-XXX](#ac-xxx) · [AC-YYY](#ac-yyy) (section bên dưới, cùng file này)

| Field | Value |
|-------|-------|
| ID | US-XXX |
| Name | |
| Parent Feature | FEAT-XXX |
| Parent Use Case | N/A |
| Story | Là một <role>, tôi muốn <goal>, để <benefit>. |
| Related Stories | US-YYY, US-ZZZ |

| INVEST | Đạt? | Justification |
|--------|------|----------------|
| Independent | [ ] | |
| Negotiable | [ ] | |
| Valuable | [ ] | |
| Estimable | [ ] | |
| Small | [ ] | |
| Testable | [ ] | |

## Definition of Ready

| Check | Tiêu chuẩn | Đạt? |
|-------|-----------|------|
| Parent | Có Parent Feature hoặc Parent UC | |
| Actor | Actor rõ ràng | |
| Goal | Goal rõ ràng | |
| Value | Business value rõ | |
| AC | Acceptance Criteria đầy đủ | |
| Business Rules | Rule liên quan đã xác định | |
| Dependency | Dependency đã xác định | |
| UX | Có design nếu cần | |
| Permission | Role/permission đã rõ nếu liên quan | |
| Error/Edge cases | Các case quan trọng đã xác định | |
| INVEST | Pass INVEST | |
| Estimation | Dev có thể estimate | |
| QA Ready | QA có thể viết test scenario | |

→ **Kết luận:** PASS / NOT PASS DoR.

## Acceptance Criteria

> Đặt các section AC ngay trong file `us-xxx.md` của User Story cha (không tách file riêng). Mỗi AC là một `###` heading riêng, ví dụ `### AC-XXX` để có thể link neo `#ac-xxx` từ phần `↓ Acceptance Criteria` phía trên.

↑ Parent: US-XXX (cùng file)

| Field | Value |
|-------|-------|
| ID | AC-XXX |
| Parent User Story | US-XXX |
| Scenario | |
| Given | |
| And | |
| When | |
| And | |
| Then | |
| And | |

## Test Scenario

| Field | Value |
|-------|-------|
| ID | TS-XXX |
| Parent AC | AC-XXX |
| Scenario | |
| Test Data | |
| Steps | 1. <br> 2. <br> 3. |
| Expected Result | |
| Priority | High / Medium / Low |
| Type | Functional / Regression / Edge Case |

## Quy ước ID và liên kết

- ID dùng prefix theo level: `MOD-001`, `EPIC-001`, `FEAT-001`, `UC-001`, `US-001`, `AC-001`, `TS-001`.
- `Parent` trỏ đến đúng một parent trực tiếp. User Story có thể trỏ đến `UC-XXX` hoặc `FEAT-XXX`.
- `Related` chỉ dùng cho quan hệ ngang cấp, ví dụ `Related Features: FEAT-002, FEAT-005`.
- Khi tách item thành file/trang/issue riêng, giữ nguyên ID và dùng link lên/xuống như example: `↑ Parent`, `↓ Feature`, `↓ User Story`. Riêng **Acceptance Criteria không tách thành item riêng** — luôn là section (`### AC-XXX`) trong cùng item với User Story cha, link bằng anchor (`#ac-xxx`) hoặc mục tương đương thay vì đường dẫn/issue riêng.
- Chỗ dùng chung (`_common/` nếu là file, trang/section "Common" nếu là Confluence/Jira) đặt ở tầng cha gần nhất của các item dùng chung rule/spec.

## Tiêu chuẩn Use Case

UC nên mô tả **một mục tiêu nghiệp vụ hoàn chỉnh của Actor** khi tương tác với hệ thống, không phải một màn hình, một button hay một API.

| Tiêu chuẩn | Ý nghĩa | Ví dụ |
|-----------|---------|-------|
| Goal-oriented | Có mục tiêu nghiệp vụ rõ ràng | Quản lý thành viên tổ chức |
| Actor-defined | Xác định actor khởi tạo | Organization Admin |
| Clear trigger | Biết điều gì bắt đầu UC | Admin chọn thêm thành viên |
| Preconditions | Điều kiện trước khi chạy | Admin đã đăng nhập và có quyền |
| Main Success Flow | Có happy path từ đầu đến khi đạt goal | Chọn user → cấp license → xác nhận |
| Alternative Flow | Các nhánh nghiệp vụ hợp lệ | User đã tồn tại |
| Exception Flow | Trường hợp không thể tiếp tục | Không còn license |
| Postconditions | Trạng thái hệ thống sau UC | User trở thành member |
| Business Rules linked | Rule phức tạp không nhét vào flow | BR-LIC-003 |
| Traceable | Truy ngược được Feature | FEAT-IAM-002 |
| Testable | QA có thể suy ra scenario | Happy/alternate/exception |
| Implementation-independent | Không mô tả API/DB/component | Không viết `POST /members` |

> **Rule:** 1 UC ≈ 1 Actor Goal.

## Tiêu chuẩn INVEST cho User Story

| Tiêu chí | Ý nghĩa |
|----------|---------|
| **I — Independent** | Story không phụ thuộc chặt vào story khác; có thể phát triển và triển khai riêng lẻ. |
| **N — Negotiable** | Story mô tả mục tiêu, chi tiết triển khai có thể thảo luận thêm. |
| **V — Valuable** | Story mang lại giá trị rõ ràng cho người dùng hoặc khách hàng. |
| **E — Estimable** | Team có đủ thông tin để estimate. |
| **S — Small** | Story đủ nhỏ để hoàn thành trong một sprint/iteration. |
| **T — Testable** | Story có AC rõ ràng để xác nhận đã hoàn thành. |

## Example

Xem bản example đã điền dữ liệu đầy đủ:

→ [`examples/billing-plan-lago-example/`](/templates/examples/billing-plan-lago-example/)

## Tài liệu tham khảo

→ [Tài liệu & phương pháp luận liên quan](/templates/references/)
