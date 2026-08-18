# Story Memory

Thư mục `memory/` trên mỗi `story/<slug>` branch là bộ nhớ dài hạn của đúng một truyện. Không coi lịch sử chat là nguồn canon và không trộn memory giữa các branch.

## Source vs canon

- `source/profile.md`: hồ sơ mẫu tham chiếu.
- `memory/*.md`: dữ liệu/canon của truyện mới.

Không dùng tên, địa danh, pháp bảo, công pháp hoặc fact của source như canon mới nếu chưa được remap.

## File chuẩn

- `clone_map.md`: bản đồ Source → Function → New equivalent; ghi KEEP_FUNCTION / ADAPT / REPLACE / DROP.
- `narrative_dna.md`: premise, central fantasy, story engine, chapter/arc loop, escalation, retention formula, hook cadence.
- `story_bible.md`: tone, POV, hard rules, limits, mysteries, endgame, forbidden retcons.
- `canon.md`: manifest canon ngắn gọn, trỏ tới các file chuyên biệt.
- `characters.md`: hồ sơ sâu, voice, knowledge boundary, state và development của nhân vật.
- `world.md`: địa lý, lịch sử, xã hội, kinh tế, luật, văn hóa, supernatural ontology.
- `factions.md`: mục tiêu, ideology, hierarchy, resources, methods, strengths/weaknesses và conflict matrix.
- `power_system.md`: nguồn sức mạnh, progression ladder, cost, counters, resource economy và progression budget.
- `timeline.md`: historical timeline, story time, deadlines và arc timeline.
- `relationships.md`: quan hệ có hướng, trust, debt, leverage, secrets, power balance và delta.
- `theme.md`: central theme, subthemes, counter-theme, moral questions, reward/punishment và motifs.
- `style_guide.md`: kỹ thuật văn phong học từ profile + vocabulary/catchphrase/imagery mới của truyện.
- `outline.md`: macro arc chuyển hóa từ function của source + rolling beats 10–20 chương.
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
9. `clone_map.md` có thể giải thích đối chiếu với source; các file canon khác ưu tiên chỉ dùng tên mới.
10. Không ghi dữ liệu truyện cụ thể vào `main`.
