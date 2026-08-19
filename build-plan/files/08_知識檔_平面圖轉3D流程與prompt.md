# 08 知識檔｜平面圖轉 3D：流程與 prompt（模式二專用）

本檔用途：使用者上傳的是**平面圖／格局圖**，或要求「變立體、看格局、全戶圖、等角圖、剖視圖」時，一律照本檔執行。本檔是模式二的唯一正本。

使用方式：先讀 A 段（能力邊界，決定要不要先跟使用者講清楚）→ 照 B 段七步走 → 從 C 段挑一條 prompt 貼用 → 用 D 段決定視角 → 交付前跑 E 段驗收 5 問 → 附上 H 段的交付附註句。

分工路由（不要在本檔找這些）：
- 模式一（效果圖／概念圖）與模式三（局部修改）的 prompt 與模板 → 查 **05 檔**。
- 材質中英文名稱與質感寫法 → 查 **02 檔**。
- 台灣住宅尺度、家具尺寸、鏡頭幾何 → 查 **03 檔**。
- 十種風格的關鍵詞、色票 → 查 **04 檔**；負面詞不查 04（04 的「共用禁止清單」含俯視類禁令，與模式二衝突，模式二一律只用本檔 C-6 的 F-2）。
- 參考圖（實景照／風格圖）用法 → 查 **06 檔**；上傳的是平面圖時就用本檔。

---

# A. 能力邊界：先講清楚，再動手

出圖前若使用者說「我要 3D 模型」「要能旋轉」「要照著施工」，先用一句話說明本節 A2，再繼續。不要讓使用者誤以為拿到的是模型。

## A1. 做得到
- 把一張 2D 平面圖，變成一張**看起來立體**的等角俯視圖或剖視渲染圖，含家具、地板材質、光影，數十秒出圖。
- 同一戶可換方位再出圖（前左／前右／後方 45 度），用於提案封面、客戶溝通、社群圖卡。
- 格局確認後可繼續調材質與光線，且能與模式一的單房效果圖共用同一組材質描述。

## A2. 做不到（要主動講）
- 出的是**一張圖片**，不是可旋轉、可量測、可匯出的 3D 模型。
- 沒有工程級尺寸；家具比例是視覺估計，不是實測。
- 不含水電、結構、消防資訊。
- 不得作為施工、估價或請照依據。

## A3. 保格局的三要件（缺一就會出錯）
1. **原圖線條乾淨**：正上方拍攝或建商電子檔，沒有尺寸線、圖例、浮水印等標註雜訊。
2. **prompt 逐項鎖住**：外框／隔間／門洞／窗洞／房間數／相對比例，六項要一一寫出來，不能只寫 keep the layout。
3. **生圖前先用文字複述一次格局**：由使用者確認無誤後才生圖。

三者缺一，就會出現自行加窗、把兩間房併成一間、誤讀廚房線條等錯誤。這不是機率問題，是已知行為。

## A4. 已知的自作主張（要預先擋掉）
- 替沒有窗的暗房加窗（最常見）。
- 把相鄰兩個小空間併成一間，或把一間切成兩間。
- 誤讀廚房的檯面線、櫥櫃線，當成牆。
- 把平面圖上的中文字（房間名、案名、尺寸標註）直接畫進成果圖。
- 加入台灣住宅不會有的壁爐、天窗、閣樓、室內樓梯。
- 天花板比例錯誤、窗戶開向錯置。

---

# B. 標準流程（七步，順序不可調換）

順序反了的代價：先調材質再確認格局，等於連格局一起重擲，前面的核對全部作廢。

## 第 1 步　準備平面圖（前處理）

要求使用者提供的圖，逐項檢查：

| 檢查項 | 要求 |
|---|---|
| 來源 | 建商電子檔優先；只有紙本才拍照 |
| 拍攝 | 正上方拍攝、四角入鏡不歪斜。斜拍會變梯形，梯形會被當成真的格局。歪了重拍，不要用軟體硬拉 |
| 清雜訊 | 刪掉尺寸線、標註、圖例、公司浮水印、案名、指北針以外的裝飾框 |
| 保留 | 牆線、門洞、窗、房間名稱、比例尺（若有） |
| 清晰度 | 牆線與門洞開口要看得出粗細差異；模糊到分不清門與窗，就要求重拍或重出檔 |
| 個資 | **上傳前先遮蔽地址、屋主姓名、建案名稱、建商標章** |

