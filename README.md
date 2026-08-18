# Novel Maker

Pipeline viết tiểu thuyết dài kỳ bằng **ChatGPT Web + GitHub**, khởi tạo truyện mới từ **hồ sơ giải mã của một truyện mẫu** thay vì bootstrap ý tưởng từ số 0.

GitHub đóng vai trò bộ nhớ dài hạn và source of truth.

## Ý tưởng chính

Workflow mới:

```text
Hồ sơ mẫu
→ Clone Map
→ Identity Remap
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
→ review
→ update memory
```

Mục tiêu không phải chỉ đổi tên. Pipeline giữ **cái hay ở cấp chức năng** như story engine, nhịp reveal, escalation, progression, payoff và kỹ thuật văn phong; đồng thời tạo canon mới với tên, world, phe, hệ sức mạnh, vật phẩm, causal chain và câu chữ riêng.

## Branch model

`main` chỉ giữ pipeline, prompt và template.

Mỗi truyện dùng một branch riêng:

```text
story/<slug>
```

Ví dụ:

```text
story/ma-dao-ky-an
story/kiem-tien-trong-sinh
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

`source/profile.md` là reference. `memory/*.md` mới là canon của truyện mới.

## Nguyên tắc clone

### Giữ ở cấp function
- Narrative DNA;
- story engine;
- genre mix;
- chapter loop / arc loop;
- escalation pattern;
- reveal cadence;
- hook/cliffhanger cadence;
- progression rhythm;
- emotional rhythm;
- setup/payoff technique;
- arc function;
- POV/narrative distance;
- nhịp câu/đoạn;
- mật độ thoại/exposition;
- kỹ thuật action, investigation, horror, cultivation, emotion, comedy.

### Bắt buộc remap
- tên nhân vật;
- địa danh;
- quốc gia/thế lực;
- tổ chức/tông môn/gia tộc;
- pháp bảo/vũ khí;
- công pháp/cảnh giới;
- tài nguyên;
- nghi lễ/mỹ học;
- sự kiện lịch sử;
- slang/catchphrase/running joke;
- câu văn và câu thoại.

### Cốt truyện
Giữ macro plot function gần hồ sơ mẫu nhưng chuyển hóa concrete causality:
- nguyên nhân;
- vật chứng;
- phương pháp điều tra/giải quyết;
- relationship pressure;
- biểu hiện sức mạnh;
- payoff;
- chuỗi nhân quả nối arc.

## Clone Map

Trước Story Bible phải tạo `memory/clone_map.md` với bốn hành động:

- `KEEP_FUNCTION`
- `ADAPT`
- `REPLACE`
- `DROP`

Mỗi yếu tố phải trả lời:

```text
Source element
→ Narrative function
→ Action
→ New equivalent
→ What stays
→ What changes
```

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

Tạo mới hoàn toàn:
- vocabulary bank;
- ví von/ẩn dụ;
- slang;
- catchphrase;
- running jokes;
- wording nghi lễ;
- signature imagery.

Không sao chép nguyên câu hoặc đoạn văn từ nguồn.

## Outline

Không bootstrap macro outline trắng.

Dùng arc/timeline kể chuyện trong hồ sơ mẫu làm **khung chức năng**. Với mỗi arc nguồn:

```text
source arc
→ function
→ promise
→ escalation
→ midpoint function
→ climax function
→ payoff function
→ new causal chain
→ new arc
```

Chỉ khóa chi tiết 10–20 chương phía trước để truyện có thể thích nghi với state thực tế.

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
- nguy cơ chỉ đổi tên từ source.

Chỉ sau khi pass mới cập nhật memory chính thức.

## Lệnh tạo truyện mới

```text
@GitHub làm việc với repo cuongtobi/novel_maker.

Dùng hồ sơ mẫu tôi cung cấp.
Tạo truyện mới với slug <slug> theo profile-clone pipeline.
Tạo branch story/<slug>.

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

Tạo Clone Map trước khi khóa canon.
Review cross-file consistency.
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
Audit continuity branch hiện tại.
Kiểm tra chapter final với toàn bộ memory.
Nêu và sửa memory mismatch nếu chapter final đã xác nhận fact.
Không tự retcon chapter final.
```

## File quan trọng

- `docs/PIPELINE.md`: workflow đầy đủ.
- `prompts/MASTER.md`: master prompt điều phối.
- `templates/profile_clone.template.md`: scaffold clone toàn bộ hồ sơ.
- `templates/style_guide.template.md`: template style clone ở cấp kỹ thuật.
- `templates/outline.template.md`: outline theo arc function + batch plan.
- `memory/README.md`: schema memory của mỗi story branch.

## Definition of Done — Initial Clone

Một truyện chỉ được bắt đầu viết khi:
- story branch riêng đã tồn tại;
- source profile được ghi nhận;
- Clone Map pass;
- Narrative DNA pass;
- Story Bible pass;
- Characters/World/Factions/Power/Timeline/Relationships/Theme pass;
- Style Guide pass;
- Macro Outline + rolling beats pass;
- current_state ở chapter 0 nhất quán;
- không còn tên/địa danh/pháp bảo/thuật ngữ nguồn bị sót ngoài `source/profile.md` hoặc phần đối chiếu trong `clone_map.md`.
