---
title: "UC-PLAN-004 — Ngừng sử dụng Plan (Delete/Archive)"
draft: false
---

# UC-PLAN-004 — Ngừng sử dụng Plan (Delete / Archive)

↑ Parent: [FEAT-PLAN-001](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/)
↓ User Story: [US-PLAN-004](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-004-delete-archive/us-plan-004/)

| Field | Value |
|-------|-------|
| ID | UC-PLAN-004 |
| Name | Ngừng sử dụng Plan (Delete / Archive) |
| Parent Feature | FEAT-PLAN-001 |
| Primary Actor | Billing Admin |
| Secondary Actors | — |
| Goal | Ngừng cho phép subscribe mới vào một Plan không còn dùng, mà không ảnh hưởng khách hàng đang subscribe. |
| Trigger | Admin chọn "Delete" trên một Plan. |
| Preconditions | PRE-01. Admin đã đăng nhập và có quyền quản lý Billing. <br> PRE-02. Plan cần xoá đang tồn tại. |
| Postconditions | POST-01. Nếu Plan chưa từng có subscription: Plan bị xoá cứng khỏi hệ thống. <br> POST-02. Nếu Plan đã từng có subscription (kể cả đã huỷ): Plan chuyển status "archived", biến mất khỏi danh sách chọn khi tạo subscription mới, nhưng subscription hiện tại không bị ảnh hưởng. |
| Main Flow | 1. Admin chọn "Delete" trên một Plan. <br> 2. System kiểm tra Plan đã từng gắn với subscription nào chưa. <br> 3. System hiển thị hộp thoại xác nhận, nội dung tuỳ theo kết quả kiểm tra ở bước 2 (xoá cứng hay archive). <br> 4. Admin xác nhận. <br> 5. System thực hiện xoá cứng hoặc archive theo BR-PLAN-006. |
| Alternate Flows | A1. Admin huỷ thao tác ở bước xác nhận → không có thay đổi nào xảy ra. |
| Exception Flows | E1. Plan đang có subscription active và admin chưa xác nhận rõ ràng → System chặn thao tác và hiển thị cảnh báo "This plan is in use by N active subscription(s)". |
| Related Use Cases | UC-PLAN-003 (Cập nhật Plan) |

## Business Rules — riêng của UC này

Rule này chỉ áp dụng cho Delete/Archive, không dùng ở UC nào khác nên không đưa vào `_common/`:

| ID | Description |
|----|-------------|
| BR-PLAN-006 | Plan đã từng có subscription (kể cả đã huỷ) không được xoá cứng — chỉ được chuyển sang `archived`. |
