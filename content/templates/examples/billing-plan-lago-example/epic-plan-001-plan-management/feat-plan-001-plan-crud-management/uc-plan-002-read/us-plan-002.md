---
title: "US-PLAN-002 — Xem danh sách Plan (kèm filter & search)"
draft: false
---

# US-PLAN-002 — Xem danh sách Plan (kèm filter & search)

↑ Parent: [UC-PLAN-002](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-002-read/)
↓ Acceptance Criteria: [AC-PLAN-003](#ac-plan-003) · [AC-PLAN-004](#ac-plan-004) · [AC-PLAN-009](#ac-plan-009) · [AC-PLAN-010](#ac-plan-010)

| Field | Value |
|-------|-------|
| ID | US-PLAN-002 |
| Name | Xem danh sách Plan (kèm filter & search) |
| Parent Use Case | UC-PLAN-002 |
| Story | Là một Billing Admin, tôi muốn xem danh sách các Plan hiện có và có thể filter theo status hoặc tìm theo code/name, để nhanh chóng tìm ra Plan cần thao tác tiếp mà không phải kéo qua toàn bộ danh sách. |
| Related Stories | US-PLAN-001, US-PLAN-003, US-PLAN-005 (Xem chi tiết Plan) |

| INVEST | Đạt? | Justification |
|--------|------|----------------|
| Independent | ✅ | Chỉ là read-only view, không phụ thuộc Create/Update/Delete, và không phụ thuộc US-PLAN-005 (chi tiết). |
| Negotiable | ✅ | Cột hiển thị và tiêu chí filter/search có thể điều chỉnh khi review UI. |
| Valuable | ✅ | Admin cần lọc/tìm nhanh Plan trước khi thao tác tiếp, đặc biệt khi số Plan lớn. |
| Estimable | ✅ | List + filter/search đơn giản, có Field Specification tham khảo. |
| Small | ✅ | Chỉ scope xem danh sách + filter/search, không bao gồm xem chi tiết hay sửa/xoá. |
| Testable | ✅ | Có AC-PLAN-003, AC-PLAN-004, AC-PLAN-009, AC-PLAN-010. |

## Definition of Ready

| Check | Tiêu chuẩn | Đạt? |
|-------|-----------|------|
| Parent | Có Parent Feature hoặc Parent UC | ✅ UC-PLAN-002 |
| Actor | Actor rõ ràng | ✅ Billing Admin |
| Goal | Goal rõ ràng | ✅ Xem danh sách Plan, filter theo status, search theo code/name |
| Value | Business value rõ | ✅ Cần thiết để ra quyết định quản lý Plan |
| AC | Acceptance Criteria đầy đủ | ✅ AC-PLAN-003, AC-PLAN-004, AC-PLAN-009, AC-PLAN-010 |
| Business Rules | Rule liên quan đã xác định | ✅ BR-PLAN-007 (xem UC) |
| Dependency | Dependency đã xác định | ✅ Cần UC-PLAN-001 đã tạo được ít nhất 1 Plan để test |
| UX | Có design nếu cần | ✅ Wireframe list + filter/search bar |
| Permission | Role/permission đã rõ | ✅ Chỉ role có quyền xem Billing |
| Error/Edge cases | Case quan trọng đã xác định | ✅ Empty state (E1), filter/search không match |
| INVEST | Pass INVEST | ✅ |
| Estimation | Dev có thể estimate | ✅ 2 story points |
| QA Ready | QA có thể viết test scenario | ✅ |

→ **Kết luận: PASS DoR — chuyển sang "Ready for Development".**

## Acceptance Criteria

### AC-PLAN-003 — Hiển thị danh sách Plan

| Field | Value |
|-------|-------|
| ID | AC-PLAN-003 |
| Parent User Story | US-PLAN-002 |
| Scenario | Hiển thị danh sách Plan |
| Given | Hệ thống đang có 3 Plan: "Pro Monthly" (active), "Legacy Plan" (archived), "Enterprise Yearly" (active) |
| When | Admin mở trang "Plans" |
| Then | System hiển thị danh sách gồm cả 3 Plan |
| And | Mỗi Plan hiển thị name, code, interval, amount, currency, status |
| And | "Legacy Plan" được đánh dấu rõ là "archived". |

### AC-PLAN-004 — Empty state khi chưa có Plan

| Field | Value |
|-------|-------|
| ID | AC-PLAN-004 |
| Parent User Story | US-PLAN-002 |
| Scenario | Empty state khi chưa có Plan |
| Given | Hệ thống chưa có Plan nào được tạo |
| When | Admin mở trang "Plans" |
| Then | System hiển thị empty state "No plans yet" |
| And | System không hiển thị danh sách trống không rõ nghĩa. |

### AC-PLAN-009 — Filter danh sách Plan theo status

| Field | Value |
|-------|-------|
| ID | AC-PLAN-009 |
| Parent User Story | US-PLAN-002 |
| Scenario | Filter danh sách Plan theo status |
| Given | Hệ thống đang có cả Plan "active" và Plan "archived" |
| And | Admin đang ở trang "Plans" |
| When | Admin chọn filter status = "active" |
| Then | System chỉ hiển thị các Plan có status "active" |
| And | Bộ đếm/kết quả danh sách cập nhật tương ứng. |

### AC-PLAN-010 — Search Plan theo code hoặc name không có kết quả

| Field | Value |
|-------|-------|
| ID | AC-PLAN-010 |
| Parent User Story | US-PLAN-002 |
| Scenario | Search Plan theo code hoặc name |
| Given | Hệ thống đang có Plan "Pro Monthly" (code `pro-monthly`) |
| And | Admin đang ở trang "Plans" |
| When | Admin nhập "pro" vào ô search |
| Then | System hiển thị các Plan có `code` hoặc `name` chứa "pro" (không phân biệt hoa/thường), gồm "Pro Monthly" |
| And | Khi Admin nhập từ khoá không khớp Plan nào, System hiển thị empty state "No plans match your search". |
