# PIPELINE — Clone hồ sơ truyện → branch truyện → batch 10 chương

## 1. Mục tiêu

Pipeline này dùng **hồ sơ giải mã của một truyện có sẵn** làm nguồn tham chiếu để khởi tạo truyện mới. Không bootstrap ý tưởng từ số 0 theo quy trình cũ.

ChatGPT Web chịu trách nhiệm phân tích, chuyển hóa, viết và review. GitHub là bộ nhớ dài hạn và source of truth.

Mỗi truyện chạy trên **một branch riêng**. `main` chỉ giữ pipeline, prompt và template.

Mục tiêu mặc định:
- truyện dài 200–300 chương;
- tiếng Việt tự nhiên, phù hợp audio YouTube;
- giữ đúng thể loại/subgenre, thế giới quan, nhịp tiến triển, story engine và xương sống cốt truyện của hồ sơ mẫu;
- dùng chế độ **Conservative Clone**: ưu tiên fidelity với source profile, chỉ thay đổi những gì cần để tạo namespace mới và tránh sao chép câu chữ;
- không sáng tạo thêm arc, lore, nhân vật, cơ chế sức mạnh hoặc biến cố lớn nếu hồ sơ mẫu không cần chúng;
- có thể viết **batch 10 chương trong một lệnh**, nhưng phải xử lý tuần tự để continuity không vỡ.

---

## 2. Nguyên tắc clone

### 2.1. Fidelity hierarchy

Khi có xung đột giữa “tạo mới” và “bám hồ sơ mẫu”, ưu tiên theo thứ tự:

1. đúng thể loại và subgenre của hồ sơ mẫu;
2. đúng central fantasy và story engine;
3. đúng xương sống cốt truyện, thứ tự biến cố lớn và hướng phát triển nhân vật;
4. đúng hệ sức mạnh/cảnh giới và lịch sử nền;
5. đúng chức năng quan hệ, reveal, progression và payoff;
6. mới đến lớp tên gọi, wording, hình ảnh và chi tiết bề mặt.

Không được hy sinh fidelity chỉ để làm truyện “khác hơn”.

### 2.2. Những gì mặc định phải giữ gần hồ sơ mẫu

Ưu tiên bảo toàn:
- genre/subgenre và cultural/aesthetic frame;
- Narrative DNA và central fantasy;
- story engine;
- tỷ lệ pha trộn điều tra / hành động / tu luyện / hài / tình cảm / chính trị;
- premise và phạm vi xung đột;
- thứ tự chức năng lớn của các arc;
- các biến cố lớn, midpoint, climax, reveal và payoff quan trọng;
- causal chain chính giữa các biến cố nếu không có lý do canon bắt buộc phải sửa;
- protagonist function, core motivation, major personality axis và development direction;
- relationship archetype và vai trò của các quan hệ chính;
- progression rhythm;
- **cảnh giới / realm ladder / cấp bậc sức mạnh**;
- breakthrough logic và progression landmarks;
- **historical backbone, historical events và chronology**;
- hook/cliffhanger cadence;
- emotional rhythm;
- style profile ở cấp kỹ thuật: POV, narrative distance, nhịp câu, mật độ thoại, exposition, cách mở/đóng cảnh.

### 2.3. Identity Remap — chỉ remap lớp định danh cần thiết

Identity Remap không còn có nghĩa là thay toàn bộ world/power/history.

#### Bắt buộc remap theo mặc định
- tên nhân vật, biệt hiệu và danh xưng riêng;
- tên địa danh mang tính proper noun;
- tên tông môn/gia tộc/tổ chức/phe phái mang tính proper noun;
- tên pháp bảo, vũ khí, vật phẩm và tài nguyên mang tính proper noun khi cần tạo namespace riêng;
- catchphrase, running joke, câu thoại và câu văn cụ thể;
- wording mô tả mang tính đặc trưng của source.

#### Mặc định KHÔNG remap
- **cảnh giới, thứ tự cảnh giới và logic tiến cấp**;
- **sự kiện lớn của cốt truyện**;
- **lịch sử nền và trục thời gian lịch sử**;
- thứ tự arc;
- midpoint/climax/payoff function;
- core mystery ladder;
- progression landmarks;
- causal chain chính nếu việc giữ lại không tạo mâu thuẫn với namespace mới.

