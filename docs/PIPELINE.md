# PIPELINE — Clone hồ sơ truyện → branch truyện → batch 10 chương

## 1. Mục tiêu

Pipeline này dùng **hồ sơ giải mã của một truyện có sẵn** làm nguồn tham chiếu để khởi tạo truyện mới. Không bootstrap ý tưởng từ số 0 theo quy trình cũ.

ChatGPT Web chịu trách nhiệm phân tích, chuyển hóa, viết và review. GitHub là bộ nhớ dài hạn và source of truth.

Mỗi truyện chạy trên **một branch riêng**. `main` chỉ giữ pipeline, prompt và template.

Mục tiêu mặc định:
- truyện dài 200–300 chương;
- tiếng Việt tự nhiên, phù hợp audio YouTube;
- giữ mạnh Narrative DNA, story engine, nhịp tiến triển, cách gieo–thu, kiểu payoff và cấu trúc chức năng của hồ sơ mẫu;
- thay toàn bộ lớp định danh và biểu hiện cụ thể để truyện mới có canon riêng;
- có thể viết **batch 10 chương trong một lệnh**, nhưng phải xử lý tuần tự để continuity không vỡ.

---

## 2. Nguyên tắc clone

### 2.1. Những gì được giữ gần hồ sơ mẫu

Ưu tiên bảo toàn **chức năng**, không sao chép câu chữ:
- Narrative DNA và central fantasy ở cấp chức năng;
- story engine;
- tỷ lệ pha trộn điều tra / hành động / tu luyện / hài / tình cảm / chính trị;
- nhịp mở câu hỏi → điều tra → trả giá → payoff → mở tầng mới;
- cấu trúc tăng stakes;
- cadence reveal, hook và cliffhanger;
- vai trò chức năng của arc;
- nhịp progression;
- cơ chế giữ chân;
- style profile ở cấp nhịp câu, mật độ thoại, khoảng cách POV, cách đưa lore, cách mở/đóng cảnh;
- theme ở cấp câu hỏi đạo đức và hệ thưởng–phạt.

### 2.2. Những gì bắt buộc remap

Mọi truyện mới phải có namespace riêng. Bắt buộc thay hoặc thiết kế lại:
- tên nhân vật, biệt hiệu, danh xưng;
- quốc gia, châu, thành, huyện, núi, sông, bí cảnh, không gian siêu nhiên;
- tông môn, gia tộc, cơ quan, tổ chức, phe phái;
- pháp bảo, vũ khí, đan dược, tài nguyên;
- công pháp, kỹ năng, cảnh giới và thuật ngữ;
- nghi lễ, biểu tượng, mỹ học siêu nhiên;
- tên sự kiện lịch sử;
- câu thoại, câu ví von, biệt ngữ và running joke.

Không dùng thao tác “search & replace tên” đơn thuần.

### 2.3. Giữ cốt truyện nhưng không thành bản đổi tên

Mặc định giữ **macro plot function** gần mẫu, nhưng thay **concrete causality**.

Có thể giữ:
- thứ tự chức năng lớn của các arc;
- vị trí tương đối của reveal, setback, midpoint, climax;
- kiểu tăng phạm vi xung đột;
- vai trò cảm xúc của một beat;
- thời điểm tương đối của power-up hoặc payoff.

Phải chuyển hóa:
- nguyên nhân trực tiếp của vụ việc;
- hình thức nạn nhân và vật chứng;
- phương pháp điều tra/giải quyết;
- quan hệ nhân vật tạo ra lựa chọn;
- cơ chế sức mạnh dùng trong cao trào;
- hình thức payoff;
- chuỗi nhân quả nối arc.

Mục tiêu là **fidelity cao ở cấu trúc chức năng, khoảng cách cao ở biểu hiện cụ thể**.

### 2.4. Cách hành văn

Học từ hồ sơ mẫu ở cấp kỹ thuật:
- POV và narrative distance;
- tốc độ câu/đoạn;
- mật độ thoại;
- tỷ lệ exposition;
- cách đưa luật thế giới sau khi hiện tượng xuất hiện;
- kiểu mở cảnh và đóng cảnh;
- cách viết action, investigation, cultivation, emotion, horror, comedy;
- cách tạo tension bằng đồng hồ, tài nguyên, thông tin bất cân xứng;
- kiểu setup/payoff.

