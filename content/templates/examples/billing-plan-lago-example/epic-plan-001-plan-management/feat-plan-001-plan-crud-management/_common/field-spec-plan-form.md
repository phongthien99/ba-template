---
title: "Common — Field Specification: Plan Form"
draft: false
---

# Common (FEAT-PLAN-001) — Field Specification: Plan Form

↑ Feature: [FEAT-PLAN-001](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/)
Dùng bởi: [UC-PLAN-001 (Create)](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-001-create/) · [UC-PLAN-003 (Update)](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-003-update/)

Mọi field xuất hiện trên form Create/Update Plan phải được định nghĩa rõ trước khi giao cho Dev, tránh việc "form có field nhưng không ai biết type/validation là gì".

| Field | Type | Required | Validation / Constraint | Default | Editable sau khi có subscription? | Example |
|-------|------|----------|--------------------------|---------|-----------------------------------|---------|
| `name` | string | Yes | Max 255 ký tự | — | Yes | `Pro Monthly` |
| `code` | string (slug) | Yes | Unique trong hệ thống; chỉ `a-z0-9-_`; max 255 ký tự | — | **No** nếu đã có subscription (BR-PLAN-004) | `pro-monthly` |
| `interval` | enum | Yes | Một trong: `weekly`, `monthly`, `quarterly`, `semiannual`, `yearly` | — | Yes (áp dụng pro-rata, BR-PLAN-005) | `monthly` |
| `amount` | decimal | Yes | > 0; tối đa 2 chữ số thập phân | — | Yes (áp dụng pro-rata, BR-PLAN-005) | `49.00` |
| `currency` | enum (ISO 4217) | Yes | Phải nằm trong danh sách currency hệ thống hỗ trợ | — | Yes | `USD` |
| `payment_timing` | enum | Yes | `in_advance` hoặc `in_arrears` | `in_arrears` | Yes | `in_advance` |
| `trial_period` | integer (days) | No | ≥ 0; chỉ tính bằng ngày | `0` | Yes | `14` |
| `description` | text | No | Max 1000 ký tự | — | Yes | `Gói dành cho khách hàng SME` |
| `tax_rate` | decimal (%) | No | 0–100; nếu để trống thì kế thừa tax mặc định của hệ thống | system default | Yes | `10` |
| `status` | enum | System-managed | `active` / `archived`; không nhập tay khi tạo | `active` | — (chỉ đổi qua [UC-PLAN-004](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-004-delete-archive/)) | `active` |
