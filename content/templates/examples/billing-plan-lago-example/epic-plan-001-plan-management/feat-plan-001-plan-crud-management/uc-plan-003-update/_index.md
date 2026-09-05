---
title: "UC-PLAN-003 — Cập nhật Plan (Update)"
draft: false
---

# UC-PLAN-003 — Cập nhật Plan (Update)

↑ Parent: [FEAT-PLAN-001](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/)
↓ User Story: [US-PLAN-003](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-003-update/us-plan-003/)
Common: [Field Specification — Plan Form](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/_common/field-spec-plan-form/) · [Business Rules — Common](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/_common/business-rules/) (BR-PLAN-004, BR-PLAN-005 — dùng chung với UC-PLAN-001)

| Field | Value |
|-------|-------|
| ID | UC-PLAN-003 |
| Name | Cập nhật Plan (Update) |
| Parent Feature | FEAT-PLAN-001 |
| Primary Actor | Billing Admin |
| Secondary Actors | — |
| Goal | Chỉnh sửa thông tin một Plan đã tồn tại mà không phá vỡ các subscription đang chạy trên Plan đó. |
| Trigger | Admin chọn "Edit" trên một Plan trong danh sách. |
| Preconditions | PRE-01. Admin đã đăng nhập và có quyền quản lý Billing. <br> PRE-02. Plan cần sửa đang tồn tại (bất kỳ status nào). |
| Postconditions | POST-01. Plan được lưu với thông tin mới. <br> POST-02. Subscription hiện tại tiếp tục dùng pricing cũ cho tới kỳ renew tiếp theo; invoice kế tiếp áp dụng pro-rata (BR-PLAN-005). |
| Main Flow | 1. Admin chọn "Edit" trên một Plan. <br> 2. System hiển thị form Update, prefill toàn bộ field hiện tại (theo Field Specification — Common). <br> 3. Admin chỉnh sửa các field được phép sửa. <br> 4. Admin xác nhận lưu. <br> 5. System validate và cập nhật Plan. |
| Alternate Flows | A1. Admin đổi `interval` hoặc `amount` trong khi Plan có subscription active → System cảnh báo "Change will apply pro-rata from next cycle" và yêu cầu xác nhận thêm trước khi lưu (BR-PLAN-005). |
| Exception Flows | E1. Admin sửa `code` trong khi Plan đã có ít nhất 1 subscription (kể cả đã huỷ) → System từ chối lưu, hiển thị lỗi "Cannot change code of a Plan with existing subscriptions" (BR-PLAN-004). <br> E2. Admin nhập `amount` ≤ 0 hoặc bỏ trống field required → System từ chối lưu và hiển thị lỗi tương ứng theo Field Specification. |
| Related Use Cases | UC-PLAN-001 (Tạo mới Plan), UC-PLAN-004 (Ngừng sử dụng Plan) |

## Business Rules

UC này **không có rule riêng** — toàn bộ business rule áp dụng cho Update (BR-PLAN-004, BR-PLAN-005) đã dùng chung với UC-PLAN-001 nên nằm ở [Business Rules — Common](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/_common/business-rules/).
