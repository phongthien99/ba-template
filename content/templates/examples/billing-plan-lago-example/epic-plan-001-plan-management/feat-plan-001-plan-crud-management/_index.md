---
title: "FEAT-PLAN-001 — Plan CRUD Management"
draft: false
---

# FEAT-PLAN-001 — Plan CRUD Management

↑ Parent: [EPIC-PLAN-001](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/)

↓ Use Cases:
[UC-PLAN-001 — Create](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-001-create/) ·
[UC-PLAN-002 — Read](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-002-read/) ·
[UC-PLAN-003 — Update](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-003-update/) ·
[UC-PLAN-004 — Delete/Archive](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-004-delete-archive/)

**Common (dùng chung cho các UC bên dưới):**
[Field Specification — Plan Form](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/_common/field-spec-plan-form/) ·
[Business Rules — Feature-level](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/_common/business-rules/)

| Field | Value |
|-------|-------|
| ID | FEAT-PLAN-001 |
| Name | Plan CRUD Management |
| Parent Epic | EPIC-PLAN-001 |
| Description | Admin có thể Create / Read / Update / Delete (archive) một Plan: billing interval, base amount, currency, payment timing (in advance / in arrears), trial period, và gắn charges theo billable metric. |
| Scope — In scope | Tạo, xem danh sách, cập nhật, xoá/archive Plan. <br> Quản lý các field cốt lõi của Plan: name, code, interval, amount, currency, trial period, payment timing. <br> Áp dụng validation và business rule dùng chung cho Create/Update. |
| Scope — Out of scope | Tạo hoặc cấu hình Billable Metric/Charge chi tiết. <br> Tính invoice, thu tiền, hoặc xử lý subscription lifecycle. |
| Scope — Assumptions | Admin đã có quyền quản lý Billing. <br> Currency và interval lấy từ danh sách được hệ thống hỗ trợ. |
| Scope — Constraints | Plan đã có active subscription không được xoá cứng. |
| Related Features | FEAT-CHARGE-001 (Charge / Billable Metric Management) |

## Vì sao có `_common/` ở đây

- `field-spec-plan-form` được **UC-PLAN-001 (Create)** và **UC-PLAN-003 (Update)** dùng chung y hệt nhau → đưa vào `_common/` cấp Feature thay vì copy 2 lần.
- `business-rules` (BR-PLAN-004, BR-PLAN-005) chi phối cả hành vi Create lẫn Update của field `code`/`interval`/`amount` → cũng là rule chung cấp Feature.
- Các rule chỉ áp dụng cho đúng 1 UC (vd. BR-PLAN-001, BR-PLAN-002, BR-PLAN-003 chỉ dùng trong Create) thì **không** đưa lên `_common/` — chúng nằm ngay trong file `_index.md` của UC đó, để tránh phải mở nhiều file mới hiểu được 1 UC.
