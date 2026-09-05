---
title: "Từ điển thuật ngữ — Billing"
draft: false
weight: -1
---

# Từ điển thuật ngữ — Billing

↑ Parent: [MOD-BILLING](/templates/examples/billing-plan-lago-example/)

Glossary này chuẩn hoá các thuật ngữ dùng chung trong Billing module để BA, Dev và QA hiểu cùng một nghĩa khi đọc Feature, Use Case, User Story, Acceptance Criteria và Test Scenario.

| Term | Business Meaning |
|------|------------------|
| Plan | Gói cước hoặc mô hình giá mà khách hàng có thể subscribe. |
| Subscription | Việc một khách hàng đang sử dụng một Plan cụ thể. |
| Charge | Khoản phí phát sinh theo usage hoặc theo cấu hình của Plan. |
| Billable Metric | Đại lượng đo usage dùng để tính phí cho khách hàng. |
| Archived | Trạng thái ngừng bán/ngừng sử dụng cho subscription mới, nhưng vẫn giữ ý nghĩa tham chiếu cho khách hàng hiện tại. |

## Detail blocks

| Field | Value |
|-------|-------|
| ID | TERM-PLAN |
| Term | Plan |
| Business Meaning | Gói cước hoặc mô hình giá mà khách hàng có thể subscribe. |
| Example | "Pro Monthly" là một Plan; khách hàng A subscribe vào Plan đó. |

| Field | Value |
|-------|-------|
| ID | TERM-ARCHIVED |
| Term | Archived |
| Business Meaning | Trạng thái ngừng bán/ngừng sử dụng cho subscription mới, nhưng vẫn giữ ý nghĩa tham chiếu cho khách hàng hiện tại. |
| Example | Plan có active subscription sẽ chuyển sang archived thay vì xoá cứng. |
