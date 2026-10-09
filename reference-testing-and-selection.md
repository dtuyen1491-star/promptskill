# Testing, Selection and Rewrite

## Mechanical test template

```text
Test ID:
Hypothesis:
Mechanical question:
Input conditions:
Minimal prompt:
Variable under test:
Clip length:
Success criteria:
Failure modes:
Observation:
Diagnosis:
Next change:
Confidence:
```

## Hypothesis pattern

Yếu:

> I want the video to feel magical.

Mạnh:

> If the camera pushes toward the red apple until it fills the frame, the apple's surface will become a red planet without a visible cut.

## Success criteria

Viết tiêu chí có thể quan sát:

- hand touches glass by the end;
- camera remains locked;
- reflection stays visible;
- subject remains still;
- object fills the frame;
- shot 2 starts with the same prop and direction.

Không dùng tiêu chí chỉ có tính cảm giác như “cinematic” hoặc “beautiful”.

## Batch design

### Stability

Giữ nguyên prompt, tạo 4–8 take để đo cơ chế có lặp lại không.

### Camera

Chỉ thay locked / push-in / tracking / truck / arc.

### Timing

Chỉ thay event xảy ra đầu, giữa hoặc cuối clip.

### Bridge

Chỉ thay material spread / object fills frame / camera passes through / match shape / shadow bridge.

### Style

Chỉ thêm palette, lens, grain, lighting sau khi cơ chế ổn.

## Scorecard — single shot

| Tiêu chí | Điểm 0–5 | Ghi chú |
|---|---:|---|
| Cơ chế chính xảy ra |  |  |
| Hành động đọc được |  |  |
| Camera đúng đường |  |  |
| Timing đúng |  |  |
| Identity/continuity |  |  |
| Bridge rõ |  |  |
| Ý định cảm xúc |  |  |
| Khả năng dựng |  |  |
| Penalty lỗi nghiêm trọng | -0 đến -3 |  |

## Scorecard — multishot

Dùng thứ tự ưu tiên:

1. Sequence có nối được không?
2. Continuity có giữ không?
3. Mỗi shot có chức năng không?
4. Cảm xúc có tiến triển không?
5. Hình ảnh có đẹp không?

Continuity có quyền phủ quyết khi một shot làm mất identity, prop, hướng camera hoặc end-state cần thiết.

## Kill list

Loại ngay nếu:

- mất subject chính;
- action không đọc được;
- camera đảo hướng không chủ ý;
- anchor biến mất;
- frame cuối không nối được;
- artifact phá ý nghĩa.

Giữ lại nếu cơ chế đúng dù ánh sáng chưa đẹp, hoặc nếu đoạn ngắn có thể crop/retime/composite.

## Material log

```text
Take:
Strongest moment:
What actually works:
What fails:
Behavioral signature:
Keep:
Change:
Next prompt:
```

## Rewrite ladder

1. **Prompt patch:** sửa một động từ hoặc timing marker.
2. **Prompt restructuring:** sắp xếp lại action/camera/time.
3. **Prompt reframing:** đổi shot size hoặc point of view.
4. **Premise rewrite:** giữ ý nghĩa, đổi cách thực hiện.
5. **Sequence architecture rewrite:** đổi vai trò hoặc thứ tự shot.

## Debug matrix

| Triệu chứng | Chẩn đoán | Sửa trước tiên |
|---|---|---|
| Hình ảnh đúng, action sai | action quá nhiều hoặc camera tranh ưu tiên | giảm còn một động từ, khóa camera |
| Action đúng, camera sai | camera path mơ hồ hoặc có nhiều path | đưa camera lên đầu, dùng một path |
| Camera đúng, timing sai | event không có mốc | thêm initial hold và “only after…” |
| Transformation đúng, bridge yếu | chỉ mô tả kết quả | thêm vật liệu trung gian |
| Shot đúng, sequence sai | thiếu global continuity/end state | lập continuity board |
| Take đẹp nhưng không dựng được | tuyển theo thẩm mỹ | chấm lại theo chức năng và context |

## Continuity board

| Shot | End state | Anchor giữ | Hướng camera | Bridge sang shot sau |
|---|---|---|---|---|
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