清圖有一條紅線：**寧可留一點雜訊，也不要把門洞或窗一併清掉**。清過頭比沒清更糟。

若使用者給的是手繪或翻拍的髒圖、無法辨識，就直接說明「這張圖線條無法判讀，請補一張正上方拍攝或建商電子檔」，不要硬猜。

## 第 2 步　標比例尺與主要尺寸

沒有實際尺度，3 坪的浴室會被畫成飯店規格。請使用者補一句（照抄句）：

> 這是一戶台灣公寓，室內約 __ 坪（__ 平方公尺），天花板高 2.8 公尺，主臥約 __ × __ 公尺。

使用者答不出來時：天花高預設 2.8 公尺（台灣 RC 公寓常見樓板高），並在回覆中標明「天花高採預設 2.8 公尺，需確認」。坪數與主臥尺寸未給就直接問，不要自行假設。

## 第 3 步　先分析、不生圖（本流程最關鍵的關卡）

上傳圖後的**第一則回覆不得出現任何圖片**。逐字送出下面這段中文 prompt（即 C 段 P-2 第一段）：

```
請先分析這張平面圖，不要生成圖片。請列出：
1. 房間總數與各房間用途。
2. 每個房間的相對位置。
3. 牆面、門洞與窗戶位置。
4. 你無法確定或線條含糊的地方。
不要自行補上原圖沒有標示的門、窗、牆或房間。
```

### 複述應該長成的格式（照這個格式回，不要寫成散文）

```
一、房間總數與用途
　共 6 個空間：客廳、餐廚、主臥、次臥 A、次臥 B、衛浴 ×2（主衛、客衛）。

二、相對位置
　入口在圖面下方（南側）；玄關進門左手為客衛，右手為餐廚。
　客廳位於中央偏南，餐廚在客廳西側並相連。
　主臥在圖面右上（東北），次臥 A 在左上（西北），次臥 B 在左下（西南）。
　主衛附屬於主臥，開口朝主臥內側。

三、牆面、門洞與窗戶
　外牆開窗 4 處：客廳南向落地窗 1、主臥東向窗 1、次臥 A 北向窗 1、餐廚北向窗 1。
　門洞 7 處：入戶門 1、房門 3、衛浴門 2、餐廚無門（開放）。
　主臥與次臥 A 之間為一道連續隔間牆，中段無開口。
　圖面中央偏北有一道短牆，兩側各接一支柱。

四、無法確定的地方
　1. 餐廚北側那條雙線，可能是窗也可能是櫥櫃立面線，需確認。
　2. 次臥 B 西側靠外牆處有一小段折線，可能是收納櫃或包管，需確認。
　3. 陽台與室內的分界線未標示落地門位置，需確認。
```

規則：
- 第四項「無法確定的地方」**一定要有內容**。全部都確定＝沒有認真讀圖，重讀一次。
- 不確定的地方一律列出來問，**不得自行補上原圖沒有的門、窗、牆或房間**。
- 若圖面標示的房間名與用途矛盾（例如標「書房」但畫了衛浴設備），列進第四項，不要自己選一個。

## 第 4 步　核對複述，錯了當場糾正

把複述交給使用者逐條核對。使用者指正時的處理：只重列被指正的那幾項，不要整份重寫。

糾正的句型（給使用者參考）：

> 錯了，餐廳在客廳**右側**不是左側；北面那道牆**沒有窗**。請重新列一次。

**複述未被確認之前，不得生圖**。使用者若直接說「不用分析了，直接畫」，仍要回一句：「我先用文字列一次格局，30 秒，確認過再畫可以省掉重畫。」列完再畫。

## 第 5 步　生圖（選版本）

依用途從 C 段挑：

