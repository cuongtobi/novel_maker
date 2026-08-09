# Novel Maker

Pipeline viết tiểu thuyết Trung Quốc dài kỳ chạy hoàn toàn bằng **ChatGPT Web + GitHub**.

Mục tiêu mặc định:
- Thể loại: tiên hiệp, xuyên không, hệ thống.
- Độ dài: 200-300 chương.
- Ngôn ngữ đầu ra: tiếng Việt tự nhiên, phù hợp truyện audio YouTube.
- Không cần server, database hay API riêng.
- GitHub đóng vai trò bộ nhớ dài hạn và nguồn canon.

## Luồng tổng quát

1. `bootstrap` → tạo ý tưởng, premise và định vị truyện.
2. `story_bible` → khóa luật truyện, tone, POV, pacing, forbidden rules.
3. `world` → thế giới, bản đồ quyền lực, cảnh giới, tài nguyên, tông môn.
4. `characters` → nhân vật, động cơ, quan hệ, bí mật, arc phát triển.
5. `outline` → chia 200-300 chương thành arc và beat theo chương.
6. `chapter_plan` → lập kế hoạch chi tiết cho chương kế tiếp dựa trên memory.
7. `draft` → viết chương hoàn chỉnh.
8. `review` → continuity, logic, pacing, anti-AI-style, audio-readability.
9. `memory_update` → cập nhật canon/state/foreshadowing/summary.
10. `audio_export` → làm sạch văn bản để đưa sang TTS/YouTube.

## Cấu trúc repo

- `docs/PIPELINE.md`: quy trình vận hành đầy đủ.
- `prompts/MASTER.md`: master prompt điều phối toàn bộ pipeline.
- `memory/`: dữ liệu truyện dài hạn.
- `templates/`: mẫu file để khởi tạo dự án truyện mới.

## Cách sử dụng từ đầu

### 1. Bootstrap concept

Mở ChatGPT Web, kết nối GitHub và dùng repo `cuongtobi/novel_maker`.

Prompt gợi ý:

```text
@GitHub làm việc với repo cuongtobi/novel_maker.
Đọc prompts/MASTER.md và docs/PIPELINE.md.

Bắt đầu một bộ truyện mới.
Bootstrap 5 concept tiên hiệp + xuyên không + hệ thống,
hướng tới khoảng 240 chương.

Mỗi concept cần:
- hook mạnh,
- protagonist,
- cơ chế xuyên không,
- cơ chế hệ thống,
- điểm khác biệt,
- bí mật trung tâm,
- hướng endgame.

Chưa ghi canon vào GitHub cho đến khi tôi chọn concept.
```

Chọn một concept hoặc yêu cầu kết hợp hai concept.

### 2. Xây Story Bible

Sau khi chọn concept:

```text
Dùng concept số X.
Xây Story Bible hoàn chỉnh theo pipeline.
Khóa premise, tone, POV, pacing, luật hệ thống,
logic sức mạnh, giới hạn protagonist, romance/comedy level,
forbidden tropes và hướng kết thúc.

Sau khi review xong, lưu canon cần thiết vào GitHub.
```

Story Bible là nền tảng canon. Sau bước này không được tự tiện retcon.

### 3. Xây World

```text
Xây world cho truyện này.
Thiết kế:
- hệ thống cảnh giới,
- địa lý,
- thế lực,
- tông môn,
- gia tộc,
- ma đạo/yêu tộc nếu cần,
- tài nguyên tu luyện,
- bí cảnh,
- kinh tế tu luyện,
- lịch sử có ảnh hưởng trực tiếp tới cốt truyện.

Không tạo lore chỉ để trang trí.
Review xong thì lưu vào memory/world.md.
```

### 4. Xây Characters

```text
Xây hệ thống nhân vật chính cho truyện.
Tối thiểu gồm:
- protagonist,
- 2-4 đồng minh chính,
- 2-4 đối thủ dài hạn,
- mentor hoặc anti-mentor,
- nhân vật tình cảm nếu có,
- nhân vật chức năng cho arc đầu.

Mỗi nhân vật cần:
- desire,
- fear,
- contradiction,
- secret,
- voice,
- knowledge boundary,
- quan hệ,
- hướng phát triển.

Review xong thì lưu vào memory/characters.md.
```

### 5. Lập Macro Outline 200-300 chương

Khuyến nghị mục tiêu đầu tiên: khoảng **240 chương**.

```text
Lập macro outline khoảng 240 chương,
chia thành 8-10 arc.

Mỗi arc cần:
- mục tiêu,
- antagonistic force,
- mystery,
- power progression,
- emotional progression,
- midpoint reversal,
- climax,
- consequence,
- hook sang arc tiếp theo.

Không outline quá chi tiết từng chương ở bước này.
Lưu outline đã review vào memory/outline.md.
```

### 6. Khởi tạo Memory

Sau khi bible, world, characters và macro outline đã ổn:

```text
Khởi tạo toàn bộ memory cho truyện trước chương 1.
Đảm bảo các file sau có dữ liệu phù hợp:
- memory/canon.md
- memory/current_state.md
- memory/characters.md
- memory/world.md
- memory/outline.md
- memory/chapter_summaries.md
- memory/open_loops.md
- memory/style_guide.md
```

GitHub là source of truth. Không dựa vào trí nhớ của chat để thay thế memory.

### 7. Outline rolling 10-20 chương phía trước

Không khóa cứng chi tiết cả 240 chương.