Không sao chép nguyên câu, thành ngữ đặc trưng, câu đe dọa, biệt hiệu, running joke hoặc đoạn mô tả từ nguồn.

---

## 3. Kiến trúc branch

### `main`
Chỉ chứa:
- `docs/`
- `prompts/`
- `templates/`
- hướng dẫn chung.

Không chứa canon của một truyện cụ thể.

### Mỗi truyện
Tạo branch:

```text
story/<slug>
```

Ví dụ:

```text
story/ma-dao-ky-an
story/kiem-tien-trong-sinh
```

Không ghi dữ liệu của hai truyện vào cùng branch.

---

## 4. Cấu trúc dữ liệu của một story branch

```text
source/
  profile.md

memory/
  clone_map.md
  narrative_dna.md
  story_bible.md
  canon.md
  characters.md
  world.md
  factions.md
  power_system.md
  timeline.md
  relationships.md
  theme.md
  style_guide.md
  outline.md
  current_state.md
  chapter_summaries.md
  open_loops.md

chapters/
  0001.md
  0002.md
  ...
```

`source/profile.md` là hồ sơ mẫu đã cung cấp, không phải canon của truyện mới.

`memory/*.md` mới là canon/source of truth của truyện mới.

---

## 5. Pipeline khởi tạo từ hồ sơ mẫu

### Bước A — Import Profile

Đọc toàn bộ hồ sơ mẫu và xác định các section có sẵn.

Ưu tiên lấy:
1. Narrative DNA
2. Story Bible
3. Characters
4. World
5. Factions
6. Power System
7. Timeline
8. Relationship Map
9. Theme
10. Cách hành văn / Style Profile
11. Outline hoặc timeline kể chuyện theo arc
12. Blueprint có thể tái sử dụng
13. Risk / yếu tố không nên bê nguyên

Nếu hồ sơ thiếu section, ghi `MISSING`; không tự giả định nguồn có dữ liệu.

### Bước B — Clone Map

Tạo `memory/clone_map.md` trước mọi canon khác.

Mỗi yếu tố nguồn phải được xếp vào một trong bốn loại:
- `KEEP_FUNCTION`: giữ chức năng tự sự;
- `ADAPT`: giữ phần lõi nhưng đổi cơ chế biểu hiện;
- `REPLACE`: thay hoàn toàn;
- `DROP`: không dùng.

Clone Map tối thiểu phải có bảng cho:
- protagonist;
- companion / mentor / rival / antagonist;
- địa danh;
- phe phái;
- hệ sức mạnh;
- vật phẩm;
- lịch sử;
- relationship archetype;
- theme;
- arc function;
- signature style technique.

Mỗi dòng ghi rõ `Source → Function → New equivalent → What changes → What stays`.

### Bước C — Identity Remap

Tạo namespace mới trước khi viết canon:
- bảng tên nhân vật;
- bảng địa danh;
- bảng tổ chức;
- bảng vũ khí/pháp bảo;
- bảng công pháp/cảnh giới;
- bảng thuật ngữ;
- bảng sự kiện lịch sử.

Tên mới phải nhất quán và không tái dùng tên nguồn.

### Bước D — Narrative DNA

Sinh `memory/narrative_dna.md` từ hồ sơ mẫu.

Phải khóa:
- premise mới;
- central fantasy;
- genre mix;
- story engine;
- chapter loop;
- arc loop;
- escalation ladder;
- retention formula;
- setup/payoff rules;
- hook/cliffhanger cadence;
- emotional rhythm.

### Bước E — Story Bible

Sinh `memory/story_bible.md`.

Phải khóa:
- premise;
- POV;
- tone;
- scope;
- protagonist limits;
- hard rules;
- mystery layers;
- endgame direction;
- forbidden retcons;
- transformation constraints từ Clone Map.

Sau khi Story Bible pass review, tạo `memory/canon.md` làm manifest canon ngắn gọn.

### Bước F — Clone Characters

Sinh `memory/characters.md`.

