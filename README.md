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
- `prompts/`: prompt cho từng agent.
- `memory/`: dữ liệu truyện dài hạn.
- `templates/`: mẫu file để khởi tạo dự án truyện mới.

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