```text
Lập chapter beat chi tiết cho chương 1-15 của Arc 1.

Mỗi chương cần:
- opening pressure,
- objective,
- conflict,
- revelation,
- cost,
- state change,
- hook.

Kiểm tra toàn bộ beat không phá canon và progression.
```

Khi gần hết nhóm chương đã outline, tạo tiếp nhóm kế tiếp dựa trên trạng thái truyện thực tế.

### 8. Viết một chương

Sau khi setup hoàn chỉnh, lệnh hằng ngày có thể rất ngắn:

```text
Viết chương 1 theo pipeline.
```

Hoặc khi mở một chat mới:

```text
@GitHub làm việc với repo cuongtobi/novel_maker.
Đọc prompts/MASTER.md và memory hiện tại.
Tiếp tục viết chương kế tiếp theo pipeline.
```

Trước khi viết chương N, ChatGPT phải đọc:
1. `memory/canon.md`
2. `memory/current_state.md`
3. phần arc hiện tại trong `memory/outline.md`
4. hồ sơ nhân vật xuất hiện trong chương
5. 3-5 summary gần nhất
6. `memory/open_loops.md`
7. `memory/style_guide.md`

Sau đó mới lập chapter plan, kiểm tra canon, viết draft và review.

### 9. Review chương

Một chương chưa hoàn tất nếu chưa qua đủ 4 gate:

**Canon Gate**
- đúng luật thế giới,
- đúng timeline,
- đúng tu vi,
- đúng vật phẩm,
- đúng knowledge boundary.

**Narrative Gate**
- có mục tiêu,
- có conflict thật,
- có state change,
- có consequence,
- hook đủ mạnh.

**Style Gate**
- tránh câu văn máy móc,
- tránh lặp ý,
- tránh exposition dump,
- thoại không đồng giọng,
- hạn chế sáo ngữ và kết luận đạo lý thừa.

**Audio Gate**
- câu đọc TTS trơn tru,
- tên riêng nhất quán,
- ít ký hiệu khó đọc,
- hội thoại rõ người nói.

Nếu fail, phải sửa trước khi coi chương là final.

### 10. Cập nhật Memory sau mỗi chương

Sau khi chương pass review:

```text
Cập nhật memory sau chương vừa hoàn tất.
Chỉ lưu các fact có hậu quả.
Cập nhật current state, character state,
progression, inventory, relationship,
open loops, setup/payoff và chapter summary.
```

Không chép toàn bộ prose vào memory.

### 11. Audit định kỳ

Khuyến nghị:
- mỗi 10 chương: audit continuity nhẹ,
- mỗi 30 chương: audit progression + arc,
- cuối mỗi arc: audit toàn bộ open loops và payoff.

Prompt ví dụ:

```text
Audit continuity từ chương 1-10.
Kiểm tra canon, timeline, tu vi, vật phẩm,
knowledge boundary, open loops và progression.
Không sửa canon nếu chưa xác định rõ lỗi.
```

### 12. Xuất bản audio YouTube

Khi chương đã final:

```text
Xuất bản audio chương 1.
Tạo bản plain text tối ưu cho TTS/YouTube.
Không markdown, không bảng, hạn chế ngoặc và ký hiệu khó đọc.
Giữ tên riêng nhất quán và hội thoại dễ nghe.
```

Có thể yêu cầu theo batch:

```text
Xuất audio chương 1-10 thành văn bản TTS.
```

## Workflow hằng ngày tối giản

Sau khi đã setup truyện, quy trình thực tế có thể chỉ còn:

```text
Viết chương 21 theo pipeline.
```

Sau đó:

```text
Review lại chương 21 và cập nhật memory nếu pass.
```

Khi cần:

```text
Xuất audio chương 21.
```

## Nguyên tắc bộ nhớ

Mỗi chương KHÔNG nạp toàn bộ 200-300 chương trước đó. Chỉ nạp:
- canon cốt lõi,
- state hiện tại,
- outline arc hiện hành,
- 3-5 chương gần nhất,
- entity liên quan trực tiếp tới chương kế tiếp,
- unresolved hooks/foreshadowing.

Như vậy context luôn gọn nhưng continuity vẫn được giữ.

## Quy tắc văn phong

- Ưu tiên câu văn tự nhiên, có nhịp, tránh mẫu câu máy móc.
- Không lạm dụng tổng kết, đối xứng câu, liệt kê ba vế, câu sáo rỗng kiểu AI.
- Mỗi nhân vật có giọng riêng.
- Hành động phải phát sinh từ động cơ và thông tin nhân vật thực sự biết.
- Không tự tiện nâng cấp sức mạnh, thêm bảo vật, nhân vật hoặc lore ngoài canon.
- Chương phải có biến đổi trạng thái rõ ràng và hook cuối chương.
- Mục tiêu là văn phong tự nhiên và có cá tính, không phải đánh lừa công cụ phát hiện AI.

## Audio YouTube

Bản final nên:
- không có markdown,
- không có bảng,
- hạn chế ngoặc,
- câu trung bình 15-35 từ,
- tên riêng nhất quán,
- hội thoại dễ nghe,
- tránh ký hiệu khó đọc với TTS,
- có thể xuất trực tiếp sang `.txt` để đọc bằng VBee hoặc TTS khác.

## Tài liệu chi tiết

Nếu cần hiểu sâu hơn về cách pipeline hoạt động:

- đọc `docs/PIPELINE.md`,
- đọc `prompts/MASTER.md`,
- kiểm tra các template trong `templates/`,
- xem trạng thái truyện hiện hành trong `memory/`.
