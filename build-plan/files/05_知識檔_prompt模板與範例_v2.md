# 05 知識檔｜Prompt 模板與範例（室內設計生圖）

本檔用途：把使用者的一句中文需求，轉成可直接送進生圖工具的英文 prompt；並提供三種任務型態的寫法、12 組實戰範例、多角度一致與局部修圖的規則。**本檔負責模式一（文生圖概念圖／實景照保格局換風格）與模式三（局部修改）；模式二（平面圖→3D 等角圖）見 08 檔。**
使用方式：先讀 04 檔取風格關鍵詞與材質 → 套本檔主模板九個 block → 依任務型態（概念圖／保格局換風格／局部修改）選對應模板 → 出圖 → 對照 F-1 禁止清單自檢。

## 生圖環境事實（2026-08-19 查證，寫 prompt 前先知道）

- 現役模型 gpt-image-2（ChatGPT Images 2.0，2026-04 上線）。官方 API **無 fine-tune／LoRA**，使用者不能訓練模型；客製只能靠指令、知識檔、參考圖與風格庫。
- **參考圖**：edit 端支援一或多張參考圖（官方範例 4 張，第三方文件記載上限 16 張）。inpaint 支援 mask：mask PNG 需與原圖同尺寸，**透明區＝要改的區**。
- **可調參數**：quality low/medium/high/auto；size 寬高需為 16 的倍數、長寬比 1:3～3:1、最高 3840×2160（2560×1440 以上為實驗性）；n 可一次多張。gpt-image-2 的 input_fidelity 預設高保真、不可調。
- **模式**：Instant（全用戶）／Thinking（Plus、Pro、Business、Enterprise 可用：支援網搜、版面推理、多圖批次一致、輸出校驗）。同案多機位一致性優先用 Thinking。
- 官方 prompting guide 重點：用**攝影語言**（鏡頭、光線、構圖）、明確要求真實質感（布料皺褶、木紋、材質磨損）、指定 framing／viewpoint／perspective／lighting mood、**清楚區分「該變」與「必須不變」**。
- Plus 生圖額度官方未公開，社群回報落差大；Pro 定位為不限量。批次出圖前先確認需求張數，不要無謂重骰。

※ 尺度、焦段、四個標準機位與色溫建議以 03 檔（台灣住宅尺度與鏡頭幾何）為準；材質中英文對照以 02 檔（材質與工法詞彙表）為準；風格關鍵詞、色票與負面詞以 04 檔為準。本檔只負責「怎麼把這些組成 prompt」。

---

# A. 主模板（九個 block）

順序固定，**不要打亂**。模型讀 prompt 時前段權重高，所以「硬鎖 → 空間 → 風格 → 不變 → 材質 → 光 → 相機 → 品質 → 禁止」。

```
[LOCK]                 空間骨架硬鎖段（逐字不改，見下方定稿句）
[SPACE & SIZE]        空間類型、坪數/尺寸、格局特徵、有幾個開口
[STYLE]                04 檔英文關鍵詞挑 6–12 個
[LAYOUT — KEEP]       必須不變的清單（保格局任務必填；概念圖可略）
[MATERIALS]           依表面分寫：地坪／牆面／天花／櫃體／檯面／織品，各帶質感詞（每項後接一句光照描述，見 A-3 第 7 條）
[LIGHTING]            時間、方向、色溫、氛圍（明暗對比程度）
[CAMERA]              焦距、眼高 120cm、透視型式、構圖框取
[QUALITY / REALISM]   寫實質感要求（木紋、布料皺褶、金屬霧面、材質磨損）
[NEGATIVE / AVOID]    禁止清單（F-1 通用清單 ＋ 該風格負面詞）
```

**[LOCK] 定稿句（每則 prompt 最前面逐字貼，不隨案子改寫，對應 01 檔 §0 共用鐵則一／H-2 第 13 條）：**

```
SPATIAL SKELETON — DO NOT ALTER: wall positions, window positions and sizes, door opening
position, camera angle and lens height are fixed and must not be changed. Only materials,
lighting and furnishings may be changed.
```

## A-1 填空版（英文，中文為欄位說明）

```
SPATIAL SKELETON — DO NOT ALTER: wall positions, window positions and sizes, door opening
position, camera angle and lens height are fixed and must not be changed. Only materials,
lighting and furnishings may be changed.

A photorealistic interior photograph of a {空間類型 room type} in a Taiwanese newly-completed
apartment, approximately {坪數/尺寸 size, e.g. 12 ping / 40 square meters}, with {開口與格局特徵
e.g. one full-height aluminium-framed sliding window on the left and a single 210cm-high door on
the right}, ceiling height {天花淨高 240-260cm after renovation}.

KEEP UNCHANGED: {必須不變清單 — window positions and sizes, door position, wall layout, beam
positions, column positions, air-conditioner indoor unit position}.

MATERIALS — floor: {地坪材質＋質感詞}; walls: {牆面材質}; ceiling: {天花做法, e.g. flat white
ceiling with a recessed cove lighting slot along the beam}; cabinetry: {櫃體材質＋門片形式};
countertop: {檯面材質}; textiles: {織品}.

LIGHTING: {時間, e.g. late morning daylight} entering from {方向, e.g. the left window},
supplemented by {人工光, e.g. 3000K warm-white cove lighting}, soft shadows, {對比程度, e.g. low
contrast, bright and airy}.

CAMERA: shot on a {焦距 24mm} equivalent wide-angle lens at eye level, camera height 120cm,
{one-point perspective / two-point perspective}, verticals kept straight, {框取要求, e.g. the
whole sofa and the TV wall fully inside the frame, nothing cropped}.

QUALITY: photorealistic architectural interior photography, natural material rendering, visible
wood grain, realistic fabric wrinkles, matte metal, accurate reflections, sharp focus, high detail.

AVOID: {F-1 通用清單 ＋ 風格負面詞}
```

## A-2 一段式範例（把填空版壓成一段，實務最常用）

```
SPATIAL SKELETON — DO NOT ALTER: wall positions, window positions and sizes, door opening
position, camera angle and lens height are fixed and must not be changed. Only materials,
lighting and furnishings may be changed.

A photorealistic interior photograph of a living room in a Taiwanese newly-completed apartment,
about 12 ping, with one full-height aluminium-framed sliding window on the left wall and a
210cm-high flush white door on the right, renovated ceiling height 250cm with a dropped soffit
concealing the beam. Floor is light oak wood flooring with visible grain; walls are warm off-white
matte paint; the ceiling is flat white with a 3000K cove lighting slot running along the beam;
the TV wall is full-height handleless light oak veneer cabinetry with a recessed niche; the low
sideboard has a warm white solid surface top; a beige linen three-seat sofa with 42cm seat height
and a wool rug sit facing it, main walkway kept at 90cm. Late-morning daylight enters from the
left window, soft shadows, low contrast, bright and calm. Shot on a 24mm equivalent wide-angle
lens at eye level, camera height 120cm, one-point perspective, verticals straight, the whole sofa
and the entire TV wall fully inside the frame. Photorealistic architectural interior photography,
visible wood grain, realistic linen wrinkles, matte finishes, sharp focus, highly detailed.
AVOID: fisheye distortion, bird's eye view, western fireplace, skylight, foreign power outlets,
overexposed highlights, repeated tiling texture, floating furniture, missing window, missing door,
disappearing beam, wrong scale furniture, text, watermark, logo, people.
```

