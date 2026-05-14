# ComfyUI Tag 编写指南

## 核心原则

使用 **Danbooru 风格 tags** 和短英文视觉短语。只描述画面里能看见的内容。

- 所有特征优先写成英文 Danbooru tags：外貌、服装、动作、表情、场景、光影
- Tag 之间用英文逗号 `,` 分隔，tag 内部用空格（如 `long hair` 而非 `long_hair`）
- 每个字段内，按重要性降序排列 tag

---

## 权重语法

```text
(tag)        → 轻微强调 (~1.1x)
(tag:1.2)    → 明确强调
(tag:0.8)    → 降低权重
```

权重只用于核心主体、关键动作、关键表情或关键服装状态。

---

## scene 字段 Tag 参考

构图/相机/分级相关 tag：

```text
分级 → 人数计数 → 性关系 → 视角 → 区域 → 远近 → 透视 → 焦点
```

示例：
```text
nsfw, 1boy 1girl, hetero, pov, from above, upper body, close-up, face focus, blurry background
```

## background 字段 Tag 参考

环境/光影/氛围相关 tag：

```text
室内外 → 地点 → 具体物件 → 光源 → 光影效果 → 氛围
```

示例：
```text
indoors, living room, wooden floor, window, curtains, night, warm lighting, sidelighting, dramatic shadows
```

---

## 外貌特征 (静态 Tags)

**头发：**
- 长度: `short hair`, `medium hair`, `long hair`, `very long hair`
- 发型: `ponytail`, `twintails`, `braid`, `messy hair`, `ahoge`, `side ponytail`
- 颜色: `blonde hair`, `black hair`, `silver hair`, `gradient hair`, `multicolored hair`

**眼睛：**
- 颜色: `blue eyes`, `red eyes`, `heterochromia`, `purple eyes`
- 特征: `slit pupils`, `glowing eyes`, `closed eyes`, `half-closed eyes`, `crying`

**皮肤：**
- `pale skin`, `tan`, `dark skin`, `dark-skinned female`
- 细节: `freckles`, `mole`, `blush`, `sweat`

**身材：**
- `petite`, `slim`, `curvy`, `muscular`
- `large breasts`, `medium breasts`, `small breasts`, `flat chest`

---

## 角色字段规则

**已录入角色（已知角色）：**
- 不要输出 `type` 和 `appear`（系统自动注入）
- 必须输出: `costume`, `action`, `interact`, `uc`, `position`

**未知角色：**
- 必须输出所有字段: `type`, `appear`, `costume`, `action`, `interact`, `uc`, `position`

---

## 动作与表情

图片是静态瞬间，不要描述连续动作。

**姿态：**
- `standing`, `sitting`, `kneeling`, `lying`, `leaning`, `squatting`, `crouching`

**表情：**
- `smile`, `blush`, `crying`, `surprised`, `angry`, `embarrassed`, `shy`, `half-closed eyes`
- `open mouth`, `closed mouth`, `tongue out`, `drooling`

**视线：**
- `looking at viewer`, `looking away`, `looking down`, `looking up`, `looking at another`

**互动（多角色时）：**
- `holding hands`, `hug`, `kiss`, `face to face`, `hand on shoulder`
- interact 使用纯标签格式，不加方向前缀
- 正确: `fellatio`, `holding hands`
- 错误: `source#fellatio`, `target#fellatio`

---

## NSFW 精确术语

使用精确的解剖学术语，不要模糊描述。

**标签：** 必须添加 `nsfw` 标签

**身体部位：** `penis`, `vagina`, `anus`, `nipples`, `erection`, `clitoris`, `testicles`, `pussy`

**横截面/断面图：** `cross section`, `internal view`, `x-ray`

**性行为：** `sex`, `vaginal`, `anal`, `oral`, `fellatio`, `cunnilingus`, `paizuri`, `handjob`

**体位：** `missionary`, `doggystyle`, `mating press`, `cowgirl position`, `deepthroat`, `spooning`

**液体/细节：** `cum`, `cum in pussy`, `cum on face`, `cum on body`, `creampie`, `sweat`, `saliva`, `drooling`

---

## 角色 uc 字段

`uc` 是角色级排除项，只写当前角色专属排除：

**适合写入：**
- 当前角色摘掉了眼镜: `glasses`
- 当前视角看不到眼睛: `visible eyes`
- 当前角色应悲伤: `smile, happy`
- 衣服已脱下或破损: 排除仍完整穿着的互斥服饰

**不适合写入：**
- `bad anatomy`, `bad hands`, `worst quality`, `lowres`（通用负向由系统配置）

---

## 自然语言位置词 (position)

使用简短自然语言描述角色在画面中的位置：

- 中心（默认）: `in center`
- 偏左: `in left side`
- 偏右: `in right side`
- 上方: `in upper area`
- 下方: `in lower area`
- 组合: `in upper left`, `in lower right`

单人默认 `in center`，仅在偏离中心时填写。

---

## 物理与构图检查

- 一只手不要同时做多个动作
- 背面视角不要强调正面表情（除非回头）
- `upper body` 不要描述脚、膝盖等看不到的部位
- 每张图只选一个最强视觉瞬间
