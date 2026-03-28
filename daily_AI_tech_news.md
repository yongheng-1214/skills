# AI科技日报生成规范手册（完整版）

**版本**：v1.0  
**更新日期**：2026-03-28  
**适用范围**：微信公众号富文本HTML生成

---

## 一、任务参数

### 1.1 输入要求
- **目标日期**：YYYY-MM-DD（例：2026-03-28）
- **排除日期列表**：[2026-03-15, 2026-03-16, ..., 前一日期]
- **输出格式**：纯HTML代码（无Markdown包裹）

### 1.2 搜索策略
**关键词组合**：
- 中文：`YYYY年M月D日 AI新闻`、`人工智能 科技新闻 M月D日`
- 英文：`AI artificial intelligence news Month D, YYYY`、`OpenAI Google Meta NVIDIA news Month D, YYYY`
- 语法：`after:YYYY-MM-DD before:YYYY-MM-DD+1`

**去重检查**：与排除日期列表交叉验证标题、事件主体、核心数据、产品首发、言论时效、政策时间，确保零重复。

---

## 二、板块结构详解（板块2-10）

### 板块1：🔥 今日热点导览
**功能**：快速浏览当日8条最重要短讯  
**内容要求**：
- 8条新闻，每条一句话概括
- 必须包含超链接（蓝色下划线样式）
- 格式：图标 + 链接标题 + 逗号 + 关键信息

**HTML模板**：
```html
<!-- 板块标题 -->
<h2 style="color:#dc3545;font-size:18px;border-left:4px solid #dc3545;padding-left:10px;margin:25px 0 15px 0;">🔥 今日热点导览</h2>

<!-- 内容容器 -->
<div style="background:#fff5f5;padding:15px;border-radius:5px;margin-bottom:20px;">
  
  <!-- 单条新闻（重复8次） -->
  <p style="margin:8px 0;line-height:1.6;font-size:15px;">
    <span style="color:#dc3545;font-weight:bold;">•</span> 
    <a href="[URL]" style="color:#333;text-decoration:none;border-bottom:1px solid #667eea;">
      <strong>[新闻标题]</strong>
    </a>，[一句话关键信息，含数字/影响]
  </p>
  
</div>
```

### 板块2：🎯 今日焦点（2-3条深度报道）

**内容结构**：
- **标题**：18-20px，含链接，右上角标签badge
- **正文**：3-5句话，包含事件背景、关键数据/引用（含超链接）、行业影响分析
- 事件背景（Who/When/What）
- 关键数据/引用（含超链接）
- 行业影响分析
- **来源**：小字灰色，带链接
- **点评框**：底部高亮，1句话犀利点评

**标签颜色体系**：
- 战略合作：`background:#fff3cd;color:#856404;`
- 法律冲突/监管：`background:#f8d7da;color:#721c24;`
- 财报季/业绩：`background:#d4edda;color:#155724;`
- 新产品/技术突破：`background:#cce5ff;color:#004085;`
- 独家新闻/重大发布：`background:#e2e3e5;color:#383d41;`

**HTML模板**：
```html
<h2 style="color:#fd7e14;font-size:18px;border-left:4px solid #fd7e14;padding-left:10px;margin:25px 0 15px 0;">🎯 今日焦点</h2>

<!-- 焦点文章1（重复2-3次） -->
<div style="background:white;border:1px solid #dee2e6;border-radius:12px;padding:25px;margin-bottom:20px;box-shadow:0 2px 8px rgba(0,0,0,0.04);">
  
  <!-- 标题区 -->
  <h3 style="margin:0 0 15px 0;font-size:18px;color:#1a1a1a;">
    <a href="[URL]" style="color:#1a1a1a;text-decoration:none;">[文章标题]</a>
    <span style="display:inline-block;background:#fff3cd;color:#856404;padding:2px 10px;border-radius:12px;font-size:12px;margin-left:10px;font-weight:normal;">[标签名]</span>
  </h3>
  
  <!-- 正文（含内链） -->
  <p style="margin:0 0 15px 0;color:#495057;font-size:15px;line-height:1.7;">
    <a href="[URL]" style="color:#667eea;text-decoration:none;">[公司名]</a>[正文内容，含<strong>关键数字</strong>与引用]
  </p>
  
  <!-- 来源 -->
  <p style="font-size:12px;color:#999;margin-bottom:15px;">
    来源：<a href="[URL]" style="color:#667eea;">[媒体名]</a>、<a href="[URL]" style="color:#667eea;">[媒体名2]</a>
  </p>
  
  <!-- 点评框 -->
  <div style="background:#f8f9fa;padding:15px;border-radius:8px;border-left:3px solid #fd7e14;">
    <em style="color:#856404;font-style:italic;">💬 点评：[一句话犀利点评，指出本质或趋势]</em>
  </div>
</div>
```