## A-3 寫 prompt 的八條硬規則

1. **尺度必寫**：門高 210cm、檯面高 85–90cm、沙發座高 40–45cm、主走道 ≥90cm、床邊走道 ≥60cm、餐桌高 75cm、書桌高 72–75cm、洗手台高 80–85cm、上櫃底距檯面 65–75cm、電視牆看距＝螢幕對角線 ×1.5–2.5。寫進 prompt 能大幅降低比例翻車。
2. **相機固定**：24mm 等效（可 20–28mm）、眼高 120cm、一點透視為主、兩點次之、`verticals kept straight`。**永遠加 `no fisheye`**。局部特寫與招牌／文字渲染例外，可用 35–50mm 標準鏡，此時不算違反廣角規定。
3. **材質限五種以內**：地坪、牆面、櫃體、檯面、織品各一，超過畫面會亂。
4. **顏色寫名稱不寫 hex**：`warm off-white`、`light oak`、`sage green`，不要寫 #F2ECDF。
5. **「不變」要逐項列**：模型不會自己知道哪些不能動，`KEEP UNCHANGED:` 後面用逗號列清單。
6. **法規類數字不編**：消防、無障礙、逃生相關尺寸若無明確來源，回覆寫「需確認」，不要寫進 prompt 當事實。
7. **材質詞要連光一起寫**：單獨寫 `matte oak` 沒有用，材質的說服力來自光而不是名詞。MATERIALS block 每項材質後面至少接一句光照描述，例如 `light oak flooring, catching soft daylight from the left window with visible grain highlights`，不得只寫材質名詞（對應 H-2 第 5 條）。
8. **先講空間，再講畫面**：[SPACE & SIZE] 與 [LAYOUT — KEEP] 固定排在 [STYLE] 之前，把格局、動線、家具位置當獨立條件先鎖定，再交代風格與畫面感（對應 H-2 第 2 條，已是 A 段 block 順序的落地版）。

---

# B. 三種任務模板

模式二 平面圖→3D 見 08 檔，本段只涵蓋模式一與模式三。

## 模式一之一　文生圖概念圖（無參考照）

用途：客戶還沒交屋、只有平面圖或口頭需求，先給方向。
特徵：**沒有 KEEP UNCHANGED**，改用「格局假設」明講這是示意。

```
TASK: concept rendering, no reference photo.

A photorealistic interior photograph of a {room} in a Taiwanese newly-completed apartment,
about {size}. Assumed layout: {自訂格局假設 — e.g. rectangular room 3.6m x 4.5m, one window on
the short wall, entrance door on the opposite corner}, renovated ceiling height 250cm.
STYLE: {04 檔的英文關鍵詞挑 6-10 個}.
MATERIALS — floor {..}; walls {..}; ceiling {..}; cabinetry {..}; countertop {..}; textiles {..}.
LIGHTING: {..}. CAMERA: 24mm equivalent, eye level 120cm, one-point perspective, verticals straight.
QUALITY: photorealistic architectural photography, visible wood grain, realistic fabric wrinkles.
AVOID: {F-1 通用清單}
```

交付時必附一句：**「本圖為概念示意，格局為假設值，實際以現場丈量與圖說為準。」**

## 模式一之二　實景照保格局換風格（有參考照）

用途：客戶已交屋、拍了空屋照或現況照，要看「同一個空間換成 X 風格」。
做法：走 **edit（圖生圖）**，上傳實景照當參考圖；**不可用純文生圖冒充**，格局一定會跑掉。

```
TASK: restyle this exact room. Use the uploaded photo as the strict structural reference.

KEEP UNCHANGED (do not move, resize, add or remove):
- window positions, window widths and heights, aluminium frame divisions
- door position and its 210cm height
- all wall positions and room proportions
- beam and column positions and depths
- air-conditioner indoor unit position
- ceiling height and the existing soffit lines
- camera position and viewing angle — reproduce the same viewpoint as the photo

CHANGE ONLY the finishes and furnishings:
- floor -> {新地坪}
- walls -> {新牆面}
- ceiling -> {新天花做法}
- built-in cabinetry -> {新櫃體}
- furniture and textiles -> {新家具軟裝}
- lighting -> {新燈光與色溫}

STYLE: {04 檔關鍵詞}
QUALITY: photorealistic, match the original perspective and lens distortion, realistic materials.
AVOID: changing the window or door positions, adding windows, removing beams, changing the room
proportions, changing the camera angle, {F-1 通用清單}
```

**交付前五項比對（每次都做，逐項與原圖對照）**：窗 → 門 → 樑柱 → 天花線 → 主要牆面位置。任一項跑掉就重出；重出兩輪仍不過，交付時**明講哪一項跑掉，不得宣稱「格局保留」**。

## 模式三　局部修改（只換地坪／櫃體／燈具）

用途：整張圖已經對了，只想換一項。
兩種做法，優先用 mask：

**做法 A — mask（inpaint，精準）**
- 準備與原圖**同尺寸**的 mask PNG；**透明區＝要修改的區域**，不透明區＝維持原樣。
- prompt 只描述要改的那一項，不要重述整個房間。

```
Replace only the area indicated by the transparent region of the mask.
New content: {只寫這一項 — e.g. light oak herringbone wood flooring with visible grain, laid
running away from the camera}. Match the existing perspective, lighting direction and colour
temperature of the photograph exactly. Keep everything else exactly the same.
AVOID: changing furniture, changing walls, changing lighting, shifting perspective, {F-1 通用清單}
```

**做法 B — 文字指定區域（沒有 mask 時）**

```
Keep everything in this image exactly the same — same camera angle, same layout, same furniture,
same lighting — and change ONLY the {指定物件與位置, e.g. the pendant lamp above the dining table}.
New version: {新描述, e.g. a matte black globe pendant, 30cm diameter, hung 75cm above the table
top}. Do not alter anything else.
```

**局部修改鐵則**：一次只改一項。要改三項就分三次，每次都帶 `keep everything else exactly the same`。同時改多項＝等於重骰，前面對的地方會一起變掉。

## B-4 材質五大類命名表

材質先依五大類建成固定清單，寫 MATERIALS block 時直接引用清單名稱、不臨場想形容詞（對應 H-2 第 15 條）：石材／木皮與木地板／金屬／織品／塗裝。**品項名稱待補**——40 組具體英文命名尚未從 02 檔既有內容抽取歸類，先只給分類框架；抽取完成後併入本節，同步更新 02 檔（見 02_04_增補清單.md 待辦）。

## B-5 攝影語彙優先

STYLE block 出現「高級」「溫馨」這類形容詞時，優先換成對應的鏡頭／光源／景深描述——攝影參數比情緒形容詞更能穩定出圖品質（對應 H-2 第 7 條、I 段第 1 條）。例：「溫馨」→ `warm 2700K ambient lighting, soft diffused shadows`；「高級」→ `slim brushed-metal trim, shallow depth of field, elegant restrained palette`。

## B-6 官方參數表對帳

