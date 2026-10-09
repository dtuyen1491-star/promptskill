# SPINE-8+ Modules: Performance, Camera, Seedance 2.5

Đọc tài liệu này khi prompt cần biểu cảm/diễn xuất, camera path có kiểm soát, first-frame workflow, Seedance 2.5 multimodal references, keyframe, edit, extend hoặc timeline dài.

## Performance direction

Viết cảm xúc bằng hành vi nhìn thấy, theo chuỗi:

```text
facial cue → head/gaze cue → breath/body cue → hand/prop cue → hold → release
```

Tách `scene anchor`, `trigger/action` và `performance direction`. Không dùng “she is sad” nếu có thể mô tả mắt, miệng, đầu, vai, hơi thở, tay và điểm giữ.

Các biến intensity: biên độ, tốc độ, tension, hold và release. Continuity phải giữ cả trạng thái năng lượng, gaze, breath, tension và end expression.

## Camera module

Viết camera bằng:

```text
CAMERA TYPE:
DIRECTION:
PATH:
SPEED:
FRAMING:
RELATION TO SUBJECT:
END STATE:
```

Giữ camera instruction riêng với scene idea để tái sử dụng. Chọn camera theo chức năng kể chuyện: static để quan sát/test performance; dolly để tăng áp lực; pan/tilt để reveal; tracking để theo subject; arc/orbit để thay đổi quan hệ; pass-through để làm bridge; crane/drone để đổi scale.

First-frame workflow: kiểm tra ảnh → chọn một camera move → viết action độc lập → thêm style sau motion baseline → chốt end state/keyframes nếu cần.

## Seedance 2.5 architecture

Với prompt multimodal, dùng:

```text
ASSET BINDING:
@Image 1 = character identity
@Image 2 = prop/style/scene role
@Video 1 = motion/camera role
@Audio 1 = voice/music/dialogue role
SUMMARY: one sentence
TIMELINE: continuous segments with no gaps
CONSISTENCY: repeated identity, palette, camera and recurring details
```

Mỗi asset phải có một vai trò rõ. Với edit, ghi `scope + change + preserve`. Với dialogue dùng plain labeled lines. Negative phrasing chủ yếu dành cho caption/audio; mô tả hình ảnh mong muốn theo hướng khẳng định.

Thông số và giới hạn có thể phụ thuộc nơi thực thi; kiểm tra tài liệu/API hiện tại trước khi cam kết. Tài liệu BytePlus mô tả Seedance 2.5 hỗ trợ video tối đa 30 giây, input text/image/video/audio và tối đa 50 reference assets theo các giới hạn thành phần; tài liệu Runway mô tả asset-binding, summary, gap-free timeline và consistency notes.

## Test additions

1. Performance-only: locked close-up, không camera move.
2. Camera-only: giữ action, đổi 4 camera paths.
3. Asset-binding: đổi một role reference.
4. Timeline: beat liên tục, kiểm tra timing/drift.
5. Scoped edit: đổi đúng một thuộc tính, giữ composition/camera/lighting.
