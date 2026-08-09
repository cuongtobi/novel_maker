# PIPELINE — Truyện tiên hiệp xuyên không hệ thống 200-300 chương

## 1. Mục tiêu

Pipeline này dùng ChatGPT Web làm tác giả/biên tập viên và GitHub làm bộ nhớ dài hạn. Mỗi bước sinh ra artifact rõ ràng để bước sau đọc lại được, không phụ thuộc vào lịch sử chat.

## 2. Các lớp dữ liệu

### Canon bất biến
- premise
- luật thế giới
- hệ thống tu luyện
- luật của hệ thống
- mốc lịch sử
- giới hạn sức mạnh
- bí mật cốt lõi

Lưu ở: `memory/canon.md`

### State hiện tại
- chương hiện tại
- vị trí từng nhân vật
- cảnh giới/tu vi
- thương tích
- vật phẩm đang giữ
- quan hệ đang thay đổi
- nhiệm vụ hệ thống đang mở
- timeline hiện hành

Lưu ở: `memory/current_state.md`

### Character memory
Mỗi nhân vật quan trọng có:
- mục tiêu
- nỗi sợ
- bí mật
- tri thức họ thực sự biết
- quan hệ
- giọng thoại
- trạng thái mới nhất

Lưu ở: `memory/characters.md`

### World memory
- khu vực
- thế lực
- cảnh giới
- luật lệ
- kinh tế/tài nguyên
- địa lý
- lịch sử

Lưu ở: `memory/world.md`

### Outline memory
- mega arc
- arc
- chapter beat
- setup/payoff
- foreshadowing

Lưu ở: `memory/outline.md`

### Episodic memory
Mỗi chương sau khi hoàn tất tạo 1 summary ngắn, chỉ giữ sự kiện có hậu quả.

Lưu ở: `memory/chapter_summaries.md`

### Open loops
Theo dõi:
- bí mật chưa giải
- lời hứa
- vật phẩm chưa dùng
- thù oán
- nhiệm vụ
- foreshadowing
- câu hỏi cốt truyện

Lưu ở: `memory/open_loops.md`

## 3. Kiến trúc 10 bước

### Bước A — Bootstrap
Sinh 3-5 concept khác nhau, chọn 1 concept có hook mạnh và có thể kéo 200-300 chương mà không phụ thuộc padding.

Output:
- logline
- selling point
- protagonist
- xuyên không mechanism
- hệ thống mechanism
- central mystery
- endgame direction

### Bước B — Story Bible
Khóa:
- tone
- POV
- nhịp truyện
- độ dài chương
- logic sức mạnh
- luật hệ thống
- giới hạn protagonist
- romance level
- comedy level
- mức bạo lực
- forbidden tropes
- end-state

### Bước C — World Builder
Tạo thế giới theo chiều dọc và chiều ngang:
- phàm giới → tu chân giới → thượng giới nếu cần
- bản đồ thế lực
- tông môn
- gia tộc
- ma đạo
- yêu tộc
- bí cảnh
- kinh tế tu luyện
- cảnh giới

Không tạo lore chỉ để trang trí. Mỗi yếu tố phải có tác dụng với xung đột hoặc lựa chọn nhân vật.

### Bước D — Character Builder
Tối thiểu:
- protagonist
- 2-4 đồng minh chính
- 2-4 đối thủ dài hạn
- 1 mentor hoặc anti-mentor
- 1 nhân vật tình cảm nếu có
- 3-6 nhân vật chức năng theo arc

Mỗi nhân vật cần desire + fear + contradiction + secret + voice + knowledge boundary.

### Bước E — Macro Outline
Cho 200-300 chương, nên chia 8-12 arc.

Ví dụ 240 chương:
- Arc 1: 1-20
- Arc 2: 21-45
- Arc 3: 46-70
- Arc 4: 71-95
- Arc 5: 96-120
- Arc 6: 121-150
- Arc 7: 151-180
- Arc 8: 181-210
- Arc 9: 211-240

Mỗi arc có:
- mục tiêu
- antagonistic force
- mystery
- power progression
- emotional progression
- midpoint reversal
- climax
- consequence
- hook sang arc tiếp

### Bước F — Chapter Beat Outline
Chỉ outline chi tiết 10-20 chương phía trước, không khóa cứng toàn bộ 300 chương.

Mỗi chương có:
- opening pressure
- objective
- conflict
- revelation
- cost
- state change
- hook

### Bước G — Context Assembly
Trước khi viết chương N, ChatGPT phải đọc:
1. `memory/canon.md`
2. `memory/current_state.md`
3. phần arc hiện hành trong `memory/outline.md`
4. nhân vật xuất hiện trong chương
5. 3-5 summary gần nhất
6. `memory/open_loops.md`

