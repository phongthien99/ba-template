---
title: "US-PLAN-003 — Cập nhật thông tin Plan"
draft: false
---

# US-PLAN-003 — Cập nhật thông tin Plan

↑ Parent: [UC-PLAN-003](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-003-update/)
↓ Acceptance Criteria: [AC-PLAN-005](#ac-plan-005) · [AC-PLAN-006](#ac-plan-006)

| Field | Value |
|-------|-------|
| ID | US-PLAN-003 |
| Name | Cập nhật thông tin Plan |
| Parent Use Case | UC-PLAN-003 |
| Story | Là một Billing Admin, tôi muốn chỉnh sửa các field của một Plan đã tồn tại (trừ `code` khi đã có subscription), để điều chỉnh giá/chu kỳ khi cần mà không phá vỡ subscription đang chạy. |
| Related Stories | US-PLAN-001, US-PLAN-004, US-PLAN-005 (Xem chi tiết Plan) |

| INVEST | Đạt? | Justification |
|--------|------|----------------|
| Independent | ✅ | Có thể ship sau Create mà không cần chờ Delete/Archive. |
| Negotiable | ✅ | Danh sách field nào "editable sau khi có subscription" có thể điều chỉnh khi review với Product. |
| Valuable | ✅ | Cho phép sửa sai/điều chỉnh giá mà không cần tạo Plan mới. |
| Estimable | ✅ | Đã có Field Specification quy định rõ field nào editable, dev estimate được. |
| Small | ✅ | Chỉ scope Update, không bao gồm versioning/migration subscription. |
| Testable | ✅ | Có AC-PLAN-005, AC-PLAN-006. |

## Definition of Ready

| Check | Tiêu chuẩn | Đạt? |
|-------|-----------|------|
| Parent | Có Parent Feature hoặc Parent UC | ✅ UC-PLAN-003 |
| Actor | Actor rõ ràng | ✅ Billing Admin |
| Goal | Goal rõ ràng | ✅ Cập nhật thông tin Plan |
| Value | Business value rõ | ✅ Điều chỉnh giá/chu kỳ mà không tạo Plan mới |
| AC | Acceptance Criteria đầy đủ | ✅ AC-PLAN-005, AC-PLAN-006 |
| Business Rules | Rule liên quan đã xác định | ✅ BR-PLAN-004, BR-PLAN-005 (xem [Common](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/_common/business-rules/)) |
| Dependency | Dependency đã xác định | ✅ Cần UC-PLAN-001 (Plan tồn tại) |
| UX | Có design nếu cần | ✅ Wireframe form Update (prefill từ Create) |
| Permission | Role/permission đã rõ | ✅ Chỉ Billing Admin |
| Error/Edge cases | Case quan trọng đã xác định | ✅ E1 (đổi code), E2 (validate field) |
| INVEST | Pass INVEST | ✅ |
| Estimation | Dev có thể estimate | ✅ 3 story points |
| QA Ready | QA có thể viết test scenario | ✅ |

→ **Kết luận: PASS DoR — chuyển sang "Ready for Development".**

## Acceptance Criteria

### AC-PLAN-005 — Từ chối đổi code khi Plan đã có subscription

| Field | Value |
|-------|-------|
| ID | AC-PLAN-005 |
| Parent User Story | US-PLAN-003 |
| Scenario | Từ chối đổi code khi Plan đã có subscription |
| Given | Plan "Pro Monthly" đã từng có ít nhất 1 subscription (kể cả đã huỷ) |
| And | Admin đang ở form Update của Plan này |
| When | Admin sửa trường "code" và nhấn "Save" |
| Then | System từ chối lưu |
| And | System hiển thị lỗi "Cannot change code of a Plan with existing subscriptions". |

### AC-PLAN-006 — Cảnh báo pro-rata khi đổi interval/amount

| Field | Value |
|-------|-------|
| ID | AC-PLAN-006 |
| Parent User Story | US-PLAN-003 |
| Scenario | Cảnh báo pro-rata khi đổi interval/amount của Plan đang có subscription active |
| Given | Plan "Pro Monthly" đang có ít nhất 1 subscription active |
| And | Admin đang ở form Update của Plan này |
| When | Admin sửa "interval" hoặc "amount" và nhấn "Save" |
| Then | System hiển thị cảnh báo "Change will apply pro-rata from next cycle" và yêu cầu xác nhận thêm |
| And | Sau khi Admin xác nhận, System lưu thay đổi |
| And | Subscription hiện tại vẫn dùng pricing cũ tới kỳ renew tiếp theo, invoice kế tiếp áp dụng pro-rata. |
