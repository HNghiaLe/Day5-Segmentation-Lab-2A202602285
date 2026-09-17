# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602285
- Ngày / CVAT local: 17/09/2026 / CVAT local
- Công cụ đã dùng: Polygon, Brush, Eraser (hỗ trợ bởi AI YOLOv8 + Segformer)

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Ảnh đầu tiên, chiếc xe ô tô (car) đỗ ở lề đường bên trái
- Class và quy tắc tôi dùng để chọn biên: Class car. Quy tắc: Vẽ bám sát vỏ kim loại và bánh xe, không lấn xuống phần bóng râm (shadow) in trên mặt đường.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: Gợi ý đôi lúc dính liền 2 xe. Dùng Eraser xóa phần lấn vì mỗi xe phải là 1 instance riêng biệt.
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: Task hard_panoptic và easy_semantic, vùng vỉa hè (sidewalk)
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: Sai lớp và sai biên
- Bằng chứng tôi nhìn thấy: Điểm metric cho sidewalk ở Hard là PQ 0.000. AI nhầm toàn bộ vỉa hè thành đường (road) do màu bê tông nhựa giống nhau.
- Quy tắc và hành động sửa: Quy tắc phân ranh giới dựa vào bó vỉa/bậc thềm chứ không phải màu sắc. Dùng Polygon khoanh lại mép vỉa hè và đổi lớp thành sidewalk.
- Sau sửa đã Save và export lại chưa? Đã Save và export đè lên ZIP cũ

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): Sau sửa thủ công, điểm PQ cho sidewalk đã tăng lên (tổng cũ 52.5/82) / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 1. Bóng cây in trên mặt đường (Easy Semantic) | 1. Là Vegetation do màu tối. 2. Là Road do bản chất bề mặt. | Phân loại theo bản chất của bề mặt vật lý, không bị tác động bởi màu do ánh sáng gây ra. | Quyết định: Vẫn gán lớp road (đường) vì bóng râm không làm đổi bản chất mặt đường. |
| 2. Xe máy bị cột điện che khuất thân (cp5_occlusion) | 1. Vẽ xuyên qua cột điện. 2. Tách làm 2 mảng đứt quãng. | Quy tắc instance: Không vẽ phần bị khuất, nhưng vật bị che vẫn là 1 thực thể. | Quyết định: Vẽ 2 polygon rời rạc phần đầu và đuôi xe, gộp chung 1 ID cho chiếc xe đó. |
| 3. Khe hở nhỏ ở kính xe (cp1_holes) | 1. Dùng tính năng khoét lỗ. 2. Vẽ phủ kín luôn mặt kính. | Quy tắc vật thể: Kính/khe nhỏ nằm gọn bên trong biên vật thể. | Quyết định: Không khoét lỗ, vẽ phủ kín để mask xe không bị rỗng ở giữa. |