### 板块3：🚀 新产品与发布（3条）

**内容要求**：
- **格式**：## [产品名]：[动作+结果]
- **技术亮点标签**：灰色小字，带emoji
- 来源链接

**HTML模板**：
```html
<h2 style="color:#28a745;font-size:18px;border-left:4px solid #28a745;padding-left:10px;margin:25px 0 15px 0;">🚀 新产品与发布</h2>

<div style="background:white;border:1px solid #dee2e6;border-radius:12px;padding:20px;margin-bottom:15px;">
  <h4 style="margin:0 0 12px 0;color:#1a1a1a;font-size:16px;">
    <a href="[URL]" style="color:#1a1a1a;text-decoration:none;">[产品名]：[动作+结果]</a>
    <span style="float:right;background:#cce5ff;padding:2px 8px;font-size:11px;color:#004085;border-radius:10px;">[公司]</span>
  </h4>
  
  <p style="margin:0 0 12px 0;color:#495057;font-size:14px;line-height:1.7;">
    [正文：技术原理简述+应用场景]
  </p>
  
  <p style="font-size:13px;color:#6c757d;">🎯 [技术亮点，如"核心指标：2.87倍算力提升"]</p>
  
  <p style="font-size:12px;color:#999;margin:0;">
    来源：<a href="[URL]" style="color:#667eea;">[来源]</a>
  </p>
</div>
```

### 板块4：⚡ AI实战派（2条）

**内容结构**：
- **第一条（重点）**：渐变背景（红/紫），适合警示/突发/重大突破
- **第二条（常规）**：浅灰背景，适合产业落地/应用案例
- **格式**：## [公司/工具]：[效果数据]
- 必须包含场景标签和关键takeaway

**HTML模板**：
```html
<h2 style="color:#6f42c1;font-size:18px;border-left:4px solid #6f42c1;padding-left:10px;margin:25px 0 15px 0;">⚡ AI实战派</h2>

<!-- 重点案例（渐变背景） -->
<div style="background:linear-gradient(135deg,#dc3545 0%,#721c24 100%);color:white;padding:20px;border-radius:10px;margin-bottom:15px;">
  <p style="font-size:13px;opacity:0.9;margin-bottom:8px;">[场景标签，如"华尔街实战 ⚠️ 危机响应"]</p>
  
  <h4 style="font-size:16px;margin-bottom:12px;">[公司/工具]：[效果数据，如"将研究耗时压缩80%"]</h4>
  
  <p style="font-size:14px;opacity:0.95;line-height:1.6;margin-bottom:12px;">
    [正文，可含<a href="[URL]" style="color:#ffd43b;text-decoration:none;">[内链]</a>]
  </p>
  
  <p style="font-size:12px;opacity:0.8;margin-top:10px;margin-bottom:0;">
    来源：<a href="[URL]" style="color:#ffd43b;">[来源]</a>
  </p>
</div>

<!-- 常规案例（浅灰背景） -->
<div style="background:#f8f9fa;border:1px solid #dee2e6;padding:20px;border-radius:10px;">
  <p style="font-size:13px;color:#6c757d;margin-bottom:8px;">[场景标签，如"制造业落地"]</p>
  
  <h4 style="font-size:16px;color:#1a1a1a;margin-bottom:12px;">[公司/工具]：[效果数据]</h4>
  
  <p style="color:#495057;font-size:14px;line-height:1.6;margin-bottom:12px;">
    [正文]
  </p>
  
  <p style="font-size:13px;color:#28a745;background:#d4edda;padding:8px 12px;border-radius:6px;display:inline-block;">
    ✓ [关键结论]
  </p>
</div>
```

### 板块5：💰 商业与资本（表格形式，4-5行）

**内容要求**：
- **列1**：公司/机构（含简介标签）
- **列2**：动作/金额（使用#20c997绿色突出）
- **列3**：关键数据（多维度指标）