| 用途 | 用哪一條 | 特徵 |
|---|---|---|
| 第一次試水溫、單一房間或簡單戶型 | **P-1** | 一句話直出、失敗成本低 |
| 客戶提案（標準做法） | **P-2 第二段** | 有家具、暖材質、保格局措辭最完整 |
| 提案封面、社群圖卡 | **P-3** | 迷你建築模型感、畫面乾淨無文字 |
| 工地與工程溝通 | **P-4** | 無家具、標牆高、承重牆與輕隔間分色 |
| 自製新 prompt 的地基 | **P-5** | 官方骨幹句，四行短版 |

送出時開頭固定加一句：「依照剛才你確認的格局生成。」再貼英文 prompt。

## 第 6 步　人眼把關，指名修

把生成圖與原平面圖並排，照 E 段驗收 5 問逐項比對。發現錯誤要**指名修**，不要籠統說「格局不對」，也**不要整張重生**（重生等於重擲，會連對的地方一起換掉）。

指名修的句型：

> 主臥和次臥之間的隔間牆不見了，請補回；南面陽台你多畫了一扇窗，原圖沒有，請移除。其他不要動。

修完再跑一次驗收 5 問，逐項回答，不得籠統說「已修正」。

## 第 7 步　補材質、出多視角、定稿

格局全過之後才動材質與光線。順序反了會連格局一起重擲。

> 格局維持不變，只把地板換成淺橡木、牆面換成米白，其餘完全不動。

多視角只換方位句（見 D 段），其餘 prompt 一字不動。定稿前再跑一次驗收 5 問。

---

# C. 五條可複製 prompt（如菓版）

以下五條英文皆為**如菓自製改寫草稿、尚未實測**；每條下方附來源網址，方便回頭覆核。原版英文逐字內容不重複收錄於本檔，見報告②03 節（五條原版與如菓版逐字比對，5/5 exact match），本檔只收如菓版以免混用。改寫加了三件事：台灣住宅尺度（天花 2.8 公尺）、視角設定（45 度等角剖視、屋頂移除）、以及排除台灣住宅沒有的壁爐／天窗／閣樓／室內樓梯。

實測通過後，才可以把「未實測」改成「已實測（日期）」。

---

## P-1　一句話直出：試水溫首選

- **原版出處**：awesome-gpt4o-images — Example 20: Floorplan to 3D Rendering
  https://github.com/jamez-bondos/awesome-gpt4o-images/blob/main/gpt-image-1/gpt-image-1-en.md
- **適用情境**：第一次試、單一房間或簡單戶型、只要一張有氣氛的示意圖。
- **輸入要求**：一張 2D 平面圖。來源標示的參數為 quality=high、size=1536×1024（走 API 的設定；網頁版直接上傳即可）。
- **已知弱點**：示範以簡單戶型為主，複雜大戶型未見驗證；短句約束少，格局跑掉時沒有補救條款。複雜戶型請改用 P-2。

**如菓版（自製草稿，未實測）**

```
Create a super realistic 3D rendering of this Taiwanese apartment floor plan. Do not change the
positions of the walls; maintain all wall lines, door openings and window openings in the exact same
position as they are in the plan. Ceiling height 2.8 m, typical Taiwan urban apartment scale. Show
the unit as an isometric cutaway from a 45-degree top-down camera, roof removed. Add furniture,
finishes, textures and depth. Do not add fireplaces, skylights, staircases, or any balcony or window
that is not drawn in the plan.
```

---

## P-2　兩段式保格局：對客戶出圖的標準做法（本檔核心）

- **原版出處**：ChatGPT 2D 平面圖轉 3D 裝潢圖教學：Prompt 與限制
  https://www.aiposthub.com/chatgpt-2d-floor-plan-to-3d-interior-render/
- **適用情境**：要交給客戶看的全戶等角剖視圖，格局不能錯。**這是預設做法**，沒有特別指定就用這條。
- **輸入要求**：建商電子檔或正上方拍攝的高清平面圖（避免梯形變形），牆線／門洞／房間名稱清楚；上傳前先遮蔽地址、姓名、建案名稱等個資；訊息裡補上坪數與天花高。
- **已知弱點**：原文作者自己實測仍發生「AI 自行加窗、誤讀廚房線條」；產出仍是靜態圖，不是模型。所以第 6 步的人眼把關不能省。
- **為何用它**：保格局措辭最完整——一次鎖住外框／隔間／門洞／窗洞／房間數／相對比例／動線，再用 add／remove／merge／rotate／mirror／relocate 六個動詞封死。

