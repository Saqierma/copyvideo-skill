# 输出契约

首次完整交付必须按以下顺序输出。不得改名、合并或省略字段；无数据时填 `未提供`、`未识别` 或 `待确认`。

## Markdown 输出

### 一、原视频基础分析表

| 项目 | 分析结果 |
| --- | --- |
| 视频总时长 |  |
| 画幅比例 |  |
| 语言 |  |
| 视频类型 |  |
| 带货品类 |  |
| 目标人群 |  |
| 核心卖点 |  |
| 情绪基调 |  |
| 节奏速度 |  |
| 镜头数量 | 填写镜头总数，并在同一单元格注明平均镜头时长 |
| 开头钩子 |  |
| 中段结构 |  |
| 结尾转化 |  |

### 二、原视频分镜拆解表

| 镜头 | 时间段 | 画面内容 | 口播/字幕 | 情绪 | 卖点 | 镜头作用 |
| --- | --- | --- | --- | --- | --- | --- |

`画面内容` 单元格按 `场景与构图；人物动作；产品展示方式；镜头运动` 填写。`口播/字幕` 单元格按 `口播：...；字幕：...` 填写。

### 三、底层结构总结

* 脚本结构：
* 情绪曲线：
* 镜头节奏：
* 卖点表达顺序：
* 转化逻辑：
* 可复用元素：
* 不可照搬元素：

### 四、变量替换表

| 原视频元素 | 替换变量 | 用户输入 | 替换规则 |
| --- | --- | --- | --- |

至少覆盖：人物、产品、场景、卖点、对白、字幕、背景、结尾行动引导。

### 五、严格对齐原视频框架版

| 镜头 | 时间段 | 新画面内容 | 新口播 | 新字幕 | 产品展示 | 情绪 | 镜头提示词 |
| --- | --- | --- | --- | --- | --- | --- | --- |

`新画面内容` 必须包含人物动作、场景和镜头运动；`镜头提示词` 必须包含光线、背景和负面要求。

### 六、延展创新故事版

| 镜头 | 时间段 | 新画面内容 | 新口播 | 新字幕 | 产品展示 | 情绪 | 镜头提示词 |
| --- | --- | --- | --- | --- | --- | --- | --- |

`新画面内容` 必须包含人物动作、场景和镜头运动；`镜头提示词` 必须包含光线、背景和负面要求。

### 七、最终视频模型提示词

按 A 版、B 版分别设小标题并逐镜头输出：

```text
镜头编号：
时长：
画幅：
画面描述：
人物动作：
产品展示：
镜头运动：
光线风格：
背景环境：
字幕文案：
口播内容：
情绪要求：
负面要求：
```

## JSON 输出

仅在用户明确要求 JSON、API 接入或自动化工作流时使用。保持数组顺序与视频时间顺序一致。

```json
{
  "source_analysis": {
    "duration_seconds": null,
    "aspect_ratio": "",
    "language": "",
    "video_type": "",
    "commerce_category": "",
    "target_audience": "",
    "core_selling_points": [],
    "emotional_tone": "",
    "pace": "",
    "shot_count": null,
    "average_shot_duration_seconds": null,
    "opening_hook": "",
    "middle_structure": "",
    "closing_conversion": ""
  },
  "source_shots": [
    {
      "shot_id": "01",
      "start_seconds": null,
      "end_seconds": null,
      "visual": "",
      "voiceover": "",
      "onscreen_text": "",
      "character_action": "",
      "product_display": "",
      "camera_movement": "",
      "emotion": "",
      "selling_point": "",
      "shot_function": "",
      "evidence_level": "direct_observation"
    }
  ],
  "underlying_structure": {
    "script_structure": [],
    "emotional_curve": [],
    "shot_rhythm": "",
    "selling_point_order": [],
    "conversion_logic": [],
    "reusable_elements": [],
    "prohibited_copy_elements": []
  },
  "replacement_variables": [
    {
      "source_element": "",
      "variable": "",
      "user_input": "",
      "replacement_rule": ""
    }
  ],
  "versions": {
    "aligned": [],
    "innovative": []
  },
  "video_prompts": [
    {
      "version": "aligned",
      "shot_id": "01",
      "duration_seconds": null,
      "aspect_ratio": "",
      "visual_description": "",
      "character_action": "",
      "product_display": "",
      "camera_movement": "",
      "lighting_style": "",
      "background_environment": "",
      "subtitle": "",
      "voiceover": "",
      "emotion": "",
      "negative_prompt": ""
    }
  ],
  "assumptions": [],
  "unresolved_inputs": []
}
```

`versions.aligned` 与 `versions.innovative` 中的每个镜头对象使用与 `video_prompts` 相同的镜头编号，并至少包含：

```json
{
  "shot_id": "",
  "start_seconds": null,
  "end_seconds": null,
  "visual": "",
  "voiceover": "",
  "subtitle": "",
  "character_action": "",
  "product_display": "",
  "camera_movement": "",
  "emotion": "",
  "shot_function": "",
  "prompt": ""
}
```

## 修改输出

用户后续只修改某一版本时，先输出：

| 修改项 | 修改前 | 修改后 | 联动范围 |
| --- | --- | --- | --- |

随后完整重发受影响版本的分镜表，以及该版本全部更新后的逐镜头视频模型提示词。不要只给零散差异，除非用户明确要求 diff。