每案出圖前至少對照一次官方參數表打勾：quality（low/medium/high/auto）、size（16 的倍數，長寬比 1:3–3:1）、input_fidelity（高保真、不可調）、n（一次張數）。漏用參數比再改十版文字更常是翻車主因（對應 H-2 第 16 條、I 段第 5 條）。

---

# C. 範例 12 組

每組格式：需求（中文一句）→ 完整英文 prompt →（為什麼這樣寫）→（常見翻車與修法）。風格輪流覆蓋十種。

---

## C-01 客廳｜現代簡約

**需求**：新成屋 12 坪客餐廳，要電視牆做滿收納，看起來乾淨不壓迫。

```
A photorealistic interior photograph of an open-plan living and dining room in a Taiwanese
newly-completed apartment, about 12 ping, with a full-height aluminium-framed sliding window on
the left wall opening to a balcony, a 210cm-high flush white door on the right, and a beam along
the ceiling concealed by a dropped soffit, renovated ceiling height 250cm. Modern minimalist
interior, neutral palette, clean geometry, uncluttered. Floor is large-format matte porcelain tile
in warm grey; walls are warm off-white flat paint; the ceiling is flat white with a continuous
3000K cove lighting slot along the soffit; the TV wall is full-height handleless matte white
cabinetry with a light walnut veneer recessed niche and a wall-mounted 65-inch television, viewing
distance about 2.5 metres; a floating sideboard sits 18cm above the floor; a beige three-seat
fabric sofa with 42cm seat height faces it across a wool rug, main walkway kept at 90cm; a light
walnut dining table 75cm high with four chairs sits under the window. Late-morning daylight from
the left window, soft shadows, low contrast, bright and calm. Shot on a 24mm equivalent wide-angle
lens at eye level, camera height 120cm, one-point perspective, verticals kept straight, the whole
sofa and the entire TV wall fully inside the frame, nothing cropped. Photorealistic architectural
interior photography, visible wood grain, realistic fabric wrinkles, matte lacquer finish, sharp
focus, highly detailed.
AVOID: fisheye distortion, bird's eye view, cold grey showroom look, floating furniture not
touching the floor, western fireplace, skylight, foreign power outlets, overexposed highlights,
repeated tiling texture, missing window, missing door, disappearing beam, wrong scale furniture,
text, watermark, logo, people.
```

**為什麼這樣寫**：把「包樑做間照」「櫃體到天花」「懸空 18cm」這三個台灣新成屋實務動作寫死，模型才不會畫成國外挑高客廳。看距寫 2.5m 對應 65 吋（對角線 165cm ×1.5–2.5）。
**常見翻車與修法**：電視畫成超大佔滿整面牆 → 補寫 `65-inch television, the TV occupies less than one third of the wall width`。

---

## C-02 客廳｜北歐風

**需求**：三房兩廳客廳，白牆淺木、要有大採光跟植栽。

```
A photorealistic interior photograph of a living room in a Taiwanese newly-completed apartment,
about 10 ping, with two full-height aluminium-framed windows on the far wall and a single
210cm-high door on the left, renovated ceiling height 250cm. Scandinavian interior, Nordic style,
light oak, white washed walls, cozy minimalism, natural linen, airy and bright. Floor is light oak
laminate flooring with visible grain; walls are matte white paint; the ceiling is flat white with
a slim 3000K cove slot; a light oak open shelving unit with white back panels stands against the
right wall; a light grey linen three-seat sofa with 43cm seat height and a pale wool rug face a
round oak coffee table; sheer linen curtains hang from a concealed curtain box; a fiddle-leaf fig
in a woven basket stands beside the window; slim black metal floor lamp in the corner. Abundant
midday daylight through the two windows, soft diffused shadows, high-key bright exposure without
blowing out the highlights. Shot on a 24mm equivalent wide-angle lens at eye level, camera height
120cm, one-point perspective, verticals kept straight. Photorealistic architectural interior
photography, natural linen texture, visible oak grain, sharp focus, highly detailed.
AVOID: fireplace, chimney, wainscoting, shaker panel doors, dark walnut floor, snow outside the
window, cluttered shelves, yellow orange colour cast, fisheye distortion, bird's eye view,
overexposed blown highlights, floating furniture, missing window, text, watermark, people.
```

**為什麼這樣寫**：北歐風最容易被模型加壁爐與雪景，所以負面詞優先擋這兩項；`high-key ... without blowing out` 是防過曝的關鍵句。
**常見翻車與修法**：窗外一片死白 → 加 `visible city greenery outside the window, balanced exposure between interior and exterior`。

---

## C-03 客廳｜侘寂 Wabi-sabi

**需求**：中古屋翻新客廳，想要手抹塗料的安靜感，不要太暗。

```
A photorealistic interior photograph of a living room in a renovated Taiwanese apartment, about 9
ping, with one large aluminium-framed window on the left and a 210cm-high flush door on the right,
ceiling height 250cm after renovation. Wabi-sabi interior, hand-troweled lime plaster walls with
subtle trowel marks, earthy muted clay palette, imperfect natural materials, quiet imperfection.
Floor is warm grey microcement with a seamless finish; the feature wall behind the sofa is
hand-troweled lime plaster in oatmeal beige; the ceiling is flat off-white with a hidden light
slot washing the plaster wall; a low dark oak veneer sideboard with a plastered front sits against
the wall; a low-profile linen sofa with 40cm seat height, an undyed linen throw, a chunky solid
wood side table, unglazed ceramic vessels and dried branches complete the room. Single-direction
soft afternoon daylight from the left window, gentle gradients from light to shadow, 2700K hidden
accent light, calm and quiet, moderate contrast but the room stays legible and not gloomy. Shot on
a 24mm equivalent wide-angle lens at eye level, camera height 120cm, one-point perspective,
verticals kept straight. Photorealistic architectural interior photography, visible plaster
texture, realistic linen wrinkles, matte stone surfaces, sharp focus, highly detailed.
AVOID: ruined wall, peeling paint, construction site look, exposed wiring, abandoned building,
damp mold stains, cracked broken surfaces, gloomy pitch-dark room, industrial concrete loft,
fisheye distortion, bird's eye view, floating furniture, missing window, text, watermark, people.
```

**為什麼這樣寫**：侘寂最大風險是被畫成廢墟，所以正面寫 `subtle trowel marks`（有質感但完整），負面把「剝落、裂縫、發霉」全擋掉；再加一句 `stays legible and not gloomy` 防過暗。
**常見翻車與修法**：整張灰到看不出家具 → 把 `moderate contrast` 改成 `soft even daylight, low contrast`，並加 `bright enough to read every surface`。

---

## C-04 主臥｜日式無印

**需求**：主臥 5 坪，床頭做收納、要安靜好睡。

