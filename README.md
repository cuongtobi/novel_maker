# Novel Maker

Pipeline viết tiểu thuyết dài kỳ bằng **ChatGPT Web + GitHub**, khởi tạo truyện mới từ **hồ sơ giải mã của một truyện mẫu** thay vì bootstrap ý tưởng từ số 0.

GitHub đóng vai trò bộ nhớ dài hạn và source of truth.

## Ý tưởng chính

Workflow:

```text
Hồ sơ mẫu
→ Genre/Subgenre Lock
→ Clone Map
→ Protected Source Structures
→ Identity Remap
→ Genre Fit Gate
→ Narrative DNA
→ Story Bible
→ Characters
→ World
→ Factions
→ Power System
→ Timeline
→ Relationships
→ Theme
→ Style Guide
→ Outline Clone
→ Initial State
→ viết chapter hoặc batch 10 chương
→ Source Fidelity + continuity review
→ update memory
```

Pipeline chạy theo **Conservative Clone**: mục tiêu không phải làm truyện khác càng nhiều càng tốt, mà là tạo truyện mới **đúng thể loại, đúng story engine và không lệch quá xa cốt truyện hồ sơ mẫu**. Lớp định danh và câu chữ được làm mới; các cấu trúc cốt lõi được phép giữ nguyên có chủ đích.

## Branch model

`main` chỉ giữ pipeline, prompt và template.

Mỗi truyện dùng một branch riêng:

```text
story/<slug>
```

Khi phát triển pipeline dùng:

```text
pipeline/<feature>
```

Không ghi canon của hai truyện vào cùng branch.

## Cấu trúc story branch

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

`source/profile.md` là reference + fidelity anchor. `memory/*.md` là canon của truyện mới.

## Nguyên tắc clone

### Fidelity trước novelty
Ưu tiên theo thứ tự:
1. genre/subgenre và aesthetic frame;
2. central fantasy và story engine;
3. plot backbone và thứ tự major events;
4. cảnh giới/power ladder và historical backbone;
5. character/relationship/progression/payoff function;
6. identity layer và wording.

Không được hy sinh fidelity chỉ để “sáng tạo hơn”.

### Mặc định giữ
- genre/subgenre;
- Narrative DNA;
- story engine;
- premise;
- arc order;
- event order;
- major reveal/midpoint/climax/payoff;
- causal chain chính;
- protagonist function và core motivation;
- relationship function;
- progression rhythm;
- **cảnh giới, thứ tự cảnh giới và logic tiến cấp**;
- **major story events**;
- **historical backbone, historical events và chronology**;
- endgame direction;
- POV/narrative distance;
- nhịp câu/đoạn;
- mật độ thoại/exposition;
- kỹ thuật action, investigation, horror, cultivation, emotion, comedy.

### Identity Remap — chỉ đổi lớp định danh cần thiết
Mặc định remap:
- tên nhân vật, biệt hiệu, danh xưng riêng;
- proper-noun địa danh;
- proper-noun phe/tông môn/gia tộc/tổ chức;
- proper-noun pháp bảo/vũ khí/vật phẩm khi cần namespace mới;
- catchphrase/running joke;
- câu văn và câu thoại cụ thể.

Mặc định **không remap**:
- cảnh giới;
- major plot events;
- lịch sử nền;
- historical events;
- chronology;
- arc order;
- core mystery ladder;
- progression landmarks.

Nếu proper noun bên trong một cấu trúc protected bắt buộc phải đổi, chỉ `ADAPT_MINIMAL`: đổi phần tên tối thiểu, không đổi chức năng, kết quả, thứ tự hoặc ý nghĩa.

## Genre Fit Gate

Mọi tên mới phải phù hợp đúng:
- thời đại;
- văn hóa;
- ontology;
- tone;
- subgenre;
- naming morphology của hồ sơ mẫu.

Không đưa tên hoặc thuật ngữ của một thể loại khác vào chỉ để tạo cảm giác mới. Tên mới phải nghe như vốn thuộc thế giới của truyện mẫu.

## Character Fidelity

Không tái thiết nhân vật chỉ để khác source.

Mặc định giữ:
- role/archetype;
- core external goal;
- internal need chính;
- major personality axis;
- limits;
- relationship function;
- development direction;
- major secret/reveal nếu nó là một phần của plot backbone.

Không tự thêm trauma, nghề, thân phận, huyết mạch, hệ thống, bí mật, mục tiêu hoặc quan hệ lớn ngoài căn cứ của profile.

## Clone Map

Trước Story Bible phải tạo `memory/clone_map.md`.

Fidelity class:
- `KEEP_FUNCTION`
- `KEEP_CANON`
- `ADAPT_MINIMAL`
- `REMAP_IDENTITY`
- `DROP`

Clone Map phải có riêng mục **Protected Source Structures** cho:
- cảnh giới/realm ladder;
- major events;
- historical backbone;
- chronology;
- arc order;
- core mystery ladder;
- progression landmarks.

