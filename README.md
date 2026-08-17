# 诺兰-movie-skill

融合**诺兰式时间操控**与**盖里奇式多线巧合**的电影语言生成技能包。  
面向 AI Agent 设计，输入场景描述与风格参数，输出可直接用于拍摄的分镜脚本、剪辑方案、声音设计及格式化拍摄手法提示词。

---

## 特性

- **Agent 视角**：定义标准输入/输出 Schema，支持枚举参数，可直接被 Agent 调用。
- **脚本优先**：以分镜、剪辑、声音三类脚本为核心输出，所有生成围绕可执行的拍摄脚本展开。
- **原子化**：叙事、剪辑、镜头、声音、色彩五类电影语言被拆分为最小可复用单元，可自由组合。
- **自我迭代**：记录用户反馈、偏好与版本历史，动态调整原子模块调用优先级。

---

## 快速开始

### 1. 安装与加载

将技能包放入 Agent 的技能目录，并在 Agent 配置中引入 `skill.yaml`：

```yaml
skills:
  - name: nolan-movie-skill
    path: ./nolan-movie-skill/skill.yaml
```

### 2. 调用示例

**输入：**

```json
{
  "scene_description": "主角在旋转走廊中追逐，时间开始逆转",
  "style_reference": "tenet",
  "time_structure": "palindrome",
  "emotion_tone": "紧张、宿命感",
  "output_format": "all"
}
```

**输出：**

```text
【格式化拍摄手法提示词】
叙事结构：回环结构 / 时间逆转 / 正逆同框
时间处理：时间膨胀 / 时间逆转 / 时间闭环
剪辑：倒放 / 交叉剪辑 / 匹配剪辑 / 快速切换
镜头语言：IMAX / 65mm实拍 / 旋转镜头 / 长镜头 / 主观视角限制
声音设计：脉冲低音 / 谢泼德音调 / 声音倒放 / 环境声渐强
色彩质感：冷色调 / 低饱和 / 高对比 / 自然光 / 胶片颗粒
转场方式：声音先行 / 动作匹配 / 重复场景
信息控制：限制视角 / 因果倒置 / 延迟揭示
节奏：信息密集 / 前段铺陈 / 中段交叉 / 结尾汇聚加速
母题：时间 / 身份 / 因果 / 循环 / 宿命

【分镜脚本】
...

【剪辑方案】
...

【声音设计】
...
```

---

## 输入输出 Schema

### 输入

| 字段 | 类型 | 说明 |
|------|------|------|
| `scene_description` | string | 场景描述，如“主角在旋转走廊中追逐” |
| `style_reference` | enum | `memento` / `inception` / `tenet` / `odyssey` / `lock_stock` / `auto` |
| `time_structure` | enum | `linear` / `reverse` / `nested` / `palindrome` / `multi_thread` / `loop` |
| `emotion_tone` | string | 情绪关键词，如“紧张”“悬疑”“宿命感” |
| `output_format` | enum | `prompt` / `shot_script` / `edit_plan` / `sound_design` / `all` |

### 输出

| 字段 | 类型 | 说明 |
|------|------|------|
| `prompt_text` | string | 格式化拍摄手法提示词 |
| `shot_script` | string | 分镜脚本 |
| `editing_plan` | string | 剪辑方案 |
| `sound_design` | string | 声音设计 |
| `atom_used` | list | 本次调用的原子模块列表 |

---

## 目录结构

```
nolan-movie-skill/
├── skill.yaml                     # 主 skill 定义（入口）
├── README.md                      # 本文件
├── core/
│   ├── master_prompt.md           # 主提示词/拍摄手法总纲
│   └── templates/
│       ├── shot_script.md         # 分镜脚本模板
│       ├── edit_script.md         # 剪辑脚本模板
│       └── sound_script.md        # 声音脚本模板
├── atoms/
│   ├── narrative/                 # 叙事原子模块
│   │   ├── time_linear.md
│   │   ├── time_reverse.md
│   │   ├── nested_dream.md
│   │   ├── palindrome.md
│   │   ├── multi_thread_coincidence.md
│   │   └── loop.md
│   ├── editing/                   # 剪辑原子模块
│   │   ├── cross_cutting.md
│   │   ├── parallel_montage.md
│   │   ├── reverse_playback.md
│   │   ├── match_cut.md
│   │   ├── freeze_frame.md
│   │   └── title_card.md
│   ├── camera/                    # 镜头原子模块
│   │   ├── imax_real.md
│   │   ├── subjective_pov.md
│   │   ├── symmetry.md
│   │   ├── low_angle.md
│   │   ├── rotate_shot.md
│   │   └── long_take.md
│   ├── sound/                     # 声音原子模块
│   │   ├── pulse_bass.md
│   │   ├── shepard_tone.md
│   │   ├── reverse_audio.md
│   │   └── dialogue_rapid.md
│   └── color/                     # 色彩原子模块
│       ├── cold_tone.md
│       ├── low_saturation.md
│       ├── high_contrast.md
│       ├── natural_light.md
│       └── film_grain.md
├── memory/
│   ├── feedback_log.md            # 用户反馈日志
│   ├── version_history.md         # 版本历史
│   └── user_preferences.json      # 用户偏好
└── examples/
    ├── memento_style.md           # 记忆碎片风格示例
    ├── inception_style.md         # 盗梦空间风格示例
    ├── tenet_style.md             # 信条风格示例
    ├── odyssey_style.md           # 奥德赛风格示例
    └── lock_stock_style.md        # 两杆大烟枪风格示例
```