```
A photorealistic interior photograph of a master bedroom in a Taiwanese newly-completed apartment,
about 5 ping, with one aluminium-framed window on the right wall and a 210cm-high flush door on
the left, renovated ceiling height 245cm with a dropped soffit over the wardrobe concealing the
air-conditioner. Japanese muji style, natural wood, clean lines, serene minimalism, warm neutral
tones. Floor is light oak wood flooring; walls are warm off-white diatomaceous-earth textured
plaster; the ceiling is flat off-white with a concealed 2700K light slot above the headboard; a
full-height handleless light oak veneer wardrobe runs along the left wall to the ceiling; the
headboard wall has a slim oak ledge at 60cm above the mattress with two paper-shade wall lamps; a
low platform bed with a linen duvet in oat white, cotton cushions, a woven floor basket and a
single branch in a ceramic vase; walkway beside the bed kept at 60cm. Soft diffused morning
daylight filtered through sheer linen curtains, no harsh light patches, 2700K warm ambient
lighting, calm and quiet. Shot on a 24mm equivalent wide-angle lens at eye level, camera height
120cm, one-point perspective, verticals kept straight, the whole bed and the wardrobe wall fully
inside the frame. Photorealistic architectural interior photography, visible oak grain, realistic
linen and cotton wrinkles, matte plaster texture, sharp focus, highly detailed.
AVOID: zen temple, stone lantern, bamboo grove, rock garden, orange toned wood, heavy timber
beams, cluttered decoration, fisheye distortion, bird's eye view, overexposed highlights, floating
furniture, missing window, missing door, wrong scale furniture, text, watermark, people.
```

**為什麼這樣寫**：主臥小、家具大，先寫「床邊走道 60cm」與「衣櫃到天花」，模型才會把床畫成合理尺寸；`no harsh light patches` 是無印風的靈魂（漫射不打射燈）。
**常見翻車與修法**：床畫成 king size 塞爆房間 → 補寫 `standard double bed, 152cm wide mattress`。

---

## C-05 主臥｜奶油風

**需求**：主臥想溫柔一點，圓角家具＋暖光，要有梳妝檯。

```
A photorealistic interior photograph of a master bedroom in a Taiwanese newly-completed apartment,
about 6 ping, with one aluminium-framed window on the left wall and a 210cm-high flush door on the
right, renovated ceiling height 250cm. Cream style interior, soft beige palette, rounded furniture,
warm cozy gentle light, low contrast tones. Floor is light oak wood flooring; walls are cream
textured paint with a softly rounded corner where the wall meets the wardrobe; the ceiling is flat
cream white with a concealed 2700K cove slot; a full-height handleless cream lacquer wardrobe with
rounded edges runs along the right wall; the headboard is an upholstered bouclé panel in oat white,
120cm high; a rounded oak dressing table 74cm high with a pill-shaped mirror sits under the window;
a plush cream rug, layered bedding in cream and milk tea tones, a curved bedside table and a small
ceramic lamp. Soft diffused daylight through sheer curtains plus 2700K warm ambient light, very
soft shadows, low contrast, tender and calm. Shot on a 24mm equivalent wide-angle lens at eye
level, camera height 120cm, one-point perspective, verticals kept straight. Photorealistic
architectural interior photography, realistic bouclé fabric texture, visible wood grain, matte
lacquer, sharp focus, highly detailed.
AVOID: overexposed white blowout, wedding photo studio look, pink tint, baby nursery, everything
rounded, plastic glossy furniture, arched window, fisheye distortion, bird's eye view, floating
furniture, missing window, missing door, text, watermark, people.
```

**為什麼這樣寫**：奶油風最常過曝變攝影棚，所以同時用正面詞 `low contrast` 與負面詞 `overexposed white blowout` 夾擊；弧形只指定在「牆與衣櫃交界」與「梳妝台、床頭櫃」，避免全室變圓。
**常見翻車與修法**：整張偏粉紅 → 補寫 `neutral cream, no pink or magenta tint, warm beige only`。

---

## C-06 廚房餐廳｜輕奢

**需求**：開放式廚房加中島，想要石紋＋金色細節但不要土豪。

```
A photorealistic interior photograph of an open-plan kitchen and dining area in a Taiwanese
newly-completed apartment, about 8 ping, with an aluminium-framed window behind the dining table
and a 210cm-high flush door to the left, renovated ceiling height 250cm. Light luxury interior,
refined proportions, understated opulence, cream and taupe palette with slim brass accents. Floor
is marble-look large-format porcelain tile; walls are suede-effect paint in warm taupe with a
fluted oak panel behind the dining area; the ceiling is flat white with a recessed 4000K neutral-white
linear task light over the island worktop; kitchen cabinetry is matte cream lacquer with slim brass edge trim and
smoked glass upper doors, upper cabinets set 70cm above the counter; the counter and the island
top are veined quartz 88cm high, the island is 180cm long with three upholstered bar stools; the
dining table is a stone-top table 75cm high with four fabric chairs and a sculptural brass pendant
hung 75cm above it. Warm evening interior lighting at 2700K with soft daylight still coming from
the window, gentle reflections on the stone, moderate contrast, elegant. Shot on a 24mm equivalent
wide-angle lens at eye level, camera height 120cm, two-point perspective from the corner of the
room, verticals kept straight, the whole island and the dining table fully inside the frame.
Photorealistic architectural interior photography, realistic stone veining that does not repeat,
brushed brass with matte finish, visible fabric texture, sharp focus, highly detailed.
AVOID: hotel lobby, casino interior, gold everywhere, oversized crystal chandelier, roman column,
baroque ornament, repeated marble texture tiling, plastic shiny surfaces, fisheye distortion,
bird's eye view, overexposed highlights, missing window, wrong scale furniture, text, watermark,
people.
```

**為什麼這樣寫**：輕奢的分寸在「金屬只做細邊」，所以寫 `slim brass edge trim`／`brushed brass with matte finish` 而不是 `gold`；石材加 `does not repeat` 直接擋掉貼圖重複。
**常見翻車與修法**：中島高度畫成餐桌高 → 明寫 `island top at 88cm, bar stools with 65cm seat height`。

---

## C-07 廚房餐廳｜中世紀現代

**需求**：餐廳區想走胡桃木＋芥黃，配一盞球型吊燈。

```
A photorealistic interior photograph of a dining area next to an open kitchen in a Taiwanese
newly-completed apartment, about 6 ping, with an aluminium-framed window on the right and a
210cm-high flush door behind, renovated ceiling height 250cm. Mid-century modern interior, walnut
veneer, tapered wooden legs, warm balanced palette with mustard and olive accents. Floor is walnut
wood flooring with visible grain; walls are warm white paint with a walnut slat feature wall
behind the sideboard; the ceiling is flat white; a low walnut sideboard with cane webbing doors on
tapered legs stands against the feature wall; a round walnut dining table 75cm high with four
mid-century dining chairs, a mustard fabric seat cushion, a geometric patterned rug; a white globe
pendant lamp 35cm in diameter hangs 75cm above the table top; a terrazzo top console holds a glass
vase; kitchen cabinetry in the background is warm white with a terrazzo countertop 88cm high.
Afternoon daylight from the right window, 3000K warm ambient lighting, warm balanced exposure,
soft shadows. Shot on a 26mm equivalent wide-angle lens at eye level, camera height 120cm,
one-point perspective, verticals kept straight, the entire table with all four chairs inside the
frame. Photorealistic architectural interior photography, visible walnut grain, realistic cane
webbing texture, terrazzo aggregate detail, sharp focus, highly detailed.
AVOID: retro diner, 1950s cafe, oversized chunky legs, over saturated primary colours, plastic toy
look, fireplace stone wall, sunken living room, fisheye distortion, bird's eye view, floating
furniture, missing window, text, watermark, people.
```