**第一段（先分析、不生圖；中文逐字送出）**

```
請先分析這張平面圖，不要生成圖片。請列出：
1. 房間總數與各房間用途。
2. 每個房間的相對位置。
3. 牆面、門洞與窗戶位置。
4. 你無法確定或線條含糊的地方。
不要自行補上原圖沒有標示的門、窗、牆或房間。
```

**第二段（確認無誤後才生圖）如菓版（自製草稿，未實測）**

```
Use the uploaded 2D floor plan as the authoritative geometry reference. This is a Taiwanese apartment
unit; ceiling height is 2.8 m and the total floor area is about [__] m2. Convert it into a
photorealistic 3D architectural cutaway render, roof removed, seen from a slightly tilted top-down
isometric camera (about 45 degrees). Strictly preserve the exact outer footprint, wall geometry,
internal partitions, door openings, window openings, room count, room positions, relative room
proportions, and circulation shown in the input. Do not add, remove, merge, rotate, mirror, or
relocate any room, wall, door, or window. Do not add fireplaces, skylights, or attic spaces. Furnish
each room according to its label at realistic Taiwanese residential scale. Use warm natural materials
(light oak flooring, off-white walls) and realistic daylight from the drawn windows only.
```

`[__]` 填實際平方公尺（坪數 × 3.3058，四捨五入到整數）。使用者只給坪數就換算後填入，並在回覆中寫明換算後的數字。

---

## P-3　迷你建築模型感：全戶等角圖

- **原版出處**：easy-peasy.ai — 3D Isometric Architectural Floor Plan Render
  https://easy-peasy.ai/ai-image-generator/images/top-down-fully-3d-isometric-bbf412de-ba3c-45ef-827d-f5a01c741605
- **適用情境**：提案封面、社群貼文主圖，要一張乾淨的全戶「建築模型」風格圖。
- **輸入要求**：整層平面圖，建議先移除文字標籤（prompt 內雖然已寫 Remove all text labels，圖面先清乾淨更保險）。
- **已知弱點**：原頁範例並非以 ChatGPT 產出，且只有單張範例、無法驗證格局保真度。用它出圖仍要跑驗收 5 問。
- **為何用它**：`miniature architectural maquette`（迷你建築模型）這個定錨詞，比講 3D render 更能逼出乾淨的等角全戶模型感；內建 Remove all text labels，直接解掉「平面圖上的中文字被畫進圖裡」這個常見災情。

**如菓版（自製草稿，未實測）**

```
Top-down, fully 3D isometric render of this entire Taiwanese apartment floor plan. Create a clean,
highly detailed miniature architectural maquette with accurate room proportions and layout, matching
the reference exactly. Wall height 2.8 m. Remove all text labels and dimension lines. Keep every wall,
door opening, window opening, appliance and room in the position drawn; do not add fireplaces,
skylights or rooms that are not in the plan. Furnish each room at realistic Taiwanese residential
scale—sofas, beds, dining tables, wardrobes, lamps, plants, rugs, kitchen appliances—arranged
realistically and in scale. Photorealistic materials (light oak flooring, porcelain tile, fabric,
glass). Soft global lighting, subtle shadows, crisp edges.
```

---

## P-4　參數化填空模板：工程溝通用

- **原版出處**：Convert 2D Floor Plan to 3D in Seconds（2026-05-26）
  https://edrawmax.wondershare.com/ai-tips/2d-floor-plan-to-3d-nano.html
- **適用情境**：工地與工程溝通。要的是格局與牆體清楚，不是美圖。
- **輸入要求**：清理過的 2D 平面圖（去掉註記與網格）、明確天花板高度。
- **已知弱點**：來源頁無實際成果圖佐證；作者自承常見版面混亂、天花板比例錯誤、窗戶方向錯置。工程溝通版對格局的要求最嚴，一致率要求 100%（見 E2）。
- **同骨架換角色**：同一份骨架換變數即可衍生設計師版（指定風格／家具／地板／牆色）、代銷版（強調亮度與家具配置）、翻新版（展示更新後配置）。只換變數，不換句構。

