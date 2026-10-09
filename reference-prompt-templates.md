# SPINE-8 Prompt Templates

## Single-shot — English

> [Shot type and visual anchor]. [Subject] [performs one primary action] toward [object/direction], ending with [observable end state]. The camera begins [starting position], [moves along a specific path] at [speed], and ends [destination/framing]. First [initial state], then [event], while [parallel event]. [Bridge mechanism]. [Style, lighting, texture, constraints]. [Audio if supported].

## Single-shot — Tiếng Việt

> [Loại shot và visual anchor]. [Chủ thể] [thực hiện một hành động chính] về phía [đối tượng/hướng], kết thúc ở [trạng thái quan sát được]. Camera bắt đầu ở [vị trí], [đi theo đường cụ thể] với [tốc độ], rồi kết thúc ở [đích/bố cục]. Đầu tiên [trạng thái đầu], sau đó [sự kiện], trong khi [sự kiện đồng thời]. [Cơ chế bridge]. [Phong cách, ánh sáng, texture, ràng buộc]. [Âm thanh nếu được hỗ trợ].

## Image-to-video — English

> The subject [performs one simple action]. The camera [specific movement or remains locked]. [One temporal change or environmental response]. Preserve the existing composition and identity anchors. [End state].

## Image-to-video — Tiếng Việt

> Chủ thể [thực hiện một hành động đơn giản]. Camera [chuyển động cụ thể hoặc giữ cố định]. [Một thay đổi theo thời gian hoặc phản ứng môi trường]. Giữ nguyên bố cục và các neo identity hiện có. [Trạng thái cuối].

## Multishot global layer

```text
GLOBAL PREMISE:
GLOBAL VISUAL RULE:
GLOBAL CONTINUITY:
GLOBAL CAMERA DIRECTION:
GLOBAL EMOTIONAL ARC:
GLOBAL STYLE:
```

## Multishot shot layer

```text
SHOT ID:
FUNCTION:
STARTING STATE:
PRIMARY ACTION:
CAMERA PATH:
TRANSFORMATION / BRIDGE:
ENDING STATE:
CONTINUITY CUE TO NEXT SHOT:
FAILURE RISK:
```

## Ví dụ single-shot song ngữ

### English

> A woman in a yellow raincoat stands beside a red train and slowly touches its glass door. The camera begins in a locked medium shot and holds her hand and the window. For the first three seconds, the train remains still. Only after her fingertips touch the glass does the dark tunnel beyond the window become a sunlit ocean. Fish drift through the carriage. Muted colors, steady motion, restrained surrealism.

### Tiếng Việt

> Một người phụ nữ mặc áo mưa vàng đứng cạnh đoàn tàu đỏ và từ từ chạm vào cửa kính. Camera bắt đầu bằng medium shot cố định, giữ bàn tay và ô cửa trong khung. Trong ba giây đầu, đoàn tàu đứng yên. Chỉ sau khi đầu ngón tay chạm kính, đường hầm tối phía sau ô cửa mới biến thành đại dương đầy nắng. Cá trôi qua trong toa. Màu trầm, chuyển động ổn định, chủ nghĩa siêu thực tiết chế.

## Ví dụ prompt tối giản để test

**English:**

> A woman in a yellow raincoat touches the glass door of a red train. The locked camera holds her hand and the window. The dark tunnel becomes a sunlit ocean.

**Tiếng Việt:**

> Một người phụ nữ mặc áo mưa vàng chạm vào cửa kính của đoàn tàu đỏ. Camera cố định giữ bàn tay và ô cửa. Đường hầm tối biến thành đại dương đầy nắng.

## Quy tắc rút gọn

Nếu prompt thất bại, giữ lại theo thứ tự:

1. subject/object anchor;
2. một action;
3. camera path;
4. timing;
5. bridge;
6. style;
7. audio.