**為什麼這樣寫**：中世紀現代靠「細錐腳＋圓桌＋球燈」三件事成立，全部寫進去；吊燈高度 75cm 與桌高 75cm 分開寫，避免燈掉到桌面上。
**常見翻車與修法**：畫成美式復古餐館（紅皮卡座） → 加 `private residential dining area, not a restaurant` 並保留負面詞 `retro diner`。

---

## C-08 浴室｜工業風

**需求**：主浴 1.5 坪，想要黑鐵＋水泥感，乾濕分離。

```
A photorealistic interior photograph of a small master bathroom in a Taiwanese newly-completed
apartment, about 1.5 ping, with a black-framed glass shower partition separating the wet and dry
areas, one small aluminium-framed window with frosted glass, and a 210cm-high door, ceiling height
240cm. Industrial loft interior, concrete finish, black metal frame, matte black hardware, raw
texture contrast. Floor is grey microcement-look porcelain tile with a linear floor drain; walls
are board-formed concrete effect tile in the wet area and grey microcement paint in the dry area;
the ceiling is a flat moisture-resistant panel in dark grey with recessed downlights; the vanity is
a black steel frame with a solid wood top at 82cm holding a white ceramic vessel basin, a matte
black wall-mounted mixer, and open black metal shelving with folded towels; a large frameless
mirror with a slim black surround and a 4000K LED strip behind it for face-level task light. Warm amber accent lighting
plus neutral 4000K downlights, moderate contrast with visible texture in the shadows, no pitch
black areas. Shot on a 20mm equivalent wide-angle lens at eye level, camera height 120cm,
one-point perspective, verticals kept straight, the vanity and the shower partition both fully
inside the frame. Photorealistic architectural interior photography, realistic concrete texture,
matte black metal, water droplets on the glass, sharp focus, highly detailed.
AVOID: bar counter, cafe interior, warehouse storage, roller shutter door, pitch black room,
repeated brick texture tiling, rusty dirty surfaces, bathtub in a tiny bathroom, fisheye
distortion, bird's eye view, overexposed highlights, missing door, wrong scale fixtures, text,
watermark, people.
```

**為什麼這樣寫**：浴室最小、最容易透視爆掉，所以用 20mm 並明寫「梳妝台與淋浴隔間都要完整入鏡」；洗手台高度用 82cm（落在 80–85cm 正典內）。
**常見翻車與修法**：小浴室硬塞浴缸 → 負面詞已擋，若仍出現就補 `walk-in shower only, no bathtub`。消防或排煙相關要求若客戶問到，回「需確認」。

---

## C-09 玄關｜新中式

**需求**：玄關 1 坪，要落塵區＋鞋櫃＋一點東方味。

```
A photorealistic interior photograph of an entrance foyer in a Taiwanese newly-completed
apartment, about 1 ping, with the main entrance door on the right, a step-down entry tile zone
just inside the door, and an opening leading to the living room ahead, ceiling height 245cm.
Modern Chinese style interior, ink-wash mood, refined oriental, restrained ornament, symmetrical
composition. Floor is dark grey stone-look tile in the entry zone changing to dark walnut wood
flooring beyond the threshold; walls are rice-paper textured off-white paint; the ceiling is flat
off-white with a concealed 3000K light slot washing the screen; a full-height black walnut veneer
shoe cabinet with a lattice screen upper section runs along the left wall, with a floating open
niche at 85cm holding a celadon ceramic vase and a key tray, and a warm LED strip under the niche;
a slim wood-framed bench 45cm high sits beside it; a single vertical ink-wash painting without any
text hangs on the facing wall. Warm accent lighting at 2700K with soft daylight spilling from the
living room, one bright area and one quiet shadow area, calm and elegant. Shot on a 24mm
equivalent wide-angle lens at eye level, camera height 120cm, one-point perspective, verticals
kept straight, the whole cabinet wall inside the frame. Photorealistic architectural interior
photography, visible walnut grain, realistic ceramic glaze, subtle paper texture, sharp focus,
highly detailed.
AVOID: chinese restaurant, temple interior, dragon phoenix carving, heavy red and gold, palace
lantern, garbled chinese characters, any calligraphy text, costume drama set, fisheye distortion,
bird's eye view, floating furniture, missing door, text, watermark, logo, people.
```

**為什麼這樣寫**：新中式一定會被模型加假漢字，所以正面寫 `ink-wash painting without any text`、負面同時擋 `garbled chinese characters` 與 `any calligraphy text`。落塵區與 85cm 置物凹槽是台灣玄關的標準動作。
**常見翻車與修法**：格柵密到像牢籠 → 補 `lattice with wide 8cm spacing, only on the upper half of the cabinet`。

---

## C-10 書房｜美式鄉村

**需求**：小書房兼客房，要書牆＋工作桌，溫馨一點。

```
A photorealistic interior photograph of a small study that doubles as a guest room in a Taiwanese
apartment, about 3.5 ping, with one aluminium-framed window on the left and a 210cm-high door on
the right, ceiling height 245cm. American farmhouse interior, shaker cabinets, painted millwork,
cozy traditional, muted country palette. Floor is rustic oak wood flooring; walls are white board
and batten wainscot to 100cm height with warm off-white paint above; the ceiling is flat white
with a slim wood trim; a full-height sage green shaker-style bookcase with brushed nickel knobs
covers the right wall; a solid wood desk 74cm high with a spindle-back wooden chair sits under the
window with a brass desk lamp; a wall-mounted fold-down guest bed panel finished to match the
bookcase; a plain wool rug, cotton curtains, framed botanical prints without text, ceramic jars on
the open shelf. Warm afternoon daylight from the left window plus 2700K ambient light, even soft
illumination, homely and inviting. Shot on a 24mm equivalent wide-angle lens at eye level, camera
height 120cm, one-point perspective, verticals kept straight, the desk and the full bookcase wall
inside the frame. Photorealistic architectural interior photography, visible paint brush texture
on millwork, realistic wood grain, cotton fabric weave, sharp focus, highly detailed.
AVOID: baroque carving, roman column, ornate gold frame, over saturated yellow, rustic barn
exterior, fireplace with chimney, western saloon, cluttered antiques, fisheye distortion, bird's
eye view, overexposed highlights, missing window, text on the artwork, watermark, people.
```

**為什麼這樣寫**：美式鄉村在台灣的落地做法是「線板只做在櫃門與半牆」，所以明寫 `board and batten wainscot to 100cm`＋`shaker-style bookcase`，而不是整室木構；掛畫寫 `without text` 避免亂字。
**常見翻車與修法**：色調整體偏黃 → 加 `neutral white balance, no yellow colour cast`。

---

## C-11 小宅一室多用｜北歐風＋現代簡約混搭

**需求**：15 坪小宅，客廳、餐廳、工作區要在同一空間，還要能收納。