**如菓版（自製草稿，未實測）**

```
Convert this 2D floor plan into an isometric 3D visualization. Show the structure without a roof to
reveal the interior layout. Wall height is 2.8 meters (typical Taiwan RC apartment). Display all
structural RC walls and columns in gray concrete texture; show light-gauge partition walls in white.
Include door swings and window placements exactly as shown, and do not add any door, window, skylight
or fireplace that is not drawn. View from the [front-left / front-right / rear] corner at 45 degrees.
Use a technical architectural style with neutral colors. No furniture. No decorative elements. Label
nothing.
```

方括號三選一，其餘不動。

---

## P-5　官方骨幹句：自製 prompt 的地基

- **原版出處**：OpenAI Cookbook — image-gen-models-prompting-guide（section 5.3）
  https://github.com/openai/openai-cookbook/blob/main/examples/multimodal/image-gen-models-prompting-guide.ipynb
- **適用情境**：所有自製 prompt 的骨幹；也適用手繪草圖轉寫實圖。
- **輸入要求**：任意草圖或平面圖。
- **已知弱點**：**該 notebook 全文從未提平面圖**，是通用草圖轉圖；套用到平面圖屬合理外推，不是官方對平面圖的背書。單獨使用時約束偏少，複雜戶型仍以 P-2 為準。
- **為何用它**：官方認可的「保留佈局」標準句式，最後一句 Do not add new elements or text 直接對治 AI 亂加門窗與亂寫字。

**如菓版（自製草稿，未實測）**

```
Turn this floor plan into a photorealistic isometric cutaway image of a Taiwanese apartment interior.
Preserve the exact layout, wall positions, door and window openings, and relative proportions.
Wall height 2.8 m; camera 45 degrees top-down; roof removed.
Choose realistic materials and daylight consistent with the plan's window positions.
Do not add new elements, rooms, fireplaces, skylights, or text.
```

---

## C-6　模式二專用禁止清單（F-2）

**模式二一律用本清單，不得沿用 05 檔的 F-1 通用清單，也不得套用 04 檔「四、共用禁止清單」。** F-1 與 04 的共用禁止清單都內含 bird's eye view／top-down view（04 另有 high angle looking down／tilted verticals 等俯視類禁令），那是為平視效果圖寫的；模式二要的正是 45 度俯角等角視，兩者直接衝突，誤用會一邊要求等角、一邊禁止俯視，出圖必然失敗且原因難查。04 檔的色票與材質詞仍可查，但負面詞一律不取 04、只用本節 F-2。

每則模式二 prompt 的結尾都帶這一整組：

```
AVOID: western fireplace, chimney, skylight, attic, interior staircase, foreign power outlets (UK or
EU round-pin), radiators, text labels, dimension lines, room name text, watermark, added windows not
drawn in the plan, merged rooms, split rooms, relocated walls, doors opening into walls, repeated
tiling texture, obvious texture seams, floating furniture not touching the floor, wrong scale
furniture, people, human faces, pets, cartoon or illustration style, CGI plastic look
```

**逐項為什麼**

| 禁止項 | 為什麼要擋 |
|---|---|
| 西式壁爐、煙囪 | 訓練資料以歐美住宅為主，客廳幾乎必生壁爐；台灣住宅沒有 |
| 天窗、閣樓 | 公寓樓層不可能有，模型常自行加來補光或填空 |
| 室內樓梯 | 平面圖是單層平面，模型會誤以為是透天而補樓梯 |
| 外國插座、暖氣片 | 一出現就一眼看出是假圖 |
| 文字標籤、尺寸線、房間名文字 | 平面圖上的中文字最容易被原樣畫進成果圖，是模式二最常見的災情 |
| 浮水印 | 建商圖檔的浮水印會被當成圖案畫進去 |
| 加窗（原圖沒有的） | AI 最愛替暗房補光，這是格局跑掉的頭號原因 |
| 併房間、切房間、移牆 | 模型會為了畫面「合理」而重整格局 |
| 門開在牆上 | 門洞位置沒鎖住時的典型錯誤 |
| 紋理重複、接縫 | 地板與磚牆最明顯，等角圖大面積地坪尤其容易露餡 |
| 家具漂浮、比例失真 | 等角視最容易看出家具沒接地與比例錯誤 |
| 人物、寵物 | 提案圖出現陌生人臉，客戶會分心也會質疑 |
| 卡通感、塑膠感 | 模型感要來自 maquette 定錨詞，不是塑膠質感 |

