# E1nstein 数字大脑 · 设计规范 (Design System)

> 版本: v1.0 · 最后更新: 2026-07-14

---

## 1. 品牌定位

| 维度 | 定义 |
|------|------|
| **品牌名** | E1nstein 的数字大脑 |
| **定位** | 展示思考、工具与创造力的极客知识花园 |
| **故事线** | 好奇心驱动的探索 (Curiosity-Driven Exploration) |
| **品牌调性** | 信任感 + 极客感 + 克制 |
| **目标受众** | 对 AI、前端、效率工具感兴趣的开发者 |
| **用户路径** | 搜索/社交 → 个人站 → 内容/工具体验 → 建立信任 → 关注/合作 |

人设关键词：`#好奇心` `#探索` `#极客` `#创造力` `#可靠`

---

## 2. 配色系统

### 主色 (Primary)

| 色值 | 用途 | 色块 |
|------|------|------|
| `#6366f1` (Indigo-500) | 品牌主色、链接、按钮、强调 | 🟣 |
| `#4f46e5` (Indigo-600) | Hover 状态 | 🟣⬇️ |
| `rgba(99, 102, 241, 0.15)` | 背景高亮、标签 | 🟣🔆 |

> 选择理由：Indigo 紫色呼应 E1nstein 中的 "stein"（德语"石头"），同时传达理性与创意。  
> 配色源自 Coolors 经典 Indigo 系。

### 中性色 (Neutral)

| 场景 | Light Mode | Dark Mode |
|------|-----------|-----------|
| 背景渐变 | `#f5f7fa` → `#c3cfe2` | `#0f172a` → `#1e1b4b` |
| 表面/卡片 | `rgba(255,255,255,0.65)` | `rgba(30,41,59,0.45)` |
| 表面 Hover | `rgba(255,255,255,0.80)` | `rgba(30,41,59,0.70)` |
| 主文字 | `#1e293b` (Slate-800) | `#f1f5f9` (Slate-100) |
| 次级文字 | `#475569` (Slate-600) | `#cbd5e1` (Slate-300) |
| 弱化文字 | `#64748b` (Slate-500) | `#94a3b8` (Slate-400) |

### 语义色

- 成功/在线：`#10b981` (Emerald-500)
- 错误/倒计时：`#ef4444` (Red-500)

---

## 3. 字体系统

| 层级 | 字重 | 字号 | 字族 |
|------|------|------|------|
| 品牌名 (Logo) | 700 | 1.25rem | `Inter, SF Pro, PingFang SC, sans-serif` |
| 标题 | 600-700 | 1.0-1.4rem | `Inter, SF Pro, PingFang SC, sans-serif` |
| 正文 | 400 | 0.85-0.95rem | `Inter, SF Pro, PingFang SC, sans-serif` |
| 小字/标签 | 400-500 | 0.7-0.82rem | `Inter, SF Pro, PingFang SC, sans-serif` |
| 等宽 (代码/数据) | 700 | 1.0-1.6rem | `JetBrains Mono, SF Mono, monospace` |

Font Stack：`'Inter','SF Pro','PingFang SC','-apple-system',BlinkMacSystemFont,sans-serif`

---

## 4. 间距系统

| Token | 值 | 使用场景 |
|-------|-----|---------|
| `--radius-sm` | 8px | 按钮、标签、小卡片 |
| `--radius` | 16px | 卡片、面板、模态框 |
| `--radius-lg` | 24px | 大卡片、特殊容器 |
| 网格间距 | 12px | 链接网格、工具网格 |
| 区块间距 | 36px | Section 之间的间距 |
| 内边距基础 | 24px | 玻璃面板内部 padding |

---

## 5. 玻璃拟态 (Glassmorphism) 规范

```css
/* 标准玻璃面板 */
.glass-panel {
  background: var(--surface);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  box-shadow: var(--shadow);
}

/* 悬停态 */
.glass-panel:hover {
  box-shadow: var(--shadow-hover);
  border-color: var(--border-active);
}
```

