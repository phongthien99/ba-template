---
title: "UC-PLAN-001 — Tạo mới một Plan (Create)"
draft: false
---

# UC-PLAN-001 — Tạo mới một Plan (Create)

↑ Parent: [FEAT-PLAN-001](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/)
↓ User Story: [US-PLAN-001](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-001-create/us-plan-001/)
Common: [Field Specification — Plan Form](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/_common/field-spec-plan-form/)

| Field | Value |
|-------|-------|
| ID | UC-PLAN-001 |
| Name | Tạo mới một Plan |
| Parent Feature | FEAT-PLAN-001 |
| Primary Actor | Billing Admin |
| Secondary Actors | — |
| Goal | Tạo ra một Plan hoàn chỉnh, sẵn sàng để khách hàng subscribe. |
| Trigger | Admin chọn "Create new Plan" trong Billing Settings. |
| Preconditions | PRE-01. Admin đã đăng nhập và có quyền quản lý Billing. <br> PRE-02. Ít nhất một Currency hợp lệ đã được cấu hình trong hệ thống. |
| Postconditions | POST-01. Plan mới ở trạng thái "Active", có thể gắn vào Subscription. <br> POST-02. Plan xuất hiện trong danh sách Plan để chọn khi tạo subscription. |
| Main Flow | 1. Admin yêu cầu tạo Plan mới. <br> 2. System hiển thị form cấu hình Plan (xem Field Specification — Common). <br> 3. Admin nhập name, code, chọn billing interval (weekly / monthly / quarterly / yearly). <br> 4. Admin nhập base amount và chọn currency. <br> 5. Admin chọn payment timing: "paid in advance" hoặc "in arrears". <br> 6. Admin (tuỳ chọn) nhập số ngày trial period. <br> 7. Admin xác nhận tạo Plan. <br> 8. System validate và lưu Plan, chuyển trạng thái "Active". |
| Alternate Flows | A1. Admin gắn thêm usage-based charges (billable metric) vào Plan trước khi xác nhận — charges này luôn được tính "in arrears" vì dựa trên consumption đã phát sinh (BR-PLAN-002). <br> A2. Admin đặt trial period — hệ thống chỉ áp dụng trial cho subscription đầu tiên của khách hàng trên Plan này (BR-PLAN-001). |
| Exception Flows | E1. Admin không nhập interval hoặc amount → System từ chối lưu và hiển thị lỗi "Interval and base amount are required". <br> E2. Admin nhập code trùng với Plan đã tồn tại → System từ chối và hiển thị lỗi "Plan code already exists". |
| Related Use Cases | UC-PLAN-002 (Xem danh sách & chi tiết Plan), UC-CHARGE-001 (Gắn Charge vào Plan) |

## Business Rules — riêng của UC này

Các rule dưới đây chỉ áp dụng cho Create, không dùng ở UC nào khác trong Feature này nên không đưa vào `_common/`:

| ID | Description |
|----|-------------|
| BR-PLAN-001 | Trial period chỉ áp dụng cho subscription đầu tiên của khách hàng trên Plan, không áp dụng lại cho các chu kỳ sau. |
| BR-PLAN-002 | Charges theo billable metric luôn bill "in arrears". |
| BR-PLAN-003 | Khi subscription bắt đầu giữa chu kỳ hoặc có upgrade/downgrade, hệ thống tự động tính pro-rata. |

Rule dùng chung với UC khác (field `code`, `interval`, `amount`): xem [Business Rules — Common](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/_common/business-rules/).