**HTML模板**：
```html
<h2 style="color:#20c997;font-size:18px;border-left:4px solid #20c997;padding-left:10px;margin:25px 0 15px 0;">💰 商业与资本</h2>

<table style="width:100%;border-collapse:collapse;font-size:14px;background:white;border-radius:12px;overflow:hidden;box-shadow:0 2px 8px rgba(0,0,0,0.04);">
  <tr style="background:#f8f9fa;">
    <th style="padding:15px;text-align:left;font-weight:600;color:#495057;border-bottom:1px solid #dee2e6;">公司/机构</th>
    <th style="padding:15px;text-align:left;font-weight:600;color:#495057;border-bottom:1px solid #dee2e6;">动作/金额</th>
    <th style="padding:15px;text-align:left;font-weight:600;color:#495057;border-bottom:1px solid #dee2e6;">关键数据</th>
  </tr>
  
  <tr>
    <td style="padding:15px;border-bottom:1px solid #f1f3f5;">
      <strong><a href="[URL]" style="color:#333;text-decoration:none;">[公司名]</a></strong><br>
      <span style="font-size:12px;color:#6c757d;">[标签]</span>
    </td>
    <td style="padding:15px;border-bottom:1px solid #f1f3f5;">
      <strong style="color:#20c997;">[金额/动作]</strong><br>
      <span style="font-size:12px;color:#6c757d;">[备注]</span>
    </td>
    <td style="padding:15px;border-bottom:1px solid #f1f3f5;">
      [关键数据1]；[关键数据2]
    </td>
  </tr>
</table>
```

### 板块6：📊 业界动向（3条）

**内容结构**：
- **格式**：## [主体]：[事件]
- 左侧彩色边条标识类别（4px solid）
- 右上角标签说明子类别
- **边条颜色规范**：
  - 红色 #dc3545：警示/负面/裁员/股价暴跌
  - 蓝色 #0dcaf0：政策发布/合作/基础设施
  - 黄色 #ffc107：市场动态/消费趋势/就业
- **来源**：小字灰色，带链接

**HTML模板**：
```html
<h2 style="color:#e83e8c;font-size:18px;border-left:4px solid #e83e8c;padding-left:10px;margin:25px 0 15px 0;">📊 业界动向</h2>

<!-- 动向1（红色边条-警示） -->
<div style="background:white;border:1px solid #dee2e6;border-radius:12px;padding:20px;margin-bottom:15px;border-left:4px solid #dc3545;">
  <h4 style="margin:0 0 12px 0;color:#1a1a1a;font-size:16px;">
    <a href="[URL]" style="color:#1a1a1a;text-decoration:none;">[主体]：[事件]</a>
    <span style="float:right;background:#f8d7da;color:#721c24;padding:2px 10px;border-radius:12px;font-size:11px;">[标签]</span>
  </h4>
  <p style="margin:0 0 12px 0;color:#495057;font-size:14px;line-height:1.7;">[正文]</p>
  <p style="font-size:12px;color:#999;margin:0;">来源：<a href="[URL]" style="color:#667eea;">[来源]</a></p>
</div>

<!-- 动向2（蓝色边条-政策） -->
<div style="background:white;border:1px solid #dee2e6;border-radius:12px;padding:20px;margin-bottom:15px;border-left:4px solid #0dcaf0;">
  <h4 style="margin:0 0 12px 0;color:#1a1a1a;font-size:16px;">
    <a href="[URL]" style="color:#1a1a1a;text-decoration:none;">[主体]：[事件]</a>
    <span style="float:right;background:#d1ecf1;color:#0c5460;padding:2px 10px;border-radius:12px;font-size:11px;">[标签]</span>
  </h4>
  <p style="margin:0 0 12px 0;color:#495057;font-size:14px;line-height:1.7;">[正文]</p>
</div>

<!-- 动向3（黄色边条-市场） -->
<div style="background:white;border:1px solid #dee2e6;border-radius:12px;padding:20px;margin-bottom:15px;border-left:4px solid #ffc107;">
  <h4 style="margin:0 0 12px 0;color:#1a1a1a;font-size:16px;">
    <a href="[URL]" style="color:#1a1a1a;text-decoration:none;">[主体]：[事件]</a>
    <span style="float:right;background:#fff3cd;color:#856404;padding:2px 10px;border-radius:12px;font-size:11px;">[标签]</span>
  </h4>
  <p style="margin:0 0 12px 0;color:#495057;font-size:14px;line-height:1.7;">[正文]</p>
</div>
```

### 板块7：💡 深度观点（2条）

**内容结构**：
- **第一条（学术/战略）**：浅紫背景 #f3f0ff，适合技术趋势、战略研判
- **第二条（投资/产业）**：浅橙背景 #fff2e8，适合投资洞察、商业模式
- **格式**：## [人物]：[核心观点]
- 必须包含人物身份标签（小字大写）

