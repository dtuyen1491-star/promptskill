---
name: spine-8-video-prompting
description: "Viết, phân tích, kiểm thử và debug prompt cho video AI theo phương pháp SPINE-8. Use for: text-to-video, image-to-video, multishot prompting, camera path, subject action, temporal progression, transformations, continuity, storyboard-to-prompt, prompt testing, batch generation, take selection, rough-cut diagnosis, and bilingual English–Vietnamese video prompt workflows."
---

# SPINE-8 Video Prompting

Dùng skill này như một quy trình đạo diễn–thử nghiệm, không như một công thức từ khóa. Mục tiêu là biến ý tưởng thành prompt có thể kiểm thử, chọn lọc và viết lại dựa trên bằng chứng từ output.

## Nguyên tắc cốt lõi

1. Viết cho thứ camera có thể nhìn thấy và model có thể chuyển động, không chỉ viết cảm giác trừu tượng.
2. Mỗi prompt/beat có **một ưu tiên chính** và thường chỉ có một hành động chính.
3. Viết camera như một **đường đi**: vị trí đầu → hướng → path → tốc độ → quan hệ với subject → điểm kết.
4. Mọi transformation phải có **bridge mechanism**; không chỉ viết “A transforms into B”.
5. Kiểm tra cơ học trước khi đánh giá thẩm mỹ.
6. Multishot phải có global premise, global visual rule, global continuity, shot architecture và end state của từng shot.
7. Sinh theo batch có câu hỏi riêng; tuyển theo chức năng, continuity và khả năng dựng, không chỉ theo take đẹp nhất.
8. Nếu output thất bại, sửa đúng lớp gây lỗi và chỉ thay một biến chính.

## SPINE-8

- **S — Story intent:** premise, trải nghiệm người xem, đích cảm xúc.
- **P — Picture & identity:** visual anchor, character/prop/style bible, reference image.
- **I — Interaction:** hành động subject và phản ứng môi trường.
- **N — Navigation:** điểm nhìn và camera path.
- **E — Events:** starting state, action, transformation, ending state, timing.
- **8 — Vòng lặp:** Bridge → Continuity → Style/constraints → Test → Generate → Select → Edit → Rewrite.

### SPINE-8+

Khi cần diễn xuất, camera phức tạp hoặc Seedance 2.5 multimodal, thêm ba lớp thực thi:

- **Performance direction:** viết cảm xúc bằng hành vi nhìn thấy theo chuỗi `facial cue → head/gaze → breath/body → hand/prop → hold → release`; không dùng nhãn cảm xúc thay cho acting.
- **Camera path module:** tách `camera type, direction, path, speed, framing, relation to subject, end state`; chọn chuyển động theo chức năng kể chuyện, không dùng “cinematic camera” chung chung.
- **Multimodal orchestration:** gắn vai trò cho từng `@Image/@Video/@Audio`, viết một câu summary, timeline liên tục không gap và consistency notes; edit phải nêu scope, change và preserve.

Đọc `references/seedance-camera-emotion.md` khi cần các lớp này.

## Quy trình bắt buộc

### 1. Xác định loại workflow

- **Text-to-video:** xây visual anchor trước, sau đó action → camera → time → bridge → style.
- **Image-to-video:** coi ảnh đầu vào là visual layer; tập trung action → camera → timing → transformation → style refinement.
- **Multishot:** thiết kế global layer và shot layer; không prompt mọi shot như các clip độc lập.
- **Chưa rõ hoặc ý tưởng phức tạp:** bắt đầu bằng premise, beat table và test cơ học; không viết prompt dài ngay.

### 2. Viết premise một câu

Dùng mẫu:

> [Chủ thể] thực hiện [hành động trung tâm] trong khi [biến đổi/xung đột] diễn ra theo [quy tắc hình ảnh], kết thúc ở [đích cảm xúc/trạng thái].

Viết cả bản English nếu người dùng cần prompt dùng trực tiếp. Nếu premise chỉ có tính từ như “cinematic, magical, emotional”, hãy chuyển nó thành hành động và bằng chứng hình ảnh.

### 3. Tạo visual anchor/identity

Ghi ngắn gọn: subject, environment, composition, lighting, palette, prop, wardrobe và 3–5 identity anchors. Với input image, không lặp lại mọi chi tiết đã có; mô tả phần cần chuyển động.

### 4. Chia thành beat

Mỗi beat phải có:

- Starting state.
- Primary action.
- Camera path.
- Transformation/reveal.
- Ending state.
- Continuity cue.
- Failure risk.

Giữ quy tắc **một thay đổi chính mỗi beat**.

Nếu beat có cảm xúc hoặc performance, thêm `emotion state, intensity, facial cue, gaze/head cue, breath/body cue, hand/prop cue, hold, release`. Nếu dùng first frame, không mô tả lại mọi chi tiết ảnh; chọn một camera move, một action và một ending state.

### 5. Viết prompt theo lớp

Thứ tự mặc định cho single-shot:

1. Visual anchor.
2. Subject action.
3. Camera path.
4. Temporal progression.
5. Transformation/bridge.
6. Style and constraints.
7. Audio nếu model hỗ trợ.

Với prompt multimodal dài, dùng thứ tự: **asset binding → one-sentence summary → gap-free timeline → performance/camera details → consistency notes**. Mỗi asset phải có một vai trò rõ; dialogue dùng dòng có nhãn người nói; negative phrasing chủ yếu dành cho audio/caption.

Không dùng “dynamic camera” nếu chưa mô tả đường đi. Không dùng danh sách negative prompt dài khi có thể mô tả trạng thái mong muốn bằng phrasing khẳng định.

### 6. Chạy test cơ học nhỏ

Viết hypothesis và success criteria trước khi generate. Dùng clip ngắn vừa đủ cho cơ chế. Cô lập một biến: subject action, camera path, timing, transformation, reflection, material spread hoặc continuity bridge.

Template đầy đủ nằm ở `references/testing-and-selection.md`.

### 7. Sinh theo batch và tuyển chọn

- Batch stability: giữ prompt, đo độ ổn định.
- Batch camera: chỉ đổi camera path.
- Batch timing: chỉ đổi vị trí sự kiện theo thời gian.
- Batch bridge: chỉ đổi cơ chế transition.
- Batch style: chỉ thêm sau khi cơ chế đã ổn.

Dùng scorecard và material log. Trong multishot, continuity có quyền phủ quyết.

### 8. Dựng rough cut và viết lại

Dựng sớm. Ghi strongest moment, lỗi thật, behavioral signature, phần giữ, phần đổi và prompt tiếp theo. Viết lại theo 5 mức: patch → restructure → reframe → rewrite premise → rewrite sequence architecture.

## Nhánh debug nhanh

- **Hình ảnh đúng, action sai:** bỏ style, giảm còn một động từ, khóa camera hoặc mở rộng framing.
- **Action đúng, camera sai:** đưa camera lên đầu, dùng một path duy nhất, bỏ “dynamic”.
- **Camera đúng, timing sai:** ghi rõ initial hold và “only after…”.
- **Transformation đúng, bridge yếu:** thêm vật liệu trung gian, vật thể lấp frame, cửa, bóng, phản chiếu hoặc camera đi xuyên.
- **Từng shot đúng nhưng sequence không nối:** lập continuity board với end state, anchor, camera direction và bridge.
- **Prompt quá dài:** tháo style trước, giữ anchor tối thiểu, một action, camera path, timing rồi mới thêm lại.
- **Cảm xúc phẳng:** thay emotion label bằng facial/gaze/breath/body/hand cues và thêm hold/release.
- **Camera mơ hồ:** viết Movement/Direction/Path/Speed/Framing/End; test static trước rồi mới tăng độ phức tạp.
- **Reference bị trộn:** tạo asset-binding list, nêu role từng asset và lặp lại primary reference traits ở các beat chính.
- **Timeline bị drift:** phủ kín toàn bộ duration bằng timestamp segments, khóa first/last frame khi endpoint cần chính xác.

## Chuẩn output

Khi người dùng yêu cầu tạo prompt, ưu tiên output theo cấu trúc:

1. **Premise / Ý định**.
2. **Assumptions / Giả định** nếu còn thiếu thông tin.
3. **Prompt English**.
4. **Bản tiếng Việt**.
5. **Layer breakdown / Phân tích theo lớp**.
6. **Minimal mechanical test / Test tối giản**.
7. **Success criteria / Tiêu chí thành công**.
8. **Next revision / Biến duy nhất nên sửa ở lượt sau**.

Với multishot, thêm global continuity, shot table, bridge và ending state. Với yêu cầu chỉ cần prompt ngắn, không ép người dùng nhận toàn bộ báo cáo; đưa prompt trước, phần phân tích sau.

## Tài nguyên tham chiếu

- Đọc `references/prompt-templates.md` khi cần template single-shot, image-to-video, multishot hoặc ví dụ song ngữ.
- Đọc `references/testing-and-selection.md` khi cần thiết kế test, scorecard, batch, material log hoặc rewrite.
- Đọc `references/bilingual-lexicon.md` khi cần chuyển động camera/action Anh–Việt.
- Đọc `references/seedance-camera-emotion.md` khi cần performance direction, camera movement library, first-frame workflow hoặc Seedance 2.5 asset/timeline architecture.

## Không được làm

- Không tuyên bố template là prompt nguyên văn của chuyên gia nếu chỉ là bản tái dựng.
- Không nhồi nhiều transformation, camera path và style shift vào một clip ngắn mà chưa test riêng.
- Không đánh giá take chỉ bằng độ đẹp.
- Không thêm từ ngẫu nhiên sau thất bại nếu chưa chẩn đoán lớp lỗi.
- Không mô tả lại chi tiết hình ảnh đầu vào một cách dư thừa trong image-to-video.