Không đọc toàn bộ truyện trừ khi đang audit continuity lớn.

### Bước H — Draft
Viết chương hoàn chỉnh theo chapter plan.

Yêu cầu:
- scene có mục tiêu và lực cản
- tránh exposition dump
- thoại gắn với tính cách
- không giải thích điều người đọc vừa thấy
- không lặp cảm xúc bằng 3 câu gần nghĩa
- kết thúc bằng tension, revelation, decision hoặc consequence

### Bước I — Review Gate
Một chương chưa được coi là hoàn tất nếu chưa qua 4 cổng:

1. Canon gate
- có phá luật thế giới không?
- có dùng thông tin nhân vật chưa biết không?
- có đổi cảnh giới/vật phẩm sai không?

2. Narrative gate
- chương có mục tiêu?
- có biến đổi trạng thái?
- conflict có thực?
- hook có đáng đọc tiếp?

3. Style gate
- có mẫu câu AI?
- có lạm dụng liệt kê?
- có câu tổng kết thừa?
- thoại có đồng giọng?

4. Audio gate
- câu có quá dài?
- ký hiệu có gây lỗi TTS?
- tên riêng có nhất quán?
- hội thoại có rõ người nói?

Nếu fail, sửa trước khi cập nhật memory.

### Bước J — Memory Update
Sau khi chương pass:
- append summary chương
- cập nhật current_state
- cập nhật character nếu trạng thái thay đổi
- cập nhật open_loops
- đánh dấu setup/payoff đã dùng
- không sửa canon nếu không có quyết định retcon rõ ràng

## 4. Chống quên trong truyện dài

### Rule 1 — Source of truth
GitHub là nguồn sự thật. Chat hiện tại chỉ là workspace tạm thời.

### Rule 2 — Facts before prose
Khi memory và prose mâu thuẫn, phải dừng và xác định fact canon trước khi viết tiếp.

### Rule 3 — Knowledge boundary
Mỗi nhân vật chỉ được hành động dựa trên thông tin họ có.

### Rule 4 — Power accounting
Mỗi lần tăng cảnh giới hoặc nhận skill phải ghi vào current_state.

### Rule 5 — Open-loop accounting
Mỗi setup quan trọng phải vào open_loops. Khi payoff xong phải đánh dấu closed.

### Rule 6 — Periodic audit
Mỗi 10 chương: audit continuity nhẹ.
Mỗi 30 chương: audit arc + progression.
Mỗi arc: audit toàn bộ open loops.

## 5. Chống văn AI

Không thể bảo đảm máy dò AI sẽ coi văn bản là “human”, nhưng pipeline chủ động loại các dấu hiệu văn phong máy móc.

Checklist:
- không mở cảnh bằng mô tả chung chung nếu không có áp lực
- tránh “không chỉ... mà còn...” lặp nhiều
- tránh mọi đoạn đều kết luận đạo lý
- tránh liên tục dùng ba tính từ/trạng từ song song
- tránh nhân vật nói ra điều cả hai đã biết chỉ để giải thích cho độc giả
- thay đổi nhịp câu theo cảnh
- dùng chi tiết cảm giác cụ thể thay vì tính từ trừu tượng
- để nhân vật hiểu sai hoặc bỏ sót thông tin hợp lý
- cho mỗi giọng thoại có từ vựng, nhịp và mức trực tiếp riêng
- không tối ưu mọi câu thành quá bóng bẩy

## 6. Audio YouTube

Sau khi chapter final, tạo bản audio-safe:
- bỏ markdown và tiêu đề kỹ thuật
- giữ tiêu đề chương nếu kênh cần
- đổi ký hiệu khó đọc thành chữ
- chia câu quá dài
- hạn chế dấu ngoặc
- bảo toàn tên riêng
- không thay nội dung truyện

Output đề xuất:
`exports/audio/ch_0001.txt`

Có thể gộp 10-20 chương thành một file để sản xuất video dài.

## 7. Cách vận hành trong ChatGPT Web

Khởi đầu:
> Làm việc với repo cuongtobi/novel_maker. Đọc README và docs/PIPELINE.md. Khởi tạo một truyện mới theo pipeline. Trước mỗi bước hãy đọc memory liên quan trên GitHub, và sau khi tôi duyệt thì lưu artifact vào repo.

Viết chương:
> Làm việc với repo cuongtobi/novel_maker. Viết chương kế tiếp theo pipeline. Đọc canon, current_state, arc outline, characters liên quan, 5 summary gần nhất và open_loops trước khi viết. Sau đó review continuity/style/audio. Nếu pass thì cập nhật memory và lưu chương.

Audit:
> Audit 10 chương gần nhất theo canon, timeline, character knowledge, power progression và open loops. Chỉ sửa memory nếu xác định được lỗi chắc chắn.