**HTML模板**：
```html
<h2 style="color:#6610f2;font-size:18px;border-left:4px solid #6610f2;padding-left:10px;margin:25px 0 15px 0;">💡 深度观点</h2>

<!-- 观点1（紫色-学术/战略） -->
<div style="background:#f3f0ff;border:1px solid #d0bfff;padding:20px;border-radius:10px;margin-bottom:15px;">
  <p style="font-size:12px;color:#722ed1;margin-bottom:8px;text-transform:uppercase;letter-spacing:1px;">[标签，如"德勤报告"]</p>
  
  <h4 style="font-size:16px;color:#391085;margin-bottom:12px;">
    <a href="[URL]" style="color:#391085;text-decoration:none;">[人物]：[核心观点]</a>
  </h4>
  
  <p style="color:#531dab;font-size:14px;line-height:1.7;margin:0;">
    [正文分析，可含<a href="[URL]" style="color:#667eea;text-decoration:none;">[内链]</a>]
  </p>
</div>

<!-- 观点2（橙色-投资/产业） -->
<div style="background:#fff2e8;border:1px solid #ffbb96;padding:20px;border-radius:10px;">
  <p style="font-size:12px;color:#d46b08;margin-bottom:8px;text-transform:uppercase;letter-spacing:1px;">[标签，如"投资洞察"]</p>
  
  <h4 style="font-size:16px;color:#873800;margin-bottom:12px;">
    <a href="[URL]" style="color:#873800;text-decoration:none;">[人物]：[核心观点]</a>
  </h4>
  
  <p style="color:#ad4e00;font-size:14px;line-height:1.7;margin:0;">
    [正文分析]
  </p>
</div>
```

### 板块8：🔬 技术前沿（1 Featured + 3 Grid）

**内容结构**：
- **Featured**：详细技术解读 + 三栏关键数据展示（居中数字）
- Grid：3个250px宽卡片，简短技术动态/论文/工具

**HTML模板**：
```html
<h2 style="color:#0dcaf0;font-size:18px;border-left:4px solid #0dcaf0;padding-left:10px;margin:25px 0 15px 0;">🔬 技术前沿</h2>

<!-- Featured 深度技术 -->
<div style="background:white;border:1px solid #dee2e6;border-radius:12px;padding:20px;position:relative;margin-bottom:15px;">
  <p style="position:absolute;top:0;right:0;background:#0dcaf0;color:white;padding:4px 12px;font-size:11px;border-radius:0 0 0 10px;margin:0;">Featured</p>
  
  <h4 style="font-size:16px;color:#1a1a1a;margin-bottom:12px;margin-top:5px;">
    <a href="[URL]" style="color:#1a1a1a;text-decoration:none;">[项目/论文]：[突破点]</a>
  </h4>
  
  <p style="color:#495057;font-size:14px;line-height:1.7;margin-bottom:15px;">
    [正文]
  </p>
  
  <!-- 三栏数据展示 -->
  <table style="width:100%;border-collapse:separate;border-spacing:10px;">
    <tr>
      <td style="text-align:center;padding:15px;background:#f8f9fa;border-radius:8px;width:33%;">
        <p style="font-size:20px;font-weight:bold;color:#0dcaf0;margin:0;">[数字1]</p>
        <p style="font-size:12px;color:#6c757d;margin:5px 0 0 0;">[标签1]</p>
      </td>
      <td style="text-align:center;padding:15px;background:#f8f9fa;border-radius:8px;width:33%;">
        <p style="font-size:20px;font-weight:bold;color:#0dcaf0;margin:0;">[数字2]</p>
        <p style="font-size:12px;color:#6c757d;margin:5px 0 0 0;">[标签2]</p>
      </td>
      <td style="text-align:center;padding:15px;background:#f8f9fa;border-radius:8px;width:33%;">
        <p style="font-size:20px;font-weight:bold;color:#0dcaf0;margin:0;">[数字3]</p>
        <p style="font-size:12px;color:#6c757d;margin:5px 0 0 0;">[标签3]</p>
      </td>
    </tr>
  </table>
</div>

<!-- Grid 三栏动态 -->
<div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:15px;">
  
  <div style="background:white;border:1px solid #dee2e6;padding:15px;border-radius:10px;">
    <h4 style="font-size:15px;color:#1a1a1a;margin:0 0 10px 0;">
      <a href="[URL]" style="color:#1a1a1a;text-decoration:none;">[标题]</a>
    </h4>
    <p style="color:#495057;font-size:13px;line-height:1.6;margin:0;">[一句话描述]</p>
  </div>
  
  <div style="background:white;border:1px solid #dee2e6;padding:15px;border-radius:10px;">
    <h4 style="font-size:15px;color:#1a1a1a;margin:0 0 10px 0;">
      <a href="[URL]" style="color:#1a1a1a;text-decoration:none;">[标题]</a>
    </h4>
    <p style="color:#495057;font-size:13px;line-height:1.6;margin:0;">[一句话描述]</p>
  </div>
  
  <div style="background:white;border:1px solid #dee2e6;padding:15px;border-radius:10px;">
    <h4 style="font-size:15px;color:#1a1a1a;margin:0 0 10px 0;">
      <a href="[URL]" style="color:#1a1a1a;text-decoration:none;">[标题]</a>
    </h4>
    <p style="color:#495057;font-size:13px;line-height:1.6;margin:0;">[一句话描述]</p>
  </div>
  
</div>
```