Chỉ thay các phần trên khi user yêu cầu rõ hoặc khi một tên proper noun bên trong bắt buộc phải đồng bộ với identity mới. Nếu phải sửa, dùng **minimal adaptation**: thay ít nhất có thể và không làm đổi vai trò, kết quả, thứ tự hay ý nghĩa của biến cố.

### 2.4. Genre Fit Gate cho mọi tên mới

Mọi tên được remap phải thuộc đúng ngôn ngữ thẩm mỹ của hồ sơ mẫu.

Trước khi khóa tên mới phải kiểm tra:
- thời đại;
- văn hóa;
- địa lý;
- hệ thống xã hội;
- tông tu luyện / huyền huyễn / đô thị / mạt thế / lịch sử / khoa huyễn... của source;
- naming morphology và register mà source đang dùng.

Không được:
- đưa tên hiện đại/công nghệ vào tiên hiệp cổ phong nếu source không có lớp đó;
- đưa mỹ học Tây phương vào truyện Đông phương nếu hồ sơ không hỗ trợ;
- dùng tên quá hài, quá đời thường hoặc quá khoa trương trái tone;
- tạo thuật ngữ thuộc một subgenre khác chỉ vì nghe “mới”.

Nguyên tắc: **tên mới phải nghe như vốn thuộc thế giới của truyện mẫu**.

### 2.5. Character Fidelity

Không tự tái thiết nhân vật chỉ để khác source.

Mặc định giữ:
- role và narrative function;
- archetype;
- core external goal;
- internal need chính;
- trục tính cách nổi bật;
- giới hạn năng lực;
- relationship function;
- development direction;
- major secret/reveal nếu nó là bộ phận của plot backbone.

Có thể đổi:
- tên;
- biệt hiệu;
- chi tiết bề mặt;
- nghề/chức danh chỉ khi cần tương thích namespace mới và phải là **semantic equivalent** trong cùng thể loại;
- một số chi tiết phụ không ảnh hưởng causal chain.

Không được tự thêm trauma, nghề, quá khứ, bí mật, huyết mạch, hệ thống, thân phận, mục tiêu hoặc mối quan hệ lớn mà source profile không có căn cứ.

### 2.6. Plot Fidelity — không sáng tạo quá mức

Mặc định **giữ cốt truyện gần hồ sơ mẫu**.

Được giữ:
- arc order;
- event order;
- nguyên nhân chính;
- đối tượng xung đột;
- loại thử thách;
- phương pháp giải quyết ở cấp logic;
- reveal order;
- progression timing;
- relationship pressure;
- midpoint/climax/payoff;
- hook sang arc tiếp theo.

Chỉ được adapt khi:
- tên cũ xung đột với namespace mới;
- chi tiết cụ thể không còn hợp lý sau remap;
- continuity bắt buộc phải sửa;
- user yêu cầu thay đổi.

Mọi adaptation phải dùng nguyên tắc **minimum necessary change**.

Không tự tạo:
- arc mới;
- phản diện lớn mới;
- mystery layer mới;
- hệ sức mạnh mới;
- lịch sử bí mật mới;
- twist mới làm đổi hướng truyện;
- character arc mới làm thay chức năng nhân vật.

### 2.7. Cách hành văn

Học từ hồ sơ mẫu ở cấp kỹ thuật:
- POV và narrative distance;
- tốc độ câu/đoạn;
- mật độ thoại;
- tỷ lệ exposition;
- cách đưa luật thế giới;
- kiểu mở cảnh và đóng cảnh;
- cách viết action, investigation, cultivation, emotion, horror, comedy;
- cách tạo tension;
- kiểu setup/payoff.

Không sao chép nguyên câu, đoạn văn, catchphrase, running joke hoặc wording đặc trưng từ nguồn.

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

`source/profile.md` là hồ sơ mẫu tham chiếu.

`memory/*.md` là canon/source of truth của truyện mới, bao gồm cả những cấu trúc source được chủ động giữ nguyên theo Clone Map.

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
13. Risk / yếu tố không nên bê nguyên câu chữ

Nếu hồ sơ thiếu section, ghi `MISSING`; không tự giả định nguồn có dữ liệu.

