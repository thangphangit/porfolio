# 🧪 Research Starter Pack — AI Agent Memory & ESG
**Tác giả:** Phan Văn Thắng · thang.phan@mycolor.biz  
**Khởi tạo:** 2026-06-26  
**Dùng cho:** Google NotebookLM — Notebook mới  

---

## 📌 Tên Notebook Gợi Ý
> **"FluxMem × ESG — Nghiên cứu Bộ nhớ AI Agent & Hiệu quả ESG"**

---

## 🎯 Mục Tiêu Nghiên Cứu

Nghiên cứu này hướng đến hai nhánh chính:

### Nhánh 1 — Lý thuyết nền (AI Agent Memory)
Phân tích và tổng hợp framework **FluxMem** — mô hình bộ nhớ tiến hóa liên tục cho LLM Agent,
được đề xuất bởi Fang et al. (2025), Zhejiang University & Alibaba Group.

### Nhánh 2 — Ứng dụng thực tiễn (AI × ESG)
Khảo sát tác động của **AI Capability (AIC)**, **Top Management Support (TMS)**,
và **Innovation Culture (IC)** đến **ESG Performance** thông qua mô hình PLS-SEM.

### Câu hỏi nghiên cứu tổng quát
1. Bộ nhớ tiến hóa liên tục trong AI Agent có thể được ứng dụng vào bối cảnh doanh nghiệp như thế nào?
2. Năng lực AI của tổ chức (AIC) tác động đến hiệu quả ESG theo cơ chế nào?
3. Văn hóa đổi mới (IC) đóng vai trò trung gian hay điều tiết trong mối quan hệ AI–ESG?

---

## 📚 Danh Sách Nguồn Cần Upload (theo thứ tự ưu tiên)

### Ưu tiên 1 — Bắt buộc upload
| # | File | Ghi chú |
|---|------|---------|
| 1 | `Rethinking AI Agent memory.md` | Bài báo chính — FluxMem framework |
| 2 | `RESEARCH_STARTER_NOTEBOOKLM.md` | File này — context tổng thể |

### Ưu tiên 2 — Nên thêm
| # | Nguồn | Cách thêm |
|---|-------|-----------|
| 3 | GitHub: github.com/zjunlp/LightMem | Thêm bằng URL |
| 4 | Export dữ liệu ESG sang .csv | Upload file |

### Ưu tiên 3 — Mở rộng (tìm thêm)
- Các bài báo về Memory-Augmented LLM Agents (Mem0, A-Mem, MemoryOS)
- Tài liệu về ESG framework và đo lường ESG Performance
- Bài báo PLS-SEM methodology

---

## 🔬 Research Gap Đã Xác Định

### Gap 1 — Bộ nhớ tĩnh trong AI Agent
Các hệ thống hiện tại (Zep, Mem0, A-Mem) xem bộ nhớ là **kho lưu trữ tĩnh** với
pipeline truy xuất cứng nhắc. Khi môi trường thay đổi, hệ thống không thể thích nghi,
dẫn đến hai lỗi cốt lõi:
- **Under-connection**: thiếu liên kết quan trọng → agent thiếu context
- **Over-connection**: liên kết thừa → hallucination

### Gap 2 — Kết hợp AI Agent Memory với ESG
Chưa có nghiên cứu nào khảo sát tác động của **khả năng bộ nhớ AI Agent tiến hóa**
đến hiệu quả ESG doanh nghiệp. Đây là khoảng trống mà nghiên cứu này hướng đến.

### Gap 3 — Vai trò của TMS
Trong dữ liệu sơ bộ (N=320), **TMS → ESG** gần như bằng 0 (r=0.007) —
trái với kỳ vọng lý thuyết. Cần khám phá liệu TMS có tác động gián tiếp
thông qua biến trung gian (AIC hoặc IC) hay không.

---

## 📊 Kết Quả Sơ Bộ Từ Dữ Liệu

### Mô hình đo lường (đã xác nhận đạt chuẩn)
| Construct | α | CR | AVE |
|-----------|---|----|-----|
| AIC (AI Capability) | 0.884 | 0.920 | 0.742 |
| TMS (Top Mgmt Support) | 0.893 | 0.926 | 0.757 |
| IC (Innovation Culture) | 0.866 | 0.909 | 0.714 |
| ESG Performance | 0.891 | 0.924 | 0.753 |