## C-7　不得使用

網路上流傳的一份「floor-plan-3d-visualization（Pipedream 自動化）系統 prompt」不得採用。理由：其所謂英文原文其實是中文摘要重寫（引文裡夾著中括號中文註解），非原始字串，且來源內容藏在壓縮檔內、外部無法覆核，照抄無效。
（該來源：https://github.com/vinjamurigowtham999-ops/floor-plan-3d-visualization ，列此僅供辨識，不供使用。）

---

# D. 視角規格與多視角一致

## D1. 三種視角規格

| 規格 | 英文定錨句 | 用途 | 屋頂 | 家具 |
|---|---|---|---|---|
| **等角俯視（預設）** | `slightly tilted top-down isometric camera, about 45 degrees` | 全戶格局溝通、客戶提案 | 移除 | 有 |
| **娃娃屋剖視** | `photorealistic 3D architectural cutaway render, roof removed, walls cut at 2.8 m` | 要看到牆高與空間感，比等角更有立體厚度 | 移除 | 有 |
| **單房透視特寫** | 見 F 段（銜接模式一） | 單一空間的氣氛與材質 | 不適用 | 有 |

三者共通：**牆高一律 2.8 公尺**（除非使用者另給實際值）。模式二不套用模式一的眼高 120cm 與 24mm 焦段規定——那是平視效果圖的參數，等角圖不適用。

工程溝通用 P-4 時，視角維持 45 度、不加家具、不加裝飾、不寫任何文字。

## D2. 方位句（多視角只換這一句）

```
View from the front-left corner at 45 degrees.
View from the front-right corner at 45 degrees.
View from the rear at 45 degrees.
```

## D3. 多視角一致的三條規則

1. **只換方位句，其餘 prompt 一字不動**。材質段、格局約束段、禁止清單全部逐字沿用。
2. **不重新解讀平面圖**。換視角時不要回到第 3 步重新複述格局，也不要重新上傳平面圖——那等於重擲。
3. **每一張都要重跑驗收 5 問**，不得只驗第一張。換視角是格局最容易漂移的時刻。

多視角出現不一致時：以已通過驗收的那張為基準，指名修不一致的那張（「這張的餐廚位置和前一張不同，餐廚應在客廳西側，請修正，其他不要動」），不要三張全部重生。

一次提案建議最多四張：全戶等角 1 張＋換方位 1 張＋主要空間透視 2 張。超過四張，一致性的維護成本會高於效益。

---

# E. 驗收與失敗修法

## E1. 驗收 5 問（每張圖交出去前都問一次，逐項作答）

1. **房間數對嗎？** 原圖幾間房、幾套衛浴，圖上就要是幾間，沒有被併也沒有被多切。
2. **隔間牆位置與相對比例對嗎？** 客廳與餐廳誰大誰小、主臥在哪一側，與原圖一致。
3. **門洞與開啟方向對嗎？** 有沒有憑空多一道門，或把門開在承重牆上。
4. **窗戶只出現在原圖有窗的位置嗎？** 這是最常見的錯誤，AI 很愛替暗房加窗。
5. **有沒有台灣住宅不會有的東西？** 壁爐、天窗、閣樓、室內樓梯——有就是自己加的，必須移除。

**五問全過才算完成。任一不過，回到第 6 步指名修，不要整張重生。**

回答格式（不得只寫「已通過」）：

```
驗收 5 問
1 房間數：6/6 通過（3 房 2 衛 + 客餐廚）
2 隔間與比例：通過（主臥在東北、客廳居中，與原圖一致）
3 門洞與開向：通過（7 處門洞全對，開向與原圖一致）
4 窗戶：不通過——次臥 B 西側多一扇窗，原圖無 → 已指名移除，見下一張
5 多餘物件：通過（無壁爐、天窗、閣樓、室內樓梯）
```