### Bước B — Clone Map

Tạo `memory/clone_map.md` trước mọi canon khác.

Mỗi yếu tố nguồn dùng một trạng thái:
- `KEEP_FUNCTION`: giữ chức năng và có thể giữ cấu trúc;
- `KEEP_CANON`: giữ nguyên cấu trúc/fact source như cảnh giới, sự kiện, lịch sử khi phù hợp;
- `ADAPT_MINIMAL`: chỉ sửa phần tối thiểu để tương thích identity mới;
- `REMAP_IDENTITY`: đổi proper noun/lớp định danh, giữ chức năng và plot role;
- `DROP`: chỉ dùng khi source profile tự đánh dấu không nên kế thừa hoặc user yêu cầu.

Clone Map tối thiểu phải bao phủ:
- protagonist và core cast;
- major locations;
- factions;
- power system;
- realm ladder;
- key artifacts/resources;
- major plot events;
- historical backbone;
- relationship archetypes;
- themes;
- arc functions;
- style techniques.

Mỗi dòng ghi rõ:

```text
Source element
→ Narrative function
→ Fidelity class
→ New/retained equivalent
→ What stays
→ Minimal changes allowed
→ Genre-fit note
```

### Bước C — Identity Remap

Tạo namespace mới trước khi viết canon:
- bảng tên nhân vật;
- bảng địa danh proper noun;
- bảng tổ chức/phe;
- bảng pháp bảo/vũ khí/vật phẩm cần đổi tên;
- bảng thuật ngữ cần đổi tên.

Tách riêng danh sách **Protected Source Structures**:
- cảnh giới/realm ladder;
- major plot events;
- historical events;
- chronology;
- arc order;
- core mystery ladder;
- progression landmarks.

Các cấu trúc protected mặc định giữ nguyên.

Mỗi tên mới phải pass Genre Fit Gate trước khi được dùng ở file canon khác.

### Bước D — Narrative DNA

Sinh `memory/narrative_dna.md` từ hồ sơ mẫu.

Phải khóa:
- premise;
- central fantasy;
- genre/subgenre;
- story engine;
- chapter loop;
- arc loop;
- escalation ladder;
- retention formula;
- setup/payoff rules;
- hook/cliffhanger cadence;
- emotional rhythm;
- fidelity constraints.

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
- protected source structures;
- allowed adaptation budget.

Sau khi Story Bible pass review, tạo `memory/canon.md` làm manifest canon ngắn gọn.

### Bước F — Clone Characters

Sinh `memory/characters.md`.

Mỗi nhân vật quan trọng cần:
- tên mới;
- inherited narrative function;
- source archetype;
- role;
- external goal;
- internal need;
- major personality axis;
- fear/wound/flaw nếu source có;
- secret nếu source có;
- voice;
- knowledge boundary;
- skills/resources;
- relationship hooks;
- development direction;
- remapped surface identity;
- prohibited inventions.

Không tự làm nhân vật “mới hơn” bằng cách thêm trauma, thân phận, hệ thống, huyết mạch hay mục tiêu lớn ngoài profile.

### Bước G — World + Factions + Power System

Sinh riêng:
- `memory/world.md`
- `memory/factions.md`
- `memory/power_system.md`

World ưu tiên giữ ontology, thời đại, logic xã hội và lịch sử nền của source. Remap tên địa danh/phe khi cần nhưng không đổi sang thẩm mỹ của thể loại khác.

Factions giữ narrative role và conflict structure gần source; chỉ đổi identity layer và chi tiết phụ cần thiết.

Power System phải giữ realm ladder/cảnh giới theo source mặc định. Theo dõi:
- nguồn sức mạnh;
- access;
- cảnh giới/grade ladder;
- breakthrough requirement;
- resource economy;
- cost;
- counter;
- exception;
- progression budget.

Không tự thiết kế hệ sức mạnh mới nếu source đã có hệ thống hoàn chỉnh.

### Bước H — Timeline + Relationships + Theme

Sinh:
- `memory/timeline.md`
- `memory/relationships.md`
- `memory/theme.md`

Timeline phải bảo toàn historical backbone và major event order của source theo mặc định.