### 板块9：💡 今日总结

**内容要求**：
- 150字左右的行业洞察
- 回答："今天最值得关注的信号是什么？"
- 高亮关键公司/数据（黄色 #ffd43b）
- 给出从业者actionable建议

**HTML模板**：
```html
<div style="background:#212529;color:white;padding:25px;border-radius:12px;margin:25px 0;">
  <h3 style="font-size:20px;margin:0 0 15px 0;">💡 今日总结</h3>
  
  <p style="font-size:15px;line-height:1.8;opacity:0.95;margin:0;">
    [正文：今日核心趋势洞察，含<strong style="color:#ffd43b;">[高亮关键信息]</strong>高亮]
    <br><br>
    <strong style="color:#ffd43b;">对于从业者：</strong>[行动建议]
  </p>
</div>
```

### 板块10：页脚

**HTML模板**：
```html
<p style="text-align:center;font-size:13px;color:#6c757d;margin:20px 0;">
  以上内容基于公开信息整理分析，仅供参考交流。观点不构成任何投资建议。
</p>

<div style="text-align:center;">
  <div style="background:linear-gradient(135deg,#667eea 0%,#764ba2 100%);color:white;padding:20px;border-radius:12px;display:inline-block;min-width:280px;">
    <p style="font-size:18px;font-weight:bold;margin:0 0 5px 0;">永恒的技术趋势（未来同行）</p>
    <p style="font-size:14px;opacity:0.9;margin:0 0 8px 0;">AI · Data · Intelligence</p>
    <p style="font-size:12px;opacity:0.8;margin:0;">每日精选AI资讯 · 实战工具分享</p>
  </div>
</div>
```


## 三、视觉规范手册（Visual Style Guide）

### 3.1 颜色代码体系（严格使用）

| 用途       | 色值        | 使用场景                     |
| -------- | --------- | ------------------------ |
| **主链接色** | `#667eea` | 所有超链接文字、引用来源             |
| **警示红**  | `#dc3545` | 热点导览标题、负面新闻、重点警示、红色边条    |
| **浅红背景** | `#fff5f5` | 热点导览内容区                  |
| **强调橙**  | `#fd7e14` | 今日焦点标题边条、点评框边条           |
| **成功绿**  | `#28a745` | 新产品板块标题边条                |
| **商业绿**  | `#20c997` | 商业与资本金额高亮                |
| **科技蓝**  | `#0dcaf0` | 技术前沿标题边条、Featured标签、蓝色边条 |
| **浅蓝背景** | `#cce5ff` | 公司标签背景、技术产品标签            |
| **深紫**   | `#6f42c1` | AI实战派标题边条、深度观点标题边条       |
| **浅紫背景** | `#f3f0ff` | 深度观点（学术/战略）背景            |
| **浅橙背景** | `#fff2e8` | 深度观点（投资/产业）背景            |
| **高亮黄**  | `#ffd43b` | 今日总结关键信息高亮、渐变卡片内链        |
| **深灰背景** | `#212529` | 今日总结背景                   |
| **正文灰**  | `#495057` | 正文文字颜色                   |
| **辅助灰**  | `#6c757d` | 辅助信息、小标签文字               |
| **浅色灰**  | `#999`    | 来源链接颜色                   |
| **边框灰**  | `#dee2e6` | 卡片边框颜色                   |
| **背景灰**  | `#f8f9fa` | 表格表头、点评框背景               |