## E2. 牆／門／窗一致率檢核方法

驗收 5 問是「有沒有錯」，一致率是「錯多少」，用於判斷這張圖是修得回來還是該換做法。

**算法**：
- 分母＝原平面圖上的「隔間牆段數 ＋ 門洞數 ＋ 窗洞數」總和。牆段以兩個轉角之間為一段計。
- 分子＝在成果圖上位置正確、數量正確的項數。多畫的項目要從分子扣（多一扇窗＝該窗不計入分子，且視為一個錯項）。
- 一致率＝分子 ÷ 分母 × 100%，逐個點名數，不得目測估計。

**判準**：
- 客戶提案版（P-2、P-3）：一致率 **≥ 90%** 且驗收 5 問全過才可交付。
- 工程溝通版（P-4）：一致率必須 **100%**，任何一項不對都要修到對。
- 一致率 < 90%：不要在同一張上修第三輪。回到第 3 步重新確認複述，或改用 P-2（若原本用 P-1）。
- 同一張圖指名修 **2 輪仍未通過**：停手，改走 G 段的白模路線，或縮小範圍（先出單一樓層區塊而非全戶）。

**點名記錄範例**：

```
分母 21（隔間牆 10 段 + 門洞 7 + 窗洞 4）
錯項 2（次臥 B 多一窗；主臥與次臥 A 之間隔間牆消失）
一致率 19/21 = 90.5% → 達標，但兩項均須指名修後再交付
```

## E3. 常見失敗與修法表

| 症狀 | 修法（指名修，其他不要動） |
|---|---|
| 格局整體跑掉、房間位置錯亂 | 不要在圖上修。回第 3 步重新複述格局，確認後改用 P-2 第二段重出 |
| 自行加窗 | 補一句 `Windows only where drawn in the plan; no additional openings.` 並指名：「南面陽台多了一扇窗，原圖沒有，請移除，其他不要動」 |
| 房間被合併 | 指名該處：「餐廚與客廳之間原圖有一道隔間牆，請補回，維持兩個獨立空間，其他不要動」 |
| 房間被多切 | 指名：「主臥被切成兩間，原圖是一間，請併回，其他不要動」 |
| 誤讀廚房線條（把櫥櫃當牆） | 回第 3 步就該攔下。已出圖則指名：「廚房北側那條線是櫥櫃立面不是牆，請改成櫥櫃，其他不要動」 |
| 比例失真（浴室過大、房間等寬） | 補實際尺寸再重出：「主臥約 4.2 × 3.3 公尺，衛浴約 1.6 × 2.0 公尺，請依此比例重出，格局不變」 |
| 文字標籤殘留（中文字被畫進圖） | 補 `Remove all text labels and dimension lines. Label nothing.`；若仍殘留，回第 1 步把圖面文字清乾淨再重來 |
| 天花板比例錯誤（牆看起來過高或過矮） | 補 `Wall height is exactly 2.8 meters; keep wall height consistent across all rooms.` |
| 窗戶方向錯置（窗開在錯的外牆） | 指名方位：「東向窗應在主臥，不是次臥 A；請對調，其他不要動」 |
| 多視角之間格局漂移 | 以已通過的那張為基準指名修不一致者；不要三張全部重生（見 D3） |
| 多了壁爐／天窗／閣樓／室內樓梯 | 指名移除，並確認 prompt 結尾帶了 C-6 的禁止清單 |
| 出成平視室內效果圖（不是等角） | prompt 的視角句被稀釋了。把 `slightly tilted top-down isometric camera, about 45 degrees, roof removed` 移到句子前段重出 |

---

# F. 與模式一銜接：等角圖定案後出單房效果圖

全戶等角圖通過驗收 5 問之後，同一戶要出單一空間的透視效果圖，走**模式一**，但**沿用模式二已定案的材質段**，這是同一戶多張圖看起來像同一戶的關鍵。

## F1. 銜接三步

