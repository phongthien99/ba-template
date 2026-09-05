---
title: "UC-PLAN-002 — Xem danh sách & chi tiết Plan (Read)"
draft: false
---

# UC-PLAN-002 — Xem danh sách & chi tiết Plan (Read)

↑ Parent: [FEAT-PLAN-001](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/)
↓ User Story: [US-PLAN-002 — Xem danh sách (kèm filter & search)](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-002-read/us-plan-002/) · [US-PLAN-005 — Xem chi tiết Plan](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-002-read/us-plan-005/)
Common: [Field Specification — Plan Form](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/_common/field-spec-plan-form/) (để biết field nào cần hiển thị ở trang chi tiết)

| Field | Value |
|-------|-------|
| ID | UC-PLAN-002 |
| Name | Xem danh sách & chi tiết Plan (Read) |
| Parent Feature | FEAT-PLAN-001 |
| Primary Actor | Billing Admin |
| Secondary Actors | — |
| Goal | Xem được toàn bộ Plan hiện có (kèm filter/search) và chi tiết từng Plan để ra quyết định quản lý (sửa/archive/tạo mới). |
| Trigger | Admin mở trang "Plans" trong Billing Settings. |
| Preconditions | PRE-01. Admin đã đăng nhập và có quyền xem Billing. |
| Postconditions | POST-01. Không có thay đổi trạng thái hệ thống (read-only). |
| Main Flow | 1. Admin mở trang "Plans". <br> 2. System hiển thị danh sách Plan: name, code, interval, amount, currency, status. <br> 3. Admin chọn một Plan trong danh sách. <br> 4. System hiển thị đầy đủ chi tiết Plan theo Field Specification. |
| Alternate Flows | A1. Admin lọc danh sách theo status (`active` / `archived`) hoặc tìm theo `code`/`name`. |
| Exception Flows | E1. Chưa có Plan nào được tạo → System hiển thị empty state "No plans yet". |
| Related Use Cases | UC-PLAN-001 (Tạo mới Plan), UC-PLAN-003 (Cập nhật Plan) |

## Business Rules — riêng của UC này

Rule này chỉ áp dụng cho Read, không dùng ở UC nào khác nên không đưa vào `_common/`:

| ID | Description |
|----|-------------|
| BR-PLAN-007 | Plan ở trạng thái `archived` vẫn hiển thị trong danh sách (đánh dấu rõ) nhưng không được chọn khi tạo subscription mới. |