## Cách hành văn

Học kỹ thuật từ section **Cách hành văn / Style Profile** trong hồ sơ:
- ngôi kể;
- narrative distance;
- tốc độ;
- mật độ thoại;
- mật độ exposition;
- cách mở/đóng cảnh;
- cách đưa luật thế giới;
- action flow;
- tension;
- setup/payoff.

Câu chữ, dialogue, ví von, catchphrase và wording cụ thể phải được viết mới; nhưng lớp ngôn ngữ mới vẫn phải đúng genre/tone của source.

Không sao chép nguyên câu hoặc đoạn văn từ nguồn.

## Outline

Không bootstrap macro outline trắng và không bắt buộc tạo causal chain mới.

Dùng arc/timeline kể chuyện trong hồ sơ mẫu làm backbone:

```text
source arc
→ preserve event backbone
→ preserve causal chain
→ preserve midpoint/climax/payoff
→ remap identity layer
→ minimal adaptation only if necessary
→ rolling beats 10–20 chương
```

Không tự thêm arc, phản diện lớn, mystery layer, system, bloodline, twist hoặc lịch sử bí mật chỉ để làm truyện khác hơn.

## Viết batch 10 chương

Pipeline hỗ trợ:

```text
Viết batch 10 chương tiếp theo.
```

Nhưng 10 chương **không được draft song song**.

Bắt buộc xử lý:

```text
Chapter N
→ review
→ provisional state delta
→ Chapter N+1 dùng delta đó
→ review
→ ...
→ Chapter N+9
→ batch audit
→ memory commit
```

Sau chapter thứ 10, audit:
- continuity;
- timeline;
- injuries;
- inventory;
- power accounting;
- relationship drift;
- repeated hooks;
- repeated scene skeleton;
- voice drift;
- setup/payoff;
- alignment với Narrative DNA;
- Genre Fit;
- Source Fidelity;
- plot drift;
- over-creation;
- realm/event/history drift ngoài ý muốn.

Chỉ sau khi pass mới cập nhật memory chính thức.

## Lệnh tạo truyện mới

```text
@GitHub làm việc với repo cuongtobi/novel_maker.

Dùng hồ sơ mẫu tôi cung cấp.
Tạo truyện mới với slug <slug> theo profile-clone pipeline.
Tạo branch story/<slug>.

Dùng Conservative Clone:
- giữ đúng genre/subgenre;
- giữ cảnh giới;
- giữ major events;
- giữ lịch sử/chronology;
- giữ plot backbone và causal chain chính;
- Identity Remap chỉ đổi lớp định danh cần thiết;
- mọi tên mới phải pass Genre Fit Gate;
- không tự thêm major lore/arc/twist/nhân vật ngoài profile.

Clone ra đầy đủ:
- Narrative DNA
- Story Bible
- Characters
- World
- Factions
- Power System
- Timeline
- Relationships
- Theme
- Style Guide
- Outline

Tạo Clone Map + Protected Source Structures trước khi khóa canon.
Review cross-file consistency + Source Fidelity.
Chưa viết chương 1.
```

## Viết batch đầu

```text
Viết batch chương 1–10 theo pipeline.
```

## Viết batch tiếp

```text
Viết batch 10 chương tiếp theo.
```

## Audit

```text
Audit continuity + source fidelity branch hiện tại.
Kiểm tra chapter final với toàn bộ memory và source anchors.
Nêu và sửa memory mismatch nếu chapter final đã xác nhận fact.
Kiểm tra genre drift, plot drift, over-creation và protected-structure drift.
Không tự retcon chapter final.
```

## File quan trọng

- `docs/PIPELINE.md`: workflow đầy đủ.
- `prompts/MASTER.md`: master prompt điều phối.
- `templates/profile_clone.template.md`: scaffold clone toàn bộ hồ sơ.
- `templates/style_guide.template.md`: template style clone ở cấp kỹ thuật.
- `templates/outline.template.md`: outline theo source backbone + batch plan.
- `templates/canon.template.md`: canon manifest + protected structures.
- `memory/README.md`: schema memory của mỗi story branch.

## Definition of Done — Initial Clone

Một truyện chỉ được bắt đầu viết khi:
- story branch riêng đã tồn tại;
- source profile được ghi nhận;
- genre/subgenre lock pass;
- Clone Map pass;
- Protected Source Structures được ghi rõ;
- Identity Remap pass Genre Fit Gate;
- Narrative DNA pass;
- Story Bible pass;
- Characters/World/Factions/Power/Timeline/Relationships/Theme pass;
- Style Guide pass;
- Macro Outline + rolling beats pass;
- current_state ở chapter 0 nhất quán;
- cảnh giới, major events, lịch sử và plot backbone không bị thay đổi ngoài adaptation budget;
- không có major lore/arc/twist/character history được thêm chỉ để sáng tạo hơn;
- không sao chép câu chữ/dialogue/catchphrase của source.