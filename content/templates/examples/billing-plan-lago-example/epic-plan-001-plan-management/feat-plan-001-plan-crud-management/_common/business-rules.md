---
title: "Common — Business Rules (Feature-level)"
draft: false
---

# Common (FEAT-PLAN-001) — Business Rules

↑ Feature: [FEAT-PLAN-001](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/)
Áp dụng cho: [UC-PLAN-001 (Create)](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-001-create/) · [UC-PLAN-003 (Update)](/templates/examples/billing-plan-lago-example/epic-plan-001-plan-management/feat-plan-001-plan-crud-management/uc-plan-003-update/)

Đây là các rule chi phối hành vi của **nhiều hơn 1 Use Case** trong Feature này, nên được đặt ở `_common/` cấp Feature thay vì lặp lại trong từng UC. Rule chỉ áp dụng cho đúng 1 UC thì nằm trong file `_index.md` của UC đó (xem UC-PLAN-002, UC-PLAN-004).

| ID | Description |
|----|-------------|
| BR-PLAN-004 | `code` không được đổi sau khi Plan đã có subscription (kể cả subscription đã huỷ). Áp dụng tại: UC-PLAN-003 (chặn sửa) và ràng buộc field `code` trong Field Specification. |
| BR-PLAN-005 | Đổi `interval`/`amount` chỉ áp dụng pro-rata cho invoice tiếp theo, không hồi tố các invoice đã phát hành. Áp dụng tại: UC-PLAN-003 (Alternate Flow A1). |