| 属性 | 值 |
|------|-----|
| 背景透明度 | 0.45-0.65 (依赖主题) |
| 模糊强度 | 20px |
| 边框颜色 | 白色 0.08-0.45 (依赖主题) |
| 阴影 | 8px 32px, 低透明度 |
| 悬停阴影 | 上调透明度 + accent 色调 |

---

## 6. 组件风格

### 卡片 (Card)
- 圆角: 16px
- 悬停: translateY(-3px) + 阴影增强
- 图标: 悬停时 scale(1.1) + rotate(5deg)，增加活力感
- 箭头: 悬停时 translateX(3px)，暗示可点击

### 按钮 (Button)
- 圆角: 8px
- 主按钮: 纯色填充 (accent) + 白色文字
- 次按钮: 描边 + 透明背景
- 悬停: 背景加深
- 点击: scale(0.98)

### 标签 (Tag/Badge)
- 圆角: 6-10px
- 尺寸: 0.7-0.8rem
- 背景: accent-light

### 筛选标签 (Category)
- 圆角: 20px (药丸形状)
- 激活态: accent 填充 + 阴影
- 悬停: 边框变 accent 色

---

## 7. 动效规范

| 场景 | 动画 | 时长 | 缓动 |
|------|------|------|------|
| 卡片出现 | fadeUp (opacity + translateY) | 0.4s | `cubic-bezier(0.25, 1, 0.5, 1)` |
| 卡片悬停 | translateY + shadow | 0.25s | `cubic-bezier(0.4, 0, 0.2, 1)` |
| 模态框打开 | scaleIn | 0.25s | `cubic-bezier(0.34, 1.56, 0.64, 1)` (弹性) |
| 状态指示灯 | pulse | 1.8s | 循环 |
| 主题切换 | 背景+颜色 transition | 0.3s | 默认 |
| 搜索框焦点 | border + shadow + translateY | 0.3s | 默认 |

> 动效原则：克制自然，不炫技。以内容本身说话，动效只是引导注意力的辅助手段。

---

## 8. 布局规范

### 两栏结构
```
┌─────────────────────────────────────┐
│              Header                  │
├──────────────┬──────────────────────┤
│  Sidebar     │   Main Content        │
│  320px       │   1fr                 │
│              │   ├── Stats Bar       │
│  Profile     │   ├── Tagline         │
│  Clock       │   ├── Search          │
│  Quotes      │   ├── Category Filter │
│  Weather     │   ├── Links Grid      │
│  Pomodoro    │   ├── Tools Grid      │
│  Status      │   ├── Projects Grid   │
│              │   ├── Skills Tags     │
│              │   ├── Reading List    │
│              │   └── Explore Grid    │
├──────────────┴──────────────────────┤
│              Footer                  │
└─────────────────────────────────────┘
```

### 响应式断点
| 断点 | 行为 |
|------|------|
| >960px | 两栏布局 |
| ≤960px | 单栏 (Sidebar 移动到上方) |
| ≤640px | 导航网格 1列、工具网格 2列、字号缩小 |

---

## 9. 设计对拍摄影 (Design References)

| 参考 | 原因 |
|------|------|
| [leerob.io](https://leerob.io) | 克制、信息密度高、技术信任感 |
| [brittanychiang.com](https://brittanychiang.com) | 极简暗色、侧栏社交导航 |
| [tw93 的博客](https://tw93.fun) | 不花哨但让人觉得靠谱 |

---

## 10. 品牌资产

| 资产 | 形式 | 位置 |
|------|------|------|
| Logo | `E` 渐变字母 + 阴影 | Header + Favicon |
| 故事线装饰 | `E=mc²` 极简公式 | 右下角背景 (opacity 0.04-0.06) |
| 背景光晕 | 3 个径向渐变光球 | 固定定位，z-index -1 |
| 品牌色 | Indigo #6366f1 | 全站 accent |

---

> **维护说明**: 此 design.md 与 index.html 同步维护。每次新增组件或修改样式前，先对照本规范确认一致性。  
> 参考来源: [styles.refero.design](https://styles.refero.design) · [Jacky 的文章方法论](https://x.com/Jackywxsz/status/2076891615013269842)