Mỗi nhân vật quan trọng cần:
- tên mới;
- function inherited from source;
- role;
- external goal;
- internal need;
- fear / wound / flaw;
- contradiction;
- secret;
- voice;
- knowledge boundary;
- skills/resources;
- relationship hooks;
- development arc;
- source traits intentionally NOT copied.

Không chỉ đổi tên rồi giữ nguyên trauma, nghề, tính cách và mạng quan hệ.

### Bước G — Clone World + Factions + Power System

Sinh riêng:
- `memory/world.md`
- `memory/factions.md`
- `memory/power_system.md`

World phải remap địa lý, chính trị, xã hội, kinh tế, văn hóa, lịch sử và tài nguyên.

Factions phải có mục tiêu, ideology, hierarchy, resources, methods, weakness và conflict matrix riêng.

Power System phải có:
- nguồn sức mạnh;
- thang tiến triển;
- điều kiện breakthrough;
- cost;
- counter;
- resource economy;
- exceptions;
- progression budget theo arc.

### Bước H — Timeline + Relationships + Theme

Sinh:
- `memory/timeline.md`
- `memory/relationships.md`
- `memory/theme.md`

Timeline gồm:
- historical timeline;
- current-story timeline;
- arc timeline.

Relationship Map phải có hướng, trạng thái ban đầu, chuyển biến dự kiến, power balance và secrets.

Theme phải ghi:
- central theme;
- subthemes;
- counter-theme;
- moral questions;
- reward/punishment logic;
- motifs mới.

### Bước I — Style Clone

Sinh `memory/style_guide.md` từ section cách hành văn của hồ sơ mẫu.

Phân biệt hai lớp:

**Giữ:**
- POV/distance;
- sentence rhythm;
- paragraph rhythm;
- dialogue density;
- exposition pattern;
- opening/closing scene pattern;
- action/investigation/emotion technique;
- tension/payoff technique.

**Tạo mới:**
- vocabulary;
- simile bank;
- slang;
- catchphrase;
- running jokes;
- ritual wording;
- signature imagery.

### Bước J — Outline Clone

Sinh `memory/outline.md`.

Không cần bootstrap macro outline từ đầu. Dùng arc/timeline kể chuyện của hồ sơ mẫu làm khung chức năng.

Với mỗi arc nguồn:
1. xác định function;
2. xác định promise;
3. xác định escalation;
4. xác định midpoint/reversal;
5. xác định climax/payoff;
6. tạo arc mới có cùng chức năng nhưng causal chain và biểu hiện mới.

Sau macro outline, lập rolling beats **10–20 chương phía trước**.

### Bước K — Initial State

Khởi tạo:
- `current_state.md` tại chương 0;
- `chapter_summaries.md` rỗng;
- `open_loops.md` từ setup của outline;
- progression budget của batch đầu.

Chỉ sau bước này truyện mới được phép viết chương 1.

---

## 6. Pipeline viết batch 10 chương

Lệnh chuẩn:

```text
Viết batch 10 chương tiếp theo theo pipeline.
```

### 6.1. Context Assembly

Trước batch N..N+9 phải đọc:
1. `narrative_dna.md`
2. `story_bible.md`
3. `canon.md`
4. `current_state.md`
5. arc hiện tại trong `outline.md`
6. beats của 10–20 chương gần nhất/phía trước
7. hồ sơ nhân vật sẽ xuất hiện
8. `world.md`
9. `factions.md` nếu liên quan
10. `power_system.md`
11. `relationships.md`
12. `timeline.md`
13. 5–10 summary gần nhất
14. `open_loops.md`
15. `style_guide.md`

### 6.2. Batch Plan

Trước khi draft, lập plan 10 chương gồm:
- objective;
- opening pressure;
- main conflict;
- reveal;
- cost;
- progression delta;
- relationship delta;
- setup/payoff;
- end hook;
- contribution vào mini-arc 10 chương.

Kiểm tra 10 chương không lặp cùng một hook, cùng một cấu trúc combat hoặc cùng một kiểu reveal.

### 6.3. Draft tuần tự — không song song

Dù user yêu cầu 10 chương trong một lần, phải xử lý nội bộ:

```text
Chương N
→ mini review
→ provisional state delta
→ Chương N+1 đọc delta đó
→ mini review
→ ...
→ Chương N+9
```