```
A photorealistic interior photograph of a compact 15-ping open-plan apartment interior in Taiwan
combining living, dining and a work corner in one space, with a full-height aluminium-framed
sliding window on the far wall, a 210cm-high flush door on the left, and a beam across the ceiling
concealed by a dropped soffit, renovated ceiling height 248cm. Scandinavian and modern minimalist
mix, light oak, warm off-white, clean geometry, space-enhancing layout, uncluttered. Floor is light
oak wood flooring running away from the camera to lengthen the room; walls are warm off-white matte
paint; the ceiling is flat white with a 3000K cove slot along the soffit; one continuous
full-height handleless light oak veneer storage wall runs from the entrance to the window, with a
recessed TV niche in the middle, a 45cm-deep desk section at 74cm height forming the work corner,
and closed doors elsewhere; a compact two-seat beige fabric sofa with 42cm seat height, a light
oak extendable dining table 75cm high with two chairs that also serves as a work surface, and a
window bench with hidden storage under the sliding window; main walkway kept at 90cm, everything
kept low so sightlines stay open. Bright daylight from the far window, soft even shadows, low
contrast, airy and visually enlarged. Shot on a 20mm equivalent wide-angle lens at eye level,
camera height 120cm, one-point perspective looking towards the window, verticals kept straight,
all three zones visible in one frame, nothing cropped. Photorealistic architectural interior
photography, visible oak grain, realistic fabric wrinkles, sharp focus, highly detailed.
AVOID: cluttered room, oversized furniture, partition walls chopping the space, dark colours,
western fireplace, skylight, fisheye distortion despite the wide lens, bird's eye view,
overexposed highlights, floating furniture, missing window, missing door, disappearing beam, text,
watermark, people.
```

**為什麼這樣寫**：小宅要「一面牆解決所有收納」，所以把儲藏牆寫成一條連續量體並在其中挖 TV 與書桌；地板方向寫 `running away from the camera` 是視覺放大的實招。
**常見翻車與修法**：20mm 常帶魚眼變形 → 負面已寫 `fisheye distortion despite the wide lens`，仍歪就退回 24mm 重出。

---

## C-12 招牌／文字渲染｜品牌調（含中文短詞）

**需求**：做一張門市或接待區的形象圖，牆上要有「如菓」兩個字的木質招牌。

```
A photorealistic interior photograph of a small design studio reception area in Taiwan, about 4
ping, with a 210cm-high glass entrance door on the right and an aluminium-framed window on the
left, ceiling height 260cm. Warm natural material palette: light oak, warm off-white plaster walls,
deep green accent. Floor is warm grey large-format matte porcelain tile; the feature wall behind
the reception counter is warm off-white textured plaster; the reception counter is light oak veneer
with a warm white solid surface top at 100cm; a deep green upholstered bench and a potted olive
tree sit to the side. Mounted centred on the plaster wall is a single flat solid oak signboard,
about 60cm wide and 24cm tall, with exactly two Traditional Chinese characters carved into it and
nothing else: 如 on the left and 菓 on the right, evenly spaced, in a clean modern sans-serif
form, the carved strokes finished in deep green. No other text, no letters, no numbers, no logo
anywhere in the image. Soft daylight from the left window plus warm 3000K accent light grazing the
signboard. Shot on a 35mm equivalent lens at eye level, camera height 120cm, one-point perspective
facing the sign wall, verticals kept straight, the whole signboard fully inside the frame and
sharply in focus. Photorealistic architectural interior photography, visible oak grain, crisp
carved edges, realistic plaster texture, sharp focus, highly detailed.
AVOID: garbled or invented Chinese characters, extra characters, mirrored or reversed characters,
simplified Chinese, English words, numbers, watermark, brand logos, fisheye distortion, bird's eye
view, overexposed highlights, people.
```

**為什麼這樣寫**：文字渲染要成功必須做三件事——寫出**確切字元**、寫出**字數**（exactly two characters）、寫出**每個字的位置**（左如右菓），並用 35mm 而非 24mm 讓招牌不被廣角拉歪（適用 20–28mm 的例外情境）。
**常見翻車與修法**：中文字缺筆、多筆、鏡像或變成簡體 → **每張出圖後逐字放大校對**（一個字一個字比對筆畫），錯了就改用「先出無字空招牌 → 再用 mask 只修招牌區域重寫文字」；同一個字連錯兩輪，改成留白招牌後製上字，不要無限重骰。

---

# D. 多角度一致（同一案 4 機位）

目標：同一個空間出 4 張不同角度，材質與家具必須看起來是同一間房。

**方法：materials block 逐字重用，只改 camera block。**

1. 先出第 1 張（主視角），確認材質與家具通過。
2. 把該 prompt 的 `[SPACE & SIZE]`、`[MATERIALS]`、`[LIGHTING]`、`[QUALITY]`、`[AVOID]` **一字不改複製**到第 2–4 張。
3. **只改 `[CAMERA]` 這一段**，並加一句 `SAME ROOM as the previous image, same materials, same furniture, same lighting; only the camera position changes.`
4. 若平台支援參考圖，把第 1 張當參考圖一起送（edit 端可帶多張，官方範例 4 張），一致性再提升一級。
5. 有 Thinking 模式（Plus／Pro／Business／Enterprise）時，**一次把 4 個機位一起交給 Thinking 出批次**，它會做版面推理與批次一致性；Instant 模式逐張出比較容易漂移。

**四機位標準組（住宅客餐廳）**

| 編號 | camera block 寫法 |
|---|---|
| V1 主視角 | `24mm equivalent, eye level 120cm, one-point perspective from the entrance looking towards the window, the whole TV wall and sofa in frame` |
| V2 反打 | `24mm equivalent, eye level 120cm, one-point perspective from the window looking back towards the entrance and the dining area` |
| V3 角落兩點 | `26mm equivalent, eye level 120cm, two-point perspective from the left corner, showing the TV wall and the side wall meeting` |
| V4 局部特寫 | `50mm equivalent, eye level 120cm, straight-on view of the TV wall niche and the cabinetry detail, shallow depth of field`（適用 20–28mm 的例外情境） |

**一致性檢核（4 張都要過）**：地板材質與拼法一致｜牆色一致｜櫃體門片與把手形式一致｜沙發布料與顏色一致｜光線方向與色溫一致｜窗戶數量與位置一致。任一項不一致 → 只重出那一張，不要整組重骰。

---

# E. 修圖不重骰

**核心句**：`Keep everything else exactly the same.` 每一次局部修改都必須帶上。

**規則**
1. **一次只改一項**。改地坪、改櫃體色、改燈具＝三次操作，不是一句話。
2. **只描述要改的那一項**，不要重述整間房。重述＝模型重新解讀整張圖＝重骰。
3. **有 mask 就用 mask**：mask PNG 與原圖**同尺寸**，**透明區＝要改的區域**，其餘不透明。mask 邊界貼著物件輪廓外 2–3 像素，太緊會出現接縫。
4. **保持透視與光線**：改材質時加 `match the existing perspective, lighting direction and colour temperature exactly`。
5. **改完立刻比對**：新舊兩張並排看窗、門、樑柱、天花線、家具位置有沒有偷偷變動。
6. gpt-image-2 預設高保真（input_fidelity 不可調），照理應保留原圖細節；若仍整張變樣，代表 prompt 寫太長把整張圖重新描述了——縮短 prompt 再試。

**常用修圖句型**