### 3.2 字体与间距规范
| 元素        | 字体大小    | 颜色               | 行高  | 边距                     |
| --------- | ------- | ---------------- | --- | ---------------------- |
| **板块标题**  | 18px    | 对应板块色            | 1.2 | `margin:25px 0 15px 0` |
| **文章主标题** | 18-20px | `#1a1a1a`        | 1.7 | `margin:0 0 15px 0`    |
| **文章副标题** | 16px    | `#1a1a1a`        | 1.6 | `margin:0 0 12px 0`    |
| **正文**    | 14-15px | `#495057`        | 1.7 | `margin:0 0 12-15px 0` |
| **辅助信息**  | 12-13px | `#6c757d`或`#999` | 1.5 | 视场景                    |
| **数据大字**  | 20px    | `#0dcaf0`        | 1   | 居中                     |
| **标签文字**  | 11-12px | 对应深色             | 1   | `padding:2px 8-10px`   |

**间距规范**：
- **板块间**：margin:25px 0（上下）
- **卡片内边距**：padding:20-25px
- **卡片外边距（底部）**：margin-bottom:15-20px
- **元素间（段间距）**：margin-bottom:12-15px
- **圆角统一**：border-radius:10px或12px（卡片），border-radius:6-8px（小标签）
- **左边框**：border-left:4px solid（板块标题）

### 3.3 引用与来源规范

- 所有外部信息使用[^N^]格式标注（如需脚注）
- 来源链接统一使用style="color:#667eea;"
- 多来源用顿号、分隔
- 来源标注位置：正文结束后，点评框之前

## 四、输出要求与检查清单

### 4.1 输出格式要求

- 纯HTML输出：直接输出HTML代码，无需Markdown代码块包裹（即不要```html）
- 可直接使用：代码可直接复制粘贴到微信公众号编辑器，无需二次调整
- 完整性：必须包含全部10个板块，缺一不可
- 时效性：所有新闻必须为指定日期当日

### 4.2 质量检查清单（Checklist）

**内容完整性检查**： 
- [ ] 板块1：8个热点导览，均为一句话，含链接和关键信息
- [ ] 板块2：2-3个焦点文章，均有3-5句话正文+1句话点评+标签
- [ ] 板块3：3个新产品，均有技术亮点标签（🎯开头）和来源
- [ ] 板块4：2个实战派案例（渐变+浅灰），均有效果数据和场景标签
- [ ] 板块5：4-5行商业资本表格，金额已用#20c997高亮
- [ ] 板块6：3个业界动向，均有彩色边条（红/蓝/黄）和右上角标签
- [ ] 板块7：2个深度观点（紫+橙背景），均有身份标签（大写）
- [ ] 板块8：1个Featured（含三栏数据表）+ 3个Grid卡片
- [ ] 板块9：今日总结150字左右，含黄色高亮和行动建议
- [ ] 板块10：页脚免责声明+品牌卡片（渐变背景） 

**格式规范检查**：
- [ ] 所有超链接均为#667eea颜色，无下划线（text-decoration:none）
- [ ] 所有板块标题左边框4px solid，颜色正确
- [ ] 所有卡片圆角统一（10px或12px）
- [ ] 页脚渐变背景正确（#667eea到#764ba2）
- [ ] 无Markdown语法残留（如**或##暴露在HTML外）
- [ ] 所有图片URL（如有）为HTTPS，且未修改原始链接

**唯一性检查（与排除日期列表比对）**：
- [ ] 标题无重复（去除日期后）
- [ ] 事件主体无重复动作（如公司A在排除日期已发布产品，今日不再报道其产品发布）
- [ ] 数据无重复发布（如"营收XX亿"为当日新数据）
- [ ] 产品无重复首发（确认为当日首次发布，非预告或后续报道）
- [ ] 人物言论无重复（确认为当日新发表观点）

### 4.3 常见错误避免
- ❌ 错误：使用<div>包裹整个HTML，导致微信编辑器格式错乱
- ✅ 正确：直接使用各板块HTML拼接，无外层包裹
- ❌ 错误：颜色使用red、blue等关键字
- ✅ 正确：必须使用十六进制色值，如#dc3545
- ❌ 错误：链接使用target="_blank"（微信不支持）
- ✅ 正确：仅使用href属性，不加额外属性
- ❌ 错误：图片使用HTTP链接
- ✅ 正确：必须使用HTTPS，且保持原始URL完整
