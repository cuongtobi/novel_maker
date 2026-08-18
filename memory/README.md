# Story Memory

Thư mục `memory/` trên mỗi `story/<slug>` branch là bộ nhớ dài hạn của đúng một truyện. Không coi lịch sử chat là nguồn canon và không trộn memory giữa các branch.

## Source vs canon

- `source/profile.md`: hồ sơ mẫu tham chiếu + fidelity anchor.
- `memory/*.md`: dữ liệu/canon của truyện mới.

Pipeline chạy theo **Conservative Clone**. Một cấu trúc từ source có thể được giữ nguyên nếu Clone Map đánh dấu `KEEP_CANON`; không bắt buộc remap toàn bộ thuật ngữ, cảnh giới, sự kiện hoặc lịch sử.

## Fidelity classes

`clone_map.md` dùng:
- `KEEP_FUNCTION`: giữ chức năng tự sự;
- `KEEP_CANON`: giữ nguyên cấu trúc/fact source;
- `ADAPT_MINIMAL`: chỉ đổi phần tối thiểu để tương thích identity mới;
- `REMAP_IDENTITY`: đổi proper noun/lớp định danh, giữ chức năng và plot role;
- `DROP`: chỉ dùng khi source/user yêu cầu bỏ.

## Protected Source Structures

Mặc định không tự thay đổi:
- cảnh giới / realm ladder;
- thứ tự cảnh giới và logic tiến cấp;
- major plot events;
- historical events và historical backbone;
- chronology;
- arc order;
- core mystery ladder;
- progression landmarks;
- major reveal/payoff direction.

Nếu proper noun bên trong các cấu trúc trên buộc phải đổi để đồng bộ identity, chỉ `ADAPT_MINIMAL` phần tên; không đổi chức năng, kết quả, thứ tự hoặc ý nghĩa.

## Genre Fit

Mọi tên mới trong characters/world/factions/items phải phù hợp:
- thời đại;
- văn hóa;
- ontology;
- tone;
- subgenre;
- naming morphology của source profile.

Không đưa naming/aesthetic của một thể loại khác vào chỉ để tạo cảm giác mới.

## File chuẩn

- `clone_map.md`: Source → Function → Fidelity class → New/retained equivalent; chứa Protected Source Structures và Genre Fit notes.
- `narrative_dna.md`: premise, genre/subgenre, central fantasy, story engine, chapter/arc loop, escalation, retention formula, hook cadence, fidelity constraints.
- `story_bible.md`: tone, POV, hard rules, limits, mysteries, endgame, forbidden retcons, protected structures và adaptation budget.
- `canon.md`: manifest canon ngắn gọn, gồm các lock về genre, realm/events/history và plot fidelity.
- `characters.md`: hồ sơ sâu, voice, knowledge boundary, state và development; mặc định giữ archetype/function/core motivation gần source.
- `world.md`: địa lý, lịch sử, xã hội, kinh tế, luật, văn hóa, supernatural ontology; remap proper nouns tối thiểu.
- `factions.md`: mục tiêu, ideology, hierarchy, resources, methods, strengths/weaknesses và conflict matrix; giữ narrative role gần source.
- `power_system.md`: nguồn sức mạnh, realm ladder, cost, counters, resource economy và progression budget; realm ladder mặc định KEEP_CANON.
- `timeline.md`: historical timeline, story time, deadlines và arc timeline; historical backbone/major events mặc định KEEP_CANON.
- `relationships.md`: quan hệ có hướng, trust, debt, leverage, secrets, power balance và delta; giữ relationship function chính gần source.
- `theme.md`: central theme, subthemes, counter-theme, moral questions, reward/punishment và motifs.
- `style_guide.md`: kỹ thuật văn phong học từ profile; câu chữ mới nhưng không drift genre/tone.
- `outline.md`: source arc/event backbone + rolling beats 10–20 chương; adaptation theo minimum necessary change.
- `current_state.md`: trạng thái cuối chapter/batch đã duyệt.
- `chapter_summaries.md`: fact có hậu quả theo chương.
- `open_loops.md`: setup, bí mật, nhiệm vụ, thù oán và payoff chưa đóng.

## Quy tắc cập nhật

1. Chỉ cập nhật memory sau khi chapter hoặc batch đã qua review.
2. Story Bible/canon không được sửa ngầm.
3. Mọi power-up, vật phẩm, thương tích, cooldown, location và relationship delta phải đi vào state phù hợp.
4. Mọi setup có khả năng ảnh hưởng tương lai phải vào `open_loops.md`.
5. Summary chương chỉ giữ fact có hậu quả, không kể lại toàn bộ prose.
6. Khi viết batch 10 chương, draft tuần tự; chapter sau phải đọc provisional delta của chapter trước.
7. Sau batch, `current_state.md` phải phản ánh đúng cuối chương thứ 10, không phải snapshot đầu batch.
8. Nếu memory mâu thuẫn với chapter final đã duyệt, audit phải nêu xung đột; không âm thầm retcon chapter.
9. Nếu memory/outline drift khỏi source profile ở genre, cảnh giới, major events, lịch sử hoặc plot backbone mà không có approved deviation, ưu tiên sửa planning/memory về đúng fidelity lock.
10. `clone_map.md` có thể chứa tên source để đối chiếu; các file canon khác dùng tên mới cho identity đã remap nhưng được phép giữ thuật ngữ/cấu trúc `KEEP_CANON`.
11. Không tự thêm major lore, arc, antagonist, mystery layer, bloodline, system, twist hoặc character history nếu source profile không có căn cứ và user chưa yêu cầu.
12. Không ghi dữ liệu truyện cụ thể vào `main`.