| 要改什麼 | 句子 |
|---|---|
| 換地坪 | `Change only the floor to light oak herringbone wood flooring with visible grain, laid running away from the camera. Match the existing perspective and lighting. Keep everything else exactly the same.` |
| 換櫃體顏色 | `Change only the colour of the built-in cabinetry to warm sage green matte lacquer, keeping the exact same cabinet shape, door divisions and handleless design. Keep everything else exactly the same.` |
| 換燈具 | `Replace only the pendant lamp above the dining table with a matte black globe pendant 35cm in diameter, hung 75cm above the table top. Keep everything else exactly the same.` |
| 調光線 | `Keep the entire scene identical and only change the lighting to warm 2700K evening ambience with the cove lighting on and the daylight reduced. Do not move any object.` |
| 移除物件 | `Remove only the floor lamp in the left corner and fill the area with the existing wall and floor finishes. Keep everything else exactly the same.` |
| 加物件 | `Add only one woven basket with a fiddle-leaf fig beside the right window, sitting on the floor with a correct contact shadow. Keep everything else exactly the same.` |

---

# F. 負面／禁止清單

本段分兩組：**F-1** 通用禁止清單（模式一／三用，含俯視類禁令）；**F-2** 模式二專用禁止清單（平面圖→3D 等角圖用，不含俯視類禁令）。**模式二一律用 F-2，不得誤用 F-1**——F-1 的 `bird's eye view`／`top-down view`／`high angle looking down`／`tilted verticals` 等禁令是為平視效果圖寫的，模式二要的正是 45 度俯角等角視，兩者直接衝突，誤用會一邊要求等角、一邊禁止俯視，出圖必然失敗且原因難查。

## F-1 通用禁止清單（模式一／三）

每張圖的 AVOID 段**至少**帶這一整組，再加 04 檔該風格的負面詞。

```
AVOID: western fireplace, chimney, skylight (unless explicitly requested), foreign power outlets
(UK or EU round-pin), radiators, basement stairs, exposed timber roof trusses, fisheye distortion,
warped perspective, tilted verticals, bird's eye view, top-down view, high angle looking down,
overexposed blown highlights, crushed pitch-black shadows, repeated tiling texture, obvious texture
seams, floating furniture not touching the floor, incorrect contact shadows, missing door, missing
window, disappearing beam, disappearing column, walls that do not meet the ceiling, wrong scale
furniture, doors taller or shorter than 210cm, oversized television, extra random text, garbled
letters or characters, watermark, signature, brand logo, people, human faces, pets, cluttered
random objects, cartoon or illustration style, CGI plastic look
```

**逐項為什麼（模型的已知偏誤）**

| 禁止項 | 為什麼要擋 |
|---|---|
| 西式壁爐 | 模型的室內訓練資料以歐美住宅為主，客廳幾乎必生壁爐；台灣住宅沒有 |
| 天窗 | 公寓樓層不可能有天窗，模型常自行加來補光 |
| 外國插座 | 英規三腳／歐規圓孔一出現，客戶一眼看出是假圖 |
| 魚眼／變形 | 廣角提示常誘發桶狀變形，必須同時要求 `verticals kept straight` |
| 鳥瞰／俯視 | 「看清楚整個空間」的需求容易被理解成俯瞰，破壞眼高 120cm 設定 |
| 過曝 | 「明亮」「大採光」提示常導致窗邊整片死白，細節全失 |
| 紋理重複 | 石材與磚牆最明顯，貼圖式重複一看就假 |
| 家具漂浮 | 缺接地陰影，家具像貼上去的 |
| 門窗消失 | 換風格時模型常把門或窗「順手」抹平 |
| 樑柱消失 | 台灣新成屋一定有樑柱，被抹掉＝圖不能施作 |
| 比例失真 | 沙發過大、門過矮、電視佔滿牆是最常見三種 |
| 多餘文字 | 亂字、假 logo、看不懂的招牌，交客戶必被抓 |

## F-2 模式二專用禁止清單（平面圖→3D 等角圖）

每則模式二 prompt 的結尾都帶這一整組（與 08 檔 C-6 同一份，兩檔互為正本備援）：

```
AVOID: western fireplace, chimney, skylight, attic, interior staircase, foreign power outlets (UK or
EU round-pin), radiators, text labels, dimension lines, room name text, watermark, added windows not
drawn in the plan, merged rooms, split rooms, relocated walls, doors opening into walls, repeated
tiling texture, obvious texture seams, floating furniture not touching the floor, wrong scale
furniture, people, human faces, pets, cartoon or illustration style, CGI plastic look
```

**逐項為什麼（F-2 新增項，未出現在 F-1 者）**

| 禁止項 | 為什麼要擋 |
|---|---|
| 室內樓梯 | 平面圖是單層平面，模型會誤以為是透天而補樓梯 |
| 文字標籤、尺寸線、房間名文字 | 平面圖上的中文字最容易被原樣畫進成果圖，是模式二最常見的災情 |
| 加窗（原圖沒有的） | AI 最愛替暗房補光，這是格局跑掉的頭號原因 |
| 併房間、切房間、移牆 | 模型會為了畫面「合理」而重整格局 |
| 門開在牆上 | 門洞位置沒鎖住時的典型錯誤 |

其餘項目（壁爐／煙囪／天窗／閣樓／外國插座／暖氣片／紋理重複／家具漂浮比例失真／人物寵物／卡通塑膠感）理由與 F-1 同表一致，不重複列。

---

# G. 交付前自檢（每張圖都跑）

1. 相機：眼高像 120cm 嗎？垂直線有沒有歪？有沒有魚眼？
2. 尺度：門看起來 210cm 嗎？沙發座高、檯面高、走道寬合理嗎？
3. 結構：窗、門、樑柱、天花線是否與需求（或原始照片）一致？
4. 材質：是不是超過五種？有沒有明顯重複貼圖？
5. 台灣感：有沒有偷渡壁爐、天窗、外國插座、暖氣片？
6. 文字：畫面有沒有多餘文字？招牌任務是否**逐字校對過筆畫**？
7. 誠實標註：概念圖必附「本圖為概念示意，格局為假設值，實際以現場丈量與圖說為準」；保格局換風格若有任一項跑掉，明講是哪一項，**不得宣稱格局保留**。
8. 法規類（消防、無障礙、逃生）數字若無明確來源，一律回「需確認」，不寫進圖說也不寫進說明。

---

# H. 已驗證寫法（由 07 回寫）

本區分兩塊：**H-1** 是 07_過關圖回寫紀錄表每 10 筆小結後回寫的實戰措辭庫（尚無回寫紀錄前留空）；**H-2** 是 2026-08-19 從報告①《提升 ChatGPT 室內設計生圖能力》第五節「16 條方法論」中，篩出屬於 **prompt 寫法**（非工具安裝、非成本追蹤、非資產管理）的條目，先行併入本檔當寫法庫的起手式。與本檔既有 A–G 段重複的條目（已落地者）只標「已落地」與對應段落，不重寫內容。

## H-1 07 回寫措辭庫

（尚無回寫紀錄）

## H-2 報告①方法論萃取（prompt 寫法類，2026-08-19 併入）