Không viết 10 chương độc lập cùng từ một snapshot ban đầu.

### 6.4. Mini Gate sau mỗi chương

Mỗi chương phải pass:
- Canon Gate
- Continuity Gate
- Narrative Gate
- Character Knowledge Gate
- Power Accounting Gate
- Style Gate
- Audio Gate

Nếu fail, sửa ngay trước khi viết chương kế tiếp.

### 6.5. Batch Gate sau chương thứ 10

Audit toàn batch:
- timeline;
- vị trí nhân vật;
- thương tích;
- inventory;
- progression budget;
- relationship drift;
- open loops;
- setup/payoff;
- pacing 10 chương;
- độ đa dạng hook;
- lặp từ/câu/cấu trúc;
- voice drift;
- mức độ bám Narrative DNA;
- nguy cơ trở thành bản đổi tên của nguồn.

Nếu batch fail, sửa các chương liên quan rồi audit lại.

### 6.6. Commit Memory

Chỉ sau khi batch pass:
- lưu 10 chapter final;
- append 10 chapter summaries;
- cập nhật `current_state.md` về cuối chương thứ 10;
- cập nhật `relationships.md` nếu có delta lâu dài;
- cập nhật `timeline.md` nếu có mốc mới;
- cập nhật `open_loops.md`;
- cập nhật progression/inventory;
- cập nhật outline rolling nếu chỉ còn <10 beat phía trước.

---

## 7. Quy tắc continuity cho batch

- Power-up phải có accounting trước/sau.
- Vật phẩm dùng ở chương sau phải tồn tại ở state chương trước.
- Thương tích không tự biến mất.
- Nhân vật không biết fact chưa được học.
- Relationship delta phải tích lũy, không reset theo chương.
- Clock/time limit phải giảm đúng.
- Setup đã đóng không được tự mở lại nếu không có lý do canon.
- Một reveal lớn phải cập nhật nhận thức của các nhân vật liên quan ở những chương sau.

---

## 8. Quy tắc branch

Trước mọi write action:
1. xác nhận đang ở `story/<slug>`;
2. không ghi chapter/canon truyện vào `main`;
3. không dùng memory của branch truyện khác;
4. mọi file mới và update của truyện phải cùng branch;
5. nếu user đổi sang truyện khác, đổi branch trước khi đọc/ghi memory.

Pipeline/templates có thể phát triển trên branch `pipeline/*` rồi merge vào `main`.

---

## 9. Lệnh vận hành đề xuất

### Tạo truyện từ hồ sơ

```text
@GitHub làm việc với repo cuongtobi/novel_maker.
Dùng hồ sơ mẫu tôi cung cấp.
Tạo truyện mới với slug <slug> theo profile-clone pipeline.
Tạo branch story/<slug>.
Clone toàn bộ initial memory, review consistency, chưa viết chương 1.
```

### Viết batch đầu

```text
Viết batch chương 1–10 theo pipeline.
```

### Viết batch tiếp

```text
Viết batch 10 chương tiếp theo.
```

### Audit trước khi tiếp tục

```text
Audit continuity toàn branch hiện tại, sửa memory nếu có mâu thuẫn đã được chapter final xác nhận, rồi mới lập batch kế tiếp.
```

---

## 10. Definition of Done

### Initial clone hoàn tất khi
- branch truyện riêng đã tồn tại;
- profile nguồn được ghi nhận;
- clone_map pass;
- Narrative DNA pass;
- Story Bible pass;
- Characters/World/Factions/Power/Timeline/Relationships/Theme pass;
- Style Guide pass;
- Macro Outline + rolling beats pass;
- current_state tại chương 0 nhất quán;
- không còn tên/địa danh/pháp bảo/thuật ngữ nguồn bị sót ngoài `source/profile.md` hoặc phần đối chiếu trong `clone_map.md`.

### Batch 10 chương hoàn tất khi
- đủ 10 chapter final;
- từng chương pass mini gate;
- toàn batch pass batch gate;
- memory cập nhật đến đúng chapter cuối;
- rolling outline còn tối thiểu 10 beat phía trước hoặc đã được bổ sung.