---

## 原子模块说明

### 叙事 atoms/narrative

| 模块 | 说明 | 代表作品 |
|------|------|----------|
| `time_linear` | 线性时间 | 常规叙事 |
| `time_reverse` | 倒叙/逆向时间 | 《记忆碎片》 |
| `nested_dream` | 嵌套层级/梦境时间差 | 《盗梦空间》 |
| `palindrome` | 回文结构/正逆同框 | 《信条》 |
| `multi_thread_coincidence` | 多线巧合汇聚 | 《两杆大烟枪》 |
| `loop` | 循环/时间闭环 | 《信条》《奥德赛》 |

### 剪辑 atoms/editing

| 模块 | 说明 |
|------|------|
| `cross_cutting` | 交叉剪辑 |
| `parallel_montage` | 平行蒙太奇 |
| `reverse_playback` | 倒放 |
| `match_cut` | 匹配剪辑 |
| `freeze_frame` | 定格 |
| `title_card` | 字幕卡 |

### 镜头 atoms/camera

| 模块 | 说明 |
|------|------|
| `imax_real` | IMAX/65mm 实拍 |
| `subjective_pov` | 主观视角限制 |
| `symmetry` | 对称构图 |
| `low_angle` | 低角度 |
| `rotate_shot` | 旋转镜头/旋转走廊 |
| `long_take` | 长镜头 |

### 声音 atoms/sound

| 模块 | 说明 |
|------|------|
| `pulse_bass` | 脉冲低音 |
| `shepard_tone` | 谢泼德音调 |
| `reverse_audio` | 逆向音效/声音倒放 |
| `dialogue_rapid` | 快节奏对白 |

### 色彩 atoms/color

| 模块 | 说明 |
|------|------|
| `cold_tone` | 冷色调 |
| `low_saturation` | 低饱和 |
| `high_contrast` | 高对比 |
| `natural_light` | 自然光 |
| `film_grain` | 胶片颗粒 |

---

## 自我迭代机制

- **反馈记录**：每次生成后，Agent 将用户反馈追加至 `memory/feedback_log.md`。
- **偏好更新**：用户对风格的偏好存入 `memory/user_preferences.json`，影响后续 `style_reference` 的默认选择。
- **权重调整**：根据反馈，动态调整原子模块的调用优先级（如用户偏好《信条》风格，则 `palindrome`、`reverse_playback` 权重提高）。
- **版本管理**：主提示词或核心模板更新时，版本号递增，变更记录写入 `memory/version_history.md`。
- **增量扩展**：新增原子模块只需在对应 `atoms/` 子目录添加文件，并在 `skill.yaml` 的 `atoms` 列表注册，不影响已有结构。

---

## 风格示例映射

| style_reference | 示例文件 | 核心特征 |
|----------------|----------|----------|
| `memento` | `examples/memento_style.md` | 倒叙双线、记忆断裂、延迟揭示 |
| `inception` | `examples/inception_style.md` | 嵌套层级、时间膨胀、平行剪辑 |
| `tenet` | `examples/tenet_style.md` | 回文结构、时间逆转、正逆同框 |
| `odyssey` | `examples/odyssey_style.md` | 史诗归途、时间母题、IMAX 实拍 |
| `lock_stock` | `examples/lock_stock_style.md` | 多线巧合、快速剪辑、黑色幽默 |

当 `style_reference` 设为 `auto` 时，Agent 会根据 `scene_description` 与 `emotion_tone` 自动匹配最合适的风格示例。

---

## 常见问题

**Q：如何新增一种电影风格？**  
A：在 `examples/` 下新建风格示例文件，并在 `skill.yaml` 的 `style_examples` 中注册；若需新原子模块，在对应 `atoms/` 目录添加文件并注册。

**Q：输出格式可以只生成提示词吗？**  
A：可以，将 `output_format` 设为 `prompt`，将只返回 `prompt_text`。

**Q：如何调整诺兰与盖里奇的风格比重？**  
A：通过 `emotion_tone` 和 `style_reference` 控制；也可在 `memory/user_preferences.json` 中设置偏好权重。

---

## 版本

- **v1.0.0**：初始版本，包含五类原子模块、五种风格示例、自我迭代机制。

- license MIT
