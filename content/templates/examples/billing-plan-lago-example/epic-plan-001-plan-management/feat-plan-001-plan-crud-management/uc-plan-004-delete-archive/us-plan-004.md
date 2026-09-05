---
title: "US-PLAN-004 — Ngừng sử dụng (Archive) Plan"
draft: false
---

# US-PLAN-004 — Ngừng sử dụng (Archive) Plan

↑ Parent: [UC-PLAN-004](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-004-delete-archive/)
↓ Acceptance Criteria: [AC-PLAN-007](#ac-plan-007) · [AC-PLAN-008](#ac-plan-008)

| Field | Value |
|-------|-------|
| ID | US-PLAN-004 |
| Name | Ngừng sử dụng (Archive) Plan |
| Parent Use Case | UC-PLAN-004 |
| Story | Là một Billing Admin, tôi muốn ngừng sử dụng (archive) một Plan không còn dùng nữa, để ngăn khách hàng mới subscribe vào Plan đó mà không ảnh hưởng khách hàng hiện tại đang dùng Plan này. |
| Related Stories | US-PLAN-003 |

| INVEST | Đạt? | Justification |
|--------|------|----------------|
| Independent | ✅ | Không phụ thuộc Update; có thể ship độc lập sau Create + Read. |
| Negotiable | ✅ | Ngưỡng xác định "đã từng có subscription" (kể cả đã huỷ) có thể điều chỉnh cùng Product/Legal. |
| Valuable | ✅ | Ngăn Plan lỗi thời tiếp tục được chọn cho khách hàng mới. |
| Estimable | ✅ | Logic rẽ nhánh xoá cứng/archive đã rõ trong BR-PLAN-006. |
| Small | ✅ | Chỉ scope 1 hành động (archive/xoá cứng), không bao gồm bulk-delete. |
| Testable | ✅ | Có AC-PLAN-007, AC-PLAN-008. |

## Definition of Ready

| Check | Tiêu chuẩn | Đạt? |
|-------|-----------|------|
| Parent | Có Parent Feature hoặc Parent UC | ✅ UC-PLAN-004 |
| Actor | Actor rõ ràng | ✅ Billing Admin |
| Goal | Goal rõ ràng | ✅ Ngừng sử dụng Plan |
| Value | Business value rõ | ✅ Ngăn subscribe mới vào Plan lỗi thời |
| AC | Acceptance Criteria đầy đủ | ✅ AC-PLAN-007, AC-PLAN-008 |
| Business Rules | Rule liên quan đã xác định | ✅ BR-PLAN-006 (xem UC) |
| Dependency | Dependency đã xác định | ✅ Cần biết trạng thái subscription của Plan |
| UX | Có design nếu cần | ✅ Confirm dialog (xoá cứng vs archive) |
| Permission | Role/permission đã rõ | ✅ Chỉ Billing Admin |
| Error/Edge cases | Case quan trọng đã xác định | ✅ E1 (Plan đang active subscription) |
| INVEST | Pass INVEST | ✅ |
| Estimation | Dev có thể estimate | ✅ 2 story points |
| QA Ready | QA có thể viết test scenario | ✅ |

→ **Kết luận: PASS DoR — chuyển sang "Ready for Development".**

## Acceptance Criteria

### AC-PLAN-007 — Xoá cứng Plan chưa từng dùng

| Field | Value |
|-------|-------|
| ID | AC-PLAN-007 |
| Parent User Story | US-PLAN-004 |
| Scenario | Xoá cứng Plan chưa từng dùng |
| Given | Plan "Draft Plan" chưa từng được gắn với bất kỳ subscription nào |
| When | Admin nhấn "Delete" và xác nhận |
| Then | System xoá cứng Plan khỏi hệ thống |
| And | Plan không còn xuất hiện trong danh sách Plan. |

### AC-PLAN-008 — Archive Plan đang có subscription active

| Field | Value |
|-------|-------|
| ID | AC-PLAN-008 |
| Parent User Story | US-PLAN-004 |
| Scenario | Archive Plan đang có subscription active |
| Given | Plan "Pro Monthly" đang có ít nhất 1 subscription active |
| When | Admin nhấn "Delete" và xác nhận cảnh báo "This plan is in use by N active subscription(s)" |
| Then | System chuyển Plan sang status "archived" |
| And | Plan biến mất khỏi danh sách chọn khi tạo subscription mới |
| And | Subscription active hiện tại không bị ảnh hưởng. |