### Tương quan construct
- **IC → ESG**: r = 0.501 ✅ Mạnh nhất
- **AIC → ESG**: r = 0.474 ✅ Đáng kể  
- **TMS → ESG**: r = 0.007 ⚠️ Bất thường — cần giải thích

### Giải thích biến: R² ≈ 0.26
Ba biến độc lập giải thích **26% phương sai** của ESG Performance.

---

## 💬 Câu Hỏi Gợi Ý Cho NotebookLM

### Nhóm 1 — Hiểu bài báo FluxMem
```
1. FluxMem giải quyết vấn đề gì mà các hệ thống bộ nhớ trước chưa làm được?
2. Ba giai đoạn tiến hóa của FluxMem là gì? Mô tả chi tiết từng giai đoạn.
3. PEMS (Procedure Evolution Maturity Score) được tính như thế nào?
4. Kết quả thực nghiệm trên GAIA benchmark cho thấy điều gì?
5. Tạo bảng so sánh FluxMem với Mem0, A-Mem, MemoryOS, Zep.
```

### Nhóm 2 — Kết nối lý thuyết với dữ liệu ESG
```
6. Năng lực bộ nhớ AI Agent (FluxMem) có thể đóng góp vào ESG doanh nghiệp như thế nào?
7. Tại sao TMS lại có tương quan gần 0 với ESG? Có lý thuyết nào giải thích không?
8. Đề xuất mô hình nghiên cứu tích hợp AI Agent Memory và ESG Performance.
9. Có nghiên cứu nào về vai trò của Innovation Culture trong áp dụng AI không?
```

### Nhóm 3 — Viết học thuật
```
10. Tóm tắt bài báo FluxMem theo cấu trúc: Background → Gap → Method → Result → Conclusion.
11. Tạo 10 câu hỏi ôn tập dạng trắc nghiệm về nội dung bài báo.
12. Đề xuất tiêu đề và abstract cho bài báo kết hợp FluxMem × ESG.
13. Liệt kê 5 hướng nghiên cứu tương lai dựa trên limitations của FluxMem.
14. Tạo briefing document 1 trang để trình bày với giáo sư hướng dẫn.
```

### Nhóm 4 — Phân tích dữ liệu
```
15. Dựa trên kết quả PLS-SEM sơ bộ, đâu là điểm mạnh và điểm yếu của mô hình?
16. Tại sao AVE > 0.5 và CR > 0.7 là quan trọng trong PLS-SEM?
17. Đề xuất cách cải thiện thang đo TMS để tăng tương quan với ESG.
18. Nếu thêm biến trung gian giữa TMS và ESG, biến đó nên là gì?
```

---

## 🗓️ Kế Hoạch Nghiên Cứu (Roadmap)

```
Tháng 1–2:  Tổng quan tài liệu AI Agent Memory (dùng NotebookLM)
Tháng 3–4:  Phát triển mô hình nghiên cứu tích hợp AI × ESG
Tháng 5–6:  Thu thập dữ liệu thực tế (thay synthetic data)
Tháng 7–8:  Chạy PLS-SEM với SmartPLS, phân tích kết quả
Tháng 9–10: Viết bài báo, submit Q1/Q2 journal
Tháng 11–12: Revise & resubmit
```

---

## 🔗 Tài Nguyên Bổ Sung

- **Code FluxMem**: https://github.com/zjunlp/LightMem
- **Benchmark LoCoMo**: Maharana et al. (2024) — long-context reasoning
- **Benchmark Mind2Web**: Deng et al. (2023) — web navigation
- **Benchmark GAIA**: Mialon et al. (2023) — general AI assistant
- **SmartPLS**: https://www.smartpls.com (PLS-SEM software)
- **NotebookLM**: https://notebooklm.google.com

---

## 📝 Ghi Chú Cá Nhân

> *Thêm ghi chú nghiên cứu của bạn vào đây khi làm việc với NotebookLM...*

---

*File này được tạo tự động · Cập nhật: 2026-06-26 · Phan Văn Thắng*