Relationship Map giữ vai trò và hướng phát triển chính; chỉ thay identity/surface detail nếu cần.

Theme giữ central theme, subtheme và reward/punishment logic gần source; motif ngôn ngữ có thể làm mới nếu không đổi ý nghĩa.

### Bước I — Style Clone

Sinh `memory/style_guide.md` từ section cách hành văn của hồ sơ mẫu.

**Giữ kỹ thuật:**
- POV/distance;
- sentence rhythm;
- paragraph rhythm;
- dialogue density;
- exposition pattern;
- opening/closing scene pattern;
- action/investigation/emotion technique;
- tension/payoff technique.

**Tạo mới ở lớp câu chữ:**
- wording cụ thể;
- câu thoại;
- ví von/ẩn dụ;
- catchphrase/running joke nếu cần;
- signature prose imagery.

Lớp ngôn ngữ mới vẫn phải đúng genre/tone của source.

### Bước J — Outline Clone

Sinh `memory/outline.md`.

Không bootstrap macro outline trắng và không buộc tạo causal chain mới.

Với mỗi arc nguồn:
1. ghi lại source arc function;
2. giữ event backbone và causal chain chính;
3. giữ promise, midpoint, climax, payoff và consequence;
4. remap identity layer;
5. chỉ adapt chi tiết tối thiểu khi tên/world identity mới khiến chi tiết cũ không còn hợp lý;
6. audit genre fit và plot drift.

Sau macro outline, lập rolling beats **10–20 chương phía trước** bám sát timeline/source arc tương ứng.

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
16. fidelity constraints và protected source structures từ `clone_map.md`.

### 6.2. Batch Plan

Trước khi draft, lập plan 10 chương gồm:
- source beat/arc anchor;
- objective;
- opening pressure;
- main conflict;
- reveal;
- cost;
- progression delta;
- relationship delta;
- setup/payoff;
- end hook;
- contribution vào mini-arc 10 chương;
- deviation note nếu có khác source profile.

Mọi deviation lớn phải có lý do canon cụ thể; nếu không có thì quay về source beat.

### 6.3. Draft tuần tự — không song song

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
- **Genre Fit Gate**
- **Source Fidelity Gate**

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
- **genre drift**;
- **plot drift so với source profile**;
- **over-creation: lore/arc/nhân vật/twist mới không có căn cứ**;
- tên gọi mới có đúng thể loại không;
- cảnh giới, major events và historical backbone có bị thay đổi ngoài ý muốn không.

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
- Cảnh giới và progression landmarks không được tự đổi khỏi source profile.
- Major event order không được tự đảo hoặc bỏ.

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
Dùng Conservative Clone: giữ đúng thể loại, cảnh giới, sự kiện, lịch sử và plot backbone.
Identity Remap chỉ đổi lớp định danh cần thiết và mọi tên mới phải pass Genre Fit Gate.
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
Audit continuity + source fidelity toàn branch hiện tại.
Sửa memory nếu có mâu thuẫn đã được chapter final xác nhận.
Kiểm tra genre drift, plot drift và over-creation rồi mới lập batch kế tiếp.
```

---

## 10. Definition of Done

### Initial clone hoàn tất khi
- branch truyện riêng đã tồn tại;
- profile nguồn được ghi nhận;
- Clone Map pass;
- Protected Source Structures đã được ghi rõ;
- Identity Remap pass Genre Fit Gate;
- Narrative DNA pass;
- Story Bible pass;
- Characters/World/Factions/Power/Timeline/Relationships/Theme pass;
- Style Guide pass;
- Macro Outline + rolling beats pass;
- current_state tại chương 0 nhất quán;
- cảnh giới, major events, lịch sử và plot backbone không bị thay đổi ngoài adaptation budget;
- không có lore/arc/nhân vật lớn được thêm chỉ để “sáng tạo hơn”;
- câu chữ và dialogue không sao chép source.

### Batch 10 chương hoàn tất khi
- đủ 10 chapter final;
- từng chương pass mini gate;
- toàn batch pass batch gate;
- không có genre drift hoặc plot drift đáng kể;
- memory cập nhật đến đúng chapter cuối;
- rolling outline còn tối thiểu 10 beat phía trước hoặc đã được bổ sung.