| # | 技巧 | 怎麼落到提示詞 | 出處 repo | 本檔對應 |
|---|---|---|---|---|
| 1 | 提示詞用五段式，不寫成一段散文 | 任務類型／主體描述／風格定義／技術參數／輸出規格五段各自獨立成句；同案換風格時只改第三段（風格），其餘不動，出圖差異才可歸因 | xianyu110/awesome-gptimage2；freestylefly/awesome-gpt-image-2 | A 段九個 block 已是同一精神的落地版，換風格只動 [STYLE] 與 [MATERIALS] 兩個 block |
| 2 | 先講空間，再講畫面 | 先用文字把格局、動線、家具位置與朝向講清楚，再要求出圖；把「佈局」當獨立條件而非形容詞 | ZGCTroy/LayoutDiffusion；aminshabani/house_diffusion | 已落地：A 段 [SPACE & SIZE]／[LAYOUT — KEEP] 固定排在 [LOCK] 之後、[STYLE] 之前，見 A-3 第 8 條 |
| 3 | 能給參考圖就別從零生成 | 現場實景照當條件輸入，模型只負責換材質與陳設，不負責重新想像格局 | lllyasviel/ControlNet；Nutlope/roomGPT | 模式一之二 已落地（走 edit、不可用純文生圖冒充） |
| 4 | 局部要改就用遮罩，別整張重生 | 只框出要改的區域送編輯端點，其餘畫素原封不動；整張重生會連客戶已點頭的部分一起改掉 | alasano/gpt-image-playground；ControlGenAI/MaterialFusion | 模式三 做法 A、E 段已落地 |
| 5 | 材質詞要連光一起寫 | 「霧面橡木」單獨寫沒有用，要連同光從哪來、反射強弱一起描述；材質的說服力來自光而不是名詞 | ControlGenAI/MaterialFusion；astra-vision/MatSwap | 已落地：A-3 第 7 條，MATERIALS block 每項材質後面至少接一句光照描述（例如 `light oak flooring, catching soft daylight from the left window with visible grain highlights`），不得只寫材質名詞 |
| 6 | 同一空間多視角，要鎖住不變量 | 提示詞用固定句段複述不可變元素（開窗位置、地坪材質、主色），每個視角只換鏡頭描述 | River-Zhang/ICEdit；hzxie/Awesome-3D-Scene-Generation | D 段「materials block 逐字重用，只改 camera block」已落地 |
| 7 | 寫實感靠攝影語彙，不靠形容詞堆疊 | 鏡頭焦段、時間、光源方向、景深這類攝影參數，比「高級」「溫馨」這類形容詞更能穩定出圖品質 | ZeroLu/awesome-gpt-image；jamez-bondos/awesome-gpt4o-images | CAMERA／LIGHTING block 已用攝影語彙；**提醒**：STYLE block 出現「高級」「溫馨」這類詞時，優先換成對應的鏡頭／光源／景深描述 |
| 13 | 用一段「不可違反」的主提示詞鎖住空間骨架 | 每則室內提示詞最前面固定放同一段話：牆體位置、開窗位置與大小、相機角度與鏡頭高度一律不得更動，只准更換材質、燈光與家具陳設；這段話不隨案子改寫，改的只有後面的風格段 | zyliu0/interior-design（補掃） | 已落地：A 主模板新增 `[LOCK]` block（九個 block 之首），定稿句逐字固定、每則 prompt 最前面都貼，對應 01 檔 §0 共用鐵則一 |
| 14 | 改圖分三段講：先移除、再繪製、最後才是可選項 | 把改圖指令拆成「要移除什麼」「一定要畫成什麼」「哪些是可選的加分項」三段分別寫，混在一句會讓模型把可選項當必要項 | amir84ferdos/ComfyUI-ArchAi3d-Qwen（補掃） | 模式三、E 段目前是「一次只改一項」的單項句，尚未拆三段；**新規則**：局部修改若同時牽涉「拿掉舊物件＋放新物件＋可選裝飾」，一律拆成 REMOVE／DRAW／OPTIONAL 三行分寫，不混在一句 |
| 15 | 材質先建分類表，再寫進提示詞 | 常用材質先依大類（石材／木皮／金屬／織品／塗裝）建成固定清單並統一命名，寫提示詞時直接引用清單名稱，不臨場想形容詞 | amir84ferdos/ComfyUI-ArchAi3d-Qwen（補掃） | 材質五大類命名框架見本檔 B-4（待補齊品項名稱），完整詞彙正本查 02 檔材質詞彙表 |

未列入本表的第 8、9、10、11、12、16 條屬工具安裝／成本追蹤／資產管理／官方參數對帳類，不是 prompt 寫法，第 8、16 條的重點另收在下方 I 段，第 9–12 條收在內部 10_附錄（不上傳 ChatGPT）。

---

# I. 官方 prompting guide 要點（2026-08-19 併入）

出處：報告①第五節第 8、16 條與六節「甲堆」，摘自 openai/openai-cookbook 官方生圖範例與 wuyoscar/GPT-Image2-Skill 的官方指南逐字備份（約 1,004 行）。本段只摘要點，不抄長文；兩者衝突一律以 openai-cookbook 官方原文為準，wuyoscar 備份僅作對照。

1. **用攝影語言，不用情緒形容詞**：鏡頭焦段、光源方向、景深這類攝影參數，比「高級」「溫馨」更能穩定出圖（對應 H-2 第 7 條）。
2. **四個獨立條件分開寫**：framing（框取範圍）、viewpoint（視點）、perspective（透視型式）、lighting mood（光線氛圍）各自成句，不要混進同一句形容詞裡——本檔 CAMERA／LIGHTING 兩個 block 已是這個精神的落地版。
3. **明確要求真實質感**：布料皺褶、木紋、材質磨損這類詞要直接寫進 prompt，模型不會自動補上——對應本檔 QUALITY block。
4. **清楚區分「該變」與「必須不變」**：官方指南把這點列為編輯任務的第一原則，對應本檔 `[LAYOUT — KEEP]` 與 `CHANGE ONLY` 兩段的寫法。
5. **參數會實質改變出圖結果，不能只在文字上打轉**：quality（low/medium/high/auto）、size（16 的倍數、長寬比 1:3–3:1）、input_fidelity（高保真、不可調）、n（一次張數）每案至少對照官方參數表打勾一次；漏用參數比再改十版文字更常是翻車主因（H-2 第 16 條）。
6. **五段式骨架是官方範例的共通寫法**：任務類型 → 主體描述 → 風格定義 → 技術參數 → 輸出規格，本檔 A 段九個 block 是這個骨架的室內設計加長版。

---

# J. 平面圖→3D 快速入口

使用者上傳的是**平面圖／格局圖**，或需求是「變立體、看格局、全戶圖、等角圖」時，**不要用本檔 A/B/C 段的平視 prompt**——一律轉查 **08_知識檔_平面圖轉3D流程與prompt**。

一句話流程：先用中文複述格局（房間數、相對位置、牆門窗位置、無法確定處）→ 使用者核對確認 → 確認後才用 08 檔的英文 prompt 出 45 度等角剖視圖，屋頂移除、牆高預設 2.8m。生圖前不生圖、複述未確認不得動筆，是模式二與模式一／三最大的差異。
