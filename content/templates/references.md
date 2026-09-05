---
title: "Tài liệu tham khảo"
draft: false
weight: 2
---

# Tài liệu & phương pháp luận liên quan

Template này là bản tổng hợp/lai ghép từ nhiều phương pháp luận BA/Agile đã có sẵn. Dưới đây là các nguồn liên quan, nhóm theo từng phần của hierarchy trong [Requirement Hierarchy Template](/templates/requirement-hierarchy-template/).

## 1. Toàn bộ hierarchy (Business Goal → Module → Epic → Feature → UC/US → AC)

| Nguồn | Liên quan đến phần nào trong template |
|-------|----------------------------------------|
| **BABOK Guide** (IIBA – International Institute of Business Analysis) | Khung chuẩn quốc tế về requirement classification: Business Requirements → Stakeholder Requirements → Solution Requirements (Functional/Non-functional) → Transition Requirements. Cấu trúc "Business Goal → Module → Epic → Feature" trong template là một biến thể cụ thể hóa của phân tầng này. |
| **ISO/IEC/IEEE 29148** | Chuẩn quốc tế về requirements engineering, định nghĩa cách viết và quản lý requirement có traceability (tương tự phần "Cross-reference / linking convention" trong template). |
| **Requirement Traceability Matrix (RTM)** | Kỹ thuật kinh điển để map ngược từ AC → US → Feature → Business Goal, chính là ý tưởng đằng sau field `Parent`/`Related` trong template. |

## 2. Epic / Feature

| Nguồn | Liên quan đến phần nào trong template |
|-------|----------------------------------------|
| **SAFe (Scaled Agile Framework)** | Định nghĩa rõ Epic → Feature → Story, có tiêu chí riêng cho Epic (Lean Business Case) khá gần với cách template coi Epic là "Feature Set". |
| **Feature-Driven Development (FDD)** | Phương pháp lấy Feature làm đơn vị trung tâm, mỗi Feature có scope/business value rõ ràng — liên quan tới phần "Scope: In/Out scope, Assumptions, Constraints" trong block Feature. |

## 3. Use Case

| Nguồn | Liên quan đến phần nào trong template |
|-------|----------------------------------------|
| **Alistair Cockburn – "Writing Effective Use Cases" (2000)** | Nguồn gốc trực tiếp của toàn bộ block UC trong template: Actor, Trigger, Precondition/Postcondition, Main Success Scenario, Extensions (= Alternate/Exception Flow ở đây). Cockburn cũng nhấn mạnh nguyên tắc "goal-level" giống hệt câu "1 UC ≈ 1 Actor Goal" trong tài liệu. |
| **UML Use Case Diagram (OMG UML spec)** | Chuẩn hóa cách biểu diễn Actor-System interaction, dù template này chỉ dùng phần text specification, không dùng diagram. |

## 4. User Story & INVEST

| Nguồn | Liên quan đến phần nào trong template |
|-------|----------------------------------------|
| **Mike Cohn – "User Stories Applied" (2004)** | Nguồn gốc format "As a … I want … so that …". |
| **Bill Wake – bài viết gốc đề xuất INVEST (2003)** | Chính là 6 tiêu chí Independent/Negotiable/Valuable/Estimable/Small/Testable được dùng nguyên trong template. |
| **Jeff Patton – "User Story Mapping" (2014)** | Kỹ thuật sắp xếp User Story theo luồng hành trình người dùng, hữu ích nếu cần mở rộng template sang dạng visual mapping thay vì chỉ liệt kê phẳng. |

## 5. Definition of Ready / Definition of Done

| Nguồn | Liên quan đến phần nào trong template |
|-------|----------------------------------------|
| **Scrum Guide (Ken Schwaber & Jeff Sutherland)** | Khái niệm "Definition of Ready" không nằm chính thức trong Scrum Guide (vốn chỉ có DoD), nhưng được cộng đồng Scrum mở rộng thêm và dùng phổ biến — đúng như cách template áp dụng. |
| **Roman Pichler – các bài viết về Product Backlog Refinement** | Nguồn tham khảo tốt cho tiêu chí DoR cụ thể (Value, Estimation, Dependency…). |

## 6. Acceptance Criteria (Given/When/Then)

| Nguồn | Liên quan đến phần nào trong template |
|-------|----------------------------------------|
| **BDD (Behavior-Driven Development) – Dan North** | Nguồn gốc cú pháp Given/When/Then trong block AC. |
| **Gherkin syntax (Cucumber)** | Chuẩn hóa Given/When/Then thành ngôn ngữ có thể parse tự động, biến AC thành executable spec — mở rộng tự nhiên nếu muốn AC "chạy được" như automation test. |

## 7. Business Rules

| Nguồn | Liên quan đến phần nào trong template |
|-------|----------------------------------------|
| **Business Rules Manifesto** (Business Rules Group) | Phương pháp tách Business Rule ra khỏi Use Case/Story (đúng như template đã làm với field "Business Rules: BR-XXX"), tránh nhét logic phức tạp vào flow. |
| **Barbara von Halle – "Business Rules Applied"** | Cùng nguồn gốc phương pháp luận tách Business Rule như trên. |

## 8. Ưu tiên hóa (chưa có trong template hiện tại)

| Nguồn | Liên quan đến phần nào trong template |
|-------|----------------------------------------|
| **MoSCoW (Must/Should/Could/Won't)** | Nếu cần thêm cột "Priority" vào Overview table, đây là phương pháp phổ biến để bổ sung. |
| **RICE / WSJF (SAFe)** | Phương pháp ưu tiên hóa định lượng hơn, thay thế/bổ sung cho MoSCoW khi cần so sánh nhiều item. |
