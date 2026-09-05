---
title: "US-PLAN-005 — Xem chi tiết Plan"
draft: false
---

# US-PLAN-005 — Xem chi tiết Plan

↑ Parent: [UC-PLAN-002](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-002-read/)
↓ Acceptance Criteria: [AC-PLAN-011](#ac-plan-011) · [AC-PLAN-012](#ac-plan-012)

| Field | Value |
|-------|-------|
| ID | US-PLAN-005 |
| Name | Xem chi tiết Plan |
| Parent Use Case | UC-PLAN-002 |
| Story | Là một Billing Admin, tôi muốn xem đầy đủ chi tiết cấu hình của một Plan cụ thể, để biết chính xác Plan đó đang định giá/chu kỳ ra sao trước khi quyết định sửa hoặc archive. |
| Related Stories | US-PLAN-002 (Xem danh sách Plan), US-PLAN-003 (Cập nhật Plan) |

| INVEST | Đạt? | Justification |
|--------|------|----------------|
| Independent | ✅ | Chỉ là read-only view; không phụ thuộc việc danh sách có filter/search hay không. |
| Negotiable | ✅ | Bố cục hiển thị chi tiết có thể điều chỉnh khi review UI. |
| Valuable | ✅ | Admin cần xem đầy đủ field trước khi sửa/archive, tránh thao tác nhầm. |
| Estimable | ✅ | Detail view đơn giản, có Field Specification tham khảo. |
| Small | ✅ | Chỉ scope xem chi tiết 1 Plan, không bao gồm danh sách hay sửa/xoá. |
| Testable | ✅ | Có AC-PLAN-011, AC-PLAN-012. |

## Definition of Ready

| Check | Tiêu chuẩn | Đạt? |
|-------|-----------|------|
| Parent | Có Parent Feature hoặc Parent UC | ✅ UC-PLAN-002 |
| Actor | Actor rõ ràng | ✅ Billing Admin |
| Goal | Goal rõ ràng | ✅ Xem chi tiết một Plan cụ thể |
| Value | Business value rõ | ✅ Cần thiết để ra quyết định sửa/archive Plan |
| AC | Acceptance Criteria đầy đủ | ✅ AC-PLAN-011, AC-PLAN-012 |
| Business Rules | Rule liên quan đã xác định | ✅ BR-PLAN-007 (xem UC) |
| Dependency | Dependency đã xác định | ✅ Cần US-PLAN-002 (danh sách) để chọn Plan cần xem |
| UX | Có design nếu cần | ✅ Wireframe trang chi tiết Plan |
| Permission | Role/permission đã rõ | ✅ Chỉ role có quyền xem Billing |
| Error/Edge cases | Case quan trọng đã xác định | ✅ Plan không tồn tại/đã bị xoá cứng (E1) |
| INVEST | Pass INVEST | ✅ |
| Estimation | Dev có thể estimate | ✅ 1 story point |
| QA Ready | QA có thể viết test scenario | ✅ |

→ **Kết luận: PASS DoR — chuyển sang "Ready for Development".**

## Acceptance Criteria

### AC-PLAN-011 — Xem chi tiết Plan thành công

| Field | Value |
|-------|-------|
| ID | AC-PLAN-011 |
| Parent User Story | US-PLAN-005 |
| Scenario | Xem chi tiết Plan thành công |
| Given | Plan "Pro Monthly" tồn tại với đầy đủ field theo Field Specification |
| And | Admin đang ở danh sách Plan |
| When | Admin chọn Plan "Pro Monthly" |
| Then | System hiển thị trang chi tiết gồm đầy đủ: name, code, interval, amount, currency, payment timing, trial period, description, tax rate, status |
| And | Các giá trị hiển thị khớp chính xác với dữ liệu hiện tại của Plan. |

### AC-PLAN-012 — Plan không tồn tại (đã bị xoá cứng)

| Field | Value |
|-------|-------|
| ID | AC-PLAN-012 |
| Parent User Story | US-PLAN-005 |
| Scenario | Truy cập chi tiết một Plan đã bị xoá cứng |
| Given | Plan trước đó đã bị xoá cứng khỏi hệ thống (theo UC-PLAN-004) |
| When | Admin truy cập trực tiếp URL chi tiết của Plan đó |
| Then | System hiển thị thông báo "Plan not found" |
| And | System không hiển thị dữ liệu cũ hoặc trang lỗi không rõ nghĩa. |