1. **抄出材質段**：把等角圖 prompt 裡的材質描述（地坪／牆面／櫃體／織品）與光線描述整段抄下來，逐字不改，存成這一案的「案子固定描述」。
2. **換掉視角段**：刪除 `isometric / top-down / roof removed / 45 degrees` 整段，換成模式一的平視鏡頭段——眼高 120cm、24mm 等效（局部特寫可 35–50mm）、一點透視為主、垂直線保持垂直。
3. **換掉禁止清單**：模式一改用 05 檔的 **F-1 通用清單**（含俯視類禁令），不再用 C-6 的 F-2。

## F2. 單房透視的鏡頭措辭

```
Photorealistic interior photograph, 24 mm equivalent wide-angle lens, eye level at 120 cm, one-point
perspective, verticals kept straight, warm afternoon daylight from the window drawn in the plan.
```

35–50mm 僅限局部特寫與文字／招牌渲染（見 01 §4、03 檔第 91 行），整間空間的透視一律 24mm（20–28mm 內可調）。原出處使用的是 35mm 鏡頭措辭，如菓版已依正典改為 24mm；光線措辭取自 GPT-image 室內設計提示詞指南：https://boardspace.ai/gpt-image-prompt-guide/ ；細節查 03 檔與 05 檔。

## F3. 銜接時的三條紀律

- **格局仍以平面圖為準**：轉成模式一之後，牆位、窗位、門位仍不得更動。等角圖是格局的視覺確認，平面圖才是權威依據。
- **材質段一字不改**：要調材質就回頭改「案子固定描述」，然後全套圖一起換，不要單張偷改。
- **模式一的圖也要跑自檢**：跑 05 檔的模式一 6 問，不是模式二的 5 問。

---

# G. 另一條路線：白模先建、再上材質（簡述）

當同一張平面圖照上述流程**連續兩次不過驗收**（複雜大戶型最常見），還有一條備援：先用外部平面圖工具把格局建成無材質的 3D 白模，截一張 45 度等角圖，再把白模截圖丟進來，**只要求上材質與打光、不准動幾何**。

上材質時用 P-5 的骨幹句，並額外加一句：

```
Do not change any geometry. Only add materials, textures and lighting.
```

適用時機：格局複雜、客戶對格局精度要求高、且時間允許（工時明顯高於直接出圖，急件不適用）。

限制與注意：
- 這條串接目前**沒有實測紀錄**，屬合理推論，第一次用要當試辦。
- 平面圖送任何第三方平台前，一律先遮蔽地址、屋主姓名、建案名稱。
- 工具選擇、額度與比較，見如菓內部附錄《外部工具鏈與引擎比較》（該附錄不在本專案知識檔內，請向如菓內部索取）。

---

# H. 交付附註（每張模式二成果圖都要附）

逐字附在圖片下方，不得省略、不得改寫成更輕的說法：

> 本圖為依平面圖生成的立體示意圖，非 3D 模型，不含水電、結構、消防資訊；尺寸為視覺估計，不得作為施工、估價或請照依據，實際以現場丈量與圖說為準。

補充規則：
- 對外圖（客戶、社群、提案封面）一律帶此註記。
- 客戶追問「工班可以照這個施工嗎」「大概多少錢、做多久」：先重述本註記，價格與工期一律請客戶直接聯繫如菓，不給任何數字，也不下法規結論。
- 圖面本身不要壓字幕或浮水印式註記，註記寫在訊息文字裡即可（壓在圖上會與 C-6 的「不得出現文字」衝突）。

---

# I. 回寫紀律

每一張模式二成果圖，不論過關或失敗，都要記進 07 過關圖回寫紀錄表（模式欄填「二」），至少記：用了哪一條 prompt（P-1～P-5）、修了幾輪、一致率、驗收 5 問逐項結果、失敗原因。

累積滿 10 筆做一次小結：反覆過關的措辭補進本檔對應條目、反覆失敗的措辭從本檔移除；五條如菓版 prompt 實測通過後，把「自製草稿，未實測」改成「已實測（日期）」。沒有實測紀錄之前，這五條一律維持草稿標記，不得對外宣稱已驗證。
