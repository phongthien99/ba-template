---
title: "US-PLAN-001 — Định nghĩa giá & chu kỳ tính phí cho Plan"
draft: false
---

# US-PLAN-001 — Định nghĩa giá & chu kỳ tính phí cho Plan

↑ Parent: [UC-PLAN-001](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-001-create/)
↓ Acceptance Criteria: [AC-PLAN-001](#ac-plan-001) · [AC-PLAN-002](#ac-plan-002)

| Field | Value |
|-------|-------|
| ID | US-PLAN-001 |
| Name | Định nghĩa giá & chu kỳ tính phí cho Plan |
| Parent Use Case | UC-PLAN-001 |
| Story | Là một Billing Admin, tôi muốn định nghĩa billing interval, base amount, currency và payment timing khi tạo Plan, để hệ thống biết chính xác khi nào và bao nhiêu tiền cần charge khách hàng. |
| Related Stories | US-PLAN-002 (Xem danh sách Plan), US-PLAN-005 (Xem chi tiết Plan), US-CHARGE-001 (Gắn billable metric charge vào Plan) |

| INVEST | Đạt? | Justification |
|--------|------|----------------|
| Independent | ✅ | Không phụ thuộc vào việc gắn charges hay trial period; có thể hoàn thành và ship riêng. |
| Negotiable | ✅ | Danh sách interval hỗ trợ (weekly/monthly/...) có thể điều chỉnh khi review với PM. |
| Valuable | ✅ | Là điều kiện tiên quyết để bất kỳ subscription nào được tạo và tính phí. |
| Estimable | ✅ | Form CRUD + validate, đã có schema Plan tham khảo từ Lago; team có thể estimate. |
| Small | ✅ | Chỉ scope phần "định nghĩa giá cơ bản", chưa bao gồm charges/coupon — hoàn thành trong 1 sprint. |
| Testable | ✅ | Có AC rõ ràng (AC-PLAN-001, AC-PLAN-002) để QA viết test case. |

## Definition of Ready

| Check | Tiêu chuẩn | Đạt? |
|-------|-----------|------|
| Parent | Có Parent Feature hoặc Parent UC | ✅ UC-PLAN-001 |
| Actor | Actor rõ ràng | ✅ Billing Admin |
| Goal | Goal rõ ràng | ✅ Định nghĩa giá & chu kỳ tính phí |
| Value | Business value rõ | ✅ Điều kiện tiên quyết để subscribe & charge |
| AC | Acceptance Criteria đầy đủ | ✅ AC-PLAN-001, AC-PLAN-002 |
| Business Rules | Rule liên quan đã xác định | ✅ BR-PLAN-001, BR-PLAN-002 (xem UC) |
| Dependency | Dependency đã xác định | ✅ Cần Currency đã cấu hình sẵn (PRE-02) |
| UX | Có design nếu cần | ✅ Wireframe form tạo Plan |
| Permission | Role/permission đã rõ | ✅ Chỉ Billing Admin |
| Error/Edge cases | Case quan trọng đã xác định | ✅ E1, E2 |
| INVEST | Pass INVEST | ✅ |
| Estimation | Dev có thể estimate | ✅ 3 story points |
| QA Ready | QA có thể viết test scenario | ✅ |

→ **Kết luận: PASS DoR — chuyển sang "Ready for Development".**

## Acceptance Criteria

### AC-PLAN-001 — Tạo Plan thành công với thông tin hợp lệ

| Field | Value |
|-------|-------|
| ID | AC-PLAN-001 |
| Parent User Story | US-PLAN-001 |
| Scenario | Tạo Plan thành công với thông tin hợp lệ |
| Given | Admin đang ở form tạo Plan mới |
| And | Admin đã nhập name="Pro Monthly", interval="monthly", amount=49, currency="USD", payment timing="in advance" |
| When | Admin nhấn "Create Plan" |
| Then | System tạo Plan mới ở trạng thái "Active" |
| And | Plan hiển thị trong danh sách Plan |
| And | Plan có thể được chọn khi tạo subscription. |

### AC-PLAN-002 — Từ chối Plan thiếu interval/amount

| Field | Value |
|-------|-------|
| ID | AC-PLAN-002 |
| Parent User Story | US-PLAN-001 |
| Scenario | Từ chối Plan thiếu interval/amount |
| Given | Admin đang ở form tạo Plan mới |
| And | Admin để trống trường "base amount" |
| When | Admin nhấn "Create Plan" |
| Then | System từ chối lưu |
| And | System hiển thị lỗi "Interval and base amount are required" |
| And | Plan không được tạo. |
