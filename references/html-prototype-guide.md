# HTML 原型生成指南

本文档定义了 HTML 原型的生成规范、样式模板和组件库。

---

## 1. 设计理念

| 理念 | 说明 |
|------|------|
| 现代化 UI 元素 | 使用卡片、阴影、圆角、过渡动画等现代设计元素 |
| 开源图标库 | 使用 Lucide Icons 丰富视觉元素 |
| 工作空间理念 | 整体布局体现"我的工作空间"概念 |
| 浅色调为主 | 白色、浅灰为主基调，清爽专业 |

---

## 2. 视觉规范

### 2.1 颜色系统

```css
:root {
  /* 主色调 */
  --primary-color: #409EFF;
  --primary-light: #66b1ff;
  --primary-dark: #337ecc;

  /* 功能色 */
  --success-color: #67C23A;
  --warning-color: #E6A23C;
  --danger-color: #F56C6C;
  --info-color: #909399;

  /* 文字色 */
  --text-primary: #303133;
  --text-regular: #606266;
  --text-secondary: #909399;
  --text-placeholder: #C0C4CC;

  /* 边框色 */
  --border-color: #DCDFE6;
  --border-light: #E4E7ED;
  --border-lighter: #EBEEF5;

  /* 背景色 */
  --bg-color: #F2F6FC;
  --bg-white: #FFFFFF;
  --bg-page: #F5F7FA;

  /* 阴影 */
  --shadow-sm: 0 2px 4px rgba(0, 0, 0, 0.06);
  --shadow-base: 0 2px 12px rgba(0, 0, 0, 0.1);
  --shadow-lg: 0 4px 16px rgba(0, 0, 0, 0.12);

  /* 圆角 */
  --radius-sm: 4px;
  --radius-base: 8px;
  --radius-lg: 12px;

  /* 间距 */
  --spacing-xs: 4px;
  --spacing-sm: 8px;
  --spacing-md: 16px;
  --spacing-lg: 24px;
  --spacing-xl: 32px;
}
```

### 2.2 字体规范

```css
:root {
  --font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;

  --font-size-xs: 12px;
  --font-size-sm: 13px;
  --font-size-base: 14px;
  --font-size-md: 16px;
  --font-size-lg: 18px;
  --font-size-xl: 20px;
  --font-size-2xl: 24px;

  --line-height: 1.5;
}
```

---

## 3. 页面布局模板

### 3.1 基础布局结构

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>[页面标题] - 我的工作空间</title>
  <link rel="stylesheet" href="../css/style.css">
  <script src="https://unpkg.com/lucide@latest"></script>
</head>
<body>
  <div class="app-container">
    <!-- Header -->
    <header class="app-header">
      <div class="header-left">
        <div class="logo">
          <i data-lucide="layout-grid"></i>
          <span>我的工作空间</span>
        </div>
      </div>
      <div class="header-right">
        <div class="header-actions">
          <button class="icon-btn"><i data-lucide="bell"></i></button>
          <button class="icon-btn"><i data-lucide="settings"></i></button>
        </div>
        <div class="user-info">
          <img src="../assets/avatar.png" alt="用户头像" class="avatar">
          <span>管理员</span>
        </div>
      </div>
    </header>

    <div class="app-body">
      <!-- Sidebar -->
      <aside class="app-sidebar">
        <nav class="sidebar-nav">
          <a href="#" class="nav-item active">
            <i data-lucide="home"></i>
            <span>首页</span>
          </a>
          <a href="#" class="nav-item">
            <i data-lucide="users"></i>
            <span>用户管理</span>
          </a>
          <a href="#" class="nav-item">
            <i data-lucide="shield"></i>
            <span>角色管理</span>
          </a>
          <a href="#" class="nav-item">
            <i data-lucide="settings"></i>
            <span>系统设置</span>
          </a>
        </nav>
      </aside>

      <!-- Main Content -->
      <main class="app-main">
        [页面内容]
      </main>
    </div>

    <!-- Footer -->
    <footer class="app-footer">
      <p>Copyright © 2024 我的工作空间</p>
    </footer>
  </div>

  <script>
    lucide.createIcons();
  </script>
</body>
</html>
```

### 3.2 列表页模板

```html
<!-- 页面标题区 -->
<div class="page-header">
  <h1 class="page-title">用户管理</h1>
  <div class="page-actions">
    <button class="btn btn-primary">
      <i data-lucide="plus"></i>
      <span>新增用户</span>
    </button>
    <button class="btn btn-default">
      <i data-lucide="download"></i>
      <span>导出</span>
    </button>
  </div>
</div>

<!-- 搜索区域 -->
<div class="search-card card">
  <div class="search-form">
    <div class="form-item">
      <label>用户名</label>
      <input type="text" class="input" placeholder="请输入用户名">
    </div>
    <div class="form-item">
      <label>状态</label>
      <select class="select">
        <option value="">全部</option>
        <option value="enabled">启用</option>
        <option value="disabled">禁用</option>
      </select>
    </div>
    <div class="form-item">
      <button class="btn btn-primary">
        <i data-lucide="search"></i>
        <span>搜索</span>
      </button>
      <button class="btn btn-default">重置</button>
    </div>
  </div>
</div>

<!-- 数据表格 -->
<div class="table-card card">
  <table class="data-table">
    <thead>
      <tr>
        <th class="col-checkbox"><input type="checkbox"></th>
        <th>用户名</th>
        <th>姓名</th>
        <th>部门</th>
        <th>状态</th>
        <th>创建时间</th>
        <th class="col-actions">操作</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><input type="checkbox"></td>
        <td>admin</td>
        <td>系统管理员</td>
        <td>技术部</td>
        <td><span class="tag tag-success">启用</span></td>
        <td>2024-01-01 10:00</td>
        <td class="actions">
          <button class="btn-link">编辑</button>
          <button class="btn-link btn-danger">删除</button>
        </td>
      </tr>
      <tr>
        <td><input type="checkbox"></td>
        <td>zhangsan</td>
        <td>张三</td>
        <td>销售部</td>
        <td><span class="tag tag-success">启用</span></td>
        <td>2024-01-15 14:30</td>
        <td class="actions">
          <button class="btn-link">编辑</button>
          <button class="btn-link btn-danger">删除</button>
        </td>
      </tr>
    </tbody>
  </table>

  <!-- 分页 -->
  <div class="pagination">
    <span class="total">共 50 条</span>
    <div class="pager">
      <button class="pager-btn" disabled>&lt;</button>
      <button class="pager-btn active">1</button>
      <button class="pager-btn">2</button>
      <button class="pager-btn">3</button>
      <button class="pager-btn">&gt;</button>
    </div>
  </div>
</div>
```

### 3.3 表单弹窗模板

```html
<!-- 弹窗遮罩 -->
<div class="modal-overlay">
  <!-- 弹窗容器 -->
  <div class="modal">
    <!-- 弹窗头部 -->
    <div class="modal-header">
      <h3 class="modal-title">新增用户</h3>
      <button class="modal-close">&times;</button>
    </div>

    <!-- 弹窗内容 -->
    <div class="modal-body">
      <form class="form">
        <div class="form-item">
          <label class="required">用户名</label>
          <input type="text" class="input" placeholder="请输入用户名">
          <span class="form-tip">4-20位字母数字</span>
        </div>

        <div class="form-item">
          <label class="required">姓名</label>
          <input type="text" class="input" placeholder="请输入姓名">
        </div>

        <div class="form-item">
          <label class="required">手机号</label>
          <input type="text" class="input" placeholder="请输入手机号">
        </div>

        <div class="form-item">
          <label>邮箱</label>
          <input type="email" class="input" placeholder="请输入邮箱">
        </div>

        <div class="form-item">
          <label class="required">部门</label>
          <select class="select">
            <option value="">请选择部门</option>
            <option value="1">技术部</option>
            <option value="2">销售部</option>
            <option value="3">财务部</option>
          </select>
        </div>

        <div class="form-item">
          <label class="required">角色</label>
          <div class="checkbox-group">
            <label class="checkbox">
              <input type="checkbox"> 管理员
            </label>
            <label class="checkbox">
              <input type="checkbox"> 普通用户
            </label>
          </div>
        </div>

        <div class="form-item">
          <label>状态</label>
          <div class="radio-group">
            <label class="radio">
              <input type="radio" name="status" checked> 启用
            </label>
            <label class="radio">
              <input type="radio" name="status"> 禁用
            </label>
          </div>
        </div>
      </form>
    </div>

    <!-- 弹窗底部 -->
    <div class="modal-footer">
      <button class="btn btn-default">取消</button>
      <button class="btn btn-primary">确定</button>
    </div>
  </div>
</div>
```

### 3.4 详情页模板

```html
<!-- 页面标题区 -->
<div class="page-header">
  <h1 class="page-title">用户详情</h1>
  <div class="page-actions">
    <button class="btn btn-primary">
      <i data-lucide="edit"></i>
      <span>编辑</span>
    </button>
    <button class="btn btn-default" onclick="history.back()">
      <i data-lucide="arrow-left"></i>
      <span>返回列表</span>
    </button>
  </div>
</div>

<!-- 详情卡片 -->
<div class="detail-card card">
  <div class="card-header">
    <h3 class="card-title">基本信息</h3>
  </div>
  <div class="card-body">
    <div class="detail-grid">
      <div class="detail-item">
        <span class="detail-label">用户名</span>
        <span class="detail-value">admin</span>
      </div>
      <div class="detail-item">
        <span class="detail-label">姓名</span>
        <span class="detail-value">系统管理员</span>
      </div>
      <div class="detail-item">
        <span class="detail-label">手机号</span>
        <span class="detail-value">138****1234</span>
      </div>
      <div class="detail-item">
        <span class="detail-label">邮箱</span>
        <span class="detail-value">admin@example.com</span>
      </div>
      <div class="detail-item">
        <span class="detail-label">部门</span>
        <span class="detail-value">技术部 / 研发组</span>
      </div>
      <div class="detail-item">
        <span class="detail-label">状态</span>
        <span class="detail-value"><span class="tag tag-success">启用</span></span>
      </div>
      <div class="detail-item">
        <span class="detail-label">创建时间</span>
        <span class="detail-value">2024-01-01 10:00:00</span>
      </div>
    </div>
  </div>
</div>

<!-- 角色信息卡片 -->
<div class="detail-card card">
  <div class="card-header">
    <h3 class="card-title">角色信息</h3>
  </div>
  <div class="card-body">
    <div class="tag-list">
      <span class="tag tag-primary">管理员</span>
      <span class="tag tag-primary">开发人员</span>
    </div>
  </div>
</div>

<!-- 操作记录卡片 -->
<div class="detail-card card">
  <div class="card-header">
    <h3 class="card-title">操作记录</h3>
  </div>
  <div class="card-body">
    <div class="timeline">
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <div class="timeline-title">修改了用户信息</div>
          <div class="timeline-time">2024-01-15 14:30</div>
        </div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <div class="timeline-title">重置了密码</div>
          <div class="timeline-time">2024-01-10 09:00</div>
        </div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <div class="timeline-title">创建了用户</div>
          <div class="timeline-time">2024-01-01 10:00</div>
        </div>
      </div>
    </div>
  </div>
</div>
```

### 3.5 登录页模板

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>登录 - 我的工作空间</title>
  <link rel="stylesheet" href="css/style.css">
  <script src="https://unpkg.com/lucide@latest"></script>
</head>
<body class="login-page">
  <div class="login-container">
    <div class="login-card">
      <div class="login-header">
        <div class="login-logo">
          <i data-lucide="layout-grid"></i>
        </div>
        <h1 class="login-title">我的工作空间</h1>
      </div>

      <form class="login-form">
        <div class="form-item">
          <div class="input-icon">
            <i data-lucide="user"></i>
            <input type="text" class="input" placeholder="用户名">
          </div>
        </div>

        <div class="form-item">
          <div class="input-icon">
            <i data-lucide="lock"></i>
            <input type="password" class="input" placeholder="密码">
          </div>
        </div>

        <div class="form-item remember-row">
          <label class="checkbox">
            <input type="checkbox"> 记住我
          </label>
          <a href="#" class="forgot-link">忘记密码？</a>
        </div>

        <button type="submit" class="btn btn-primary btn-block btn-lg">
          登 录
        </button>
      </form>

      <div class="login-footer">
        <p>还没有账号？<a href="#">联系管理员</a></p>
      </div>
    </div>
  </div>

  <script>
    lucide.createIcons();
  </script>
</body>
</html>
```

---

## 4. 组件样式库

### 4.1 基础样式（style.css 核心部分）

```css
/* ========== 重置和基础 ========== */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: var(--font-family);
  font-size: var(--font-size-base);
  color: var(--text-primary);
  background-color: var(--bg-page);
  line-height: var(--line-height);
}

/* ========== 布局 ========== */
.app-container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.app-body {
  flex: 1;
  display: flex;
  overflow: hidden;
}

/* ========== Header ========== */
.app-header {
  height: 60px;
  background: var(--bg-white);
  border-bottom: 1px solid var(--border-color);
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 var(--spacing-lg);
  box-shadow: var(--shadow-sm);
}

.logo {
  display: flex;
  align-items: center;
  gap: var(--spacing-sm);
  font-size: var(--font-size-lg);
  font-weight: 600;
  color: var(--primary-color);
}

/* ========== Sidebar ========== */
.app-sidebar {
  width: 220px;
  background: var(--bg-white);
  border-right: 1px solid var(--border-color);
  padding: var(--spacing-md) 0;
}

.sidebar-nav {
  display: flex;
  flex-direction: column;
}

.nav-item {
  display: flex;
  align-items: center;
  gap: var(--spacing-sm);
  padding: var(--spacing-md) var(--spacing-lg);
  color: var(--text-regular);
  text-decoration: none;
  transition: all 0.2s;
}

.nav-item:hover,
.nav-item.active {
  background: var(--bg-color);
  color: var(--primary-color);
}

/* ========== Main Content ========== */
.app-main {
  flex: 1;
  padding: var(--spacing-lg);
  overflow-y: auto;
}

/* ========== Cards ========== */
.card {
  background: var(--bg-white);
  border-radius: var(--radius-base);
  box-shadow: var(--shadow-sm);
  margin-bottom: var(--spacing-md);
}

.card-header {
  padding: var(--spacing-md) var(--spacing-lg);
  border-bottom: 1px solid var(--border-lighter);
}

.card-title {
  font-size: var(--font-size-md);
  font-weight: 600;
}

.card-body {
  padding: var(--spacing-lg);
}

/* ========== Buttons ========== */
.btn {
  display: inline-flex;
  align-items: center;
  gap: var(--spacing-xs);
  padding: var(--spacing-sm) var(--spacing-md);
  font-size: var(--font-size-base);
  border: 1px solid transparent;
  border-radius: var(--radius-sm);
  cursor: pointer;
  transition: all 0.2s;
  text-decoration: none;
}

.btn-primary {
  background: var(--primary-color);
  color: white;
}

.btn-primary:hover {
  background: var(--primary-light);
}

.btn-default {
  background: var(--bg-white);
  border-color: var(--border-color);
  color: var(--text-regular);
}

.btn-default:hover {
  border-color: var(--primary-color);
  color: var(--primary-color);
}

.btn-danger {
  color: var(--danger-color);
}

.btn-block {
  width: 100%;
  justify-content: center;
}

.btn-lg {
  padding: var(--spacing-md) var(--spacing-lg);
  font-size: var(--font-size-md);
}

.btn-link {
  background: none;
  border: none;
  color: var(--primary-color);
  padding: 0 var(--spacing-xs);
  cursor: pointer;
}

.btn-link:hover {
  text-decoration: underline;
}

/* ========== Forms ========== */
.form-item {
  margin-bottom: var(--spacing-md);
}

.form-item label {
  display: block;
  margin-bottom: var(--spacing-xs);
  color: var(--text-regular);
}

.form-item label.required::after {
  content: ' *';
  color: var(--danger-color);
}

.input,
.select {
  width: 100%;
  height: 40px;
  padding: 0 var(--spacing-md);
  font-size: var(--font-size-base);
  border: 1px solid var(--border-color);
  border-radius: var(--radius-sm);
  transition: border-color 0.2s;
}

.input:focus,
.select:focus {
  outline: none;
  border-color: var(--primary-color);
  box-shadow: 0 0 0 2px rgba(64, 158, 255, 0.2);
}

.form-tip {
  font-size: var(--font-size-xs);
  color: var(--text-secondary);
  margin-top: var(--spacing-xs);
}

/* ========== Tables ========== */
.data-table {
  width: 100%;
  border-collapse: collapse;
}

.data-table th,
.data-table td {
  padding: var(--spacing-md);
  text-align: left;
  border-bottom: 1px solid var(--border-lighter);
}

.data-table th {
  background: var(--bg-page);
  font-weight: 600;
  color: var(--text-regular);
}

.data-table tbody tr:hover {
  background: var(--bg-color);
}

.col-actions {
  width: 150px;
  text-align: right;
}

/* ========== Tags ========== */
.tag {
  display: inline-block;
  padding: 2px var(--spacing-sm);
  font-size: var(--font-size-xs);
  border-radius: var(--radius-sm);
}

.tag-success {
  background: rgba(103, 194, 58, 0.1);
  color: var(--success-color);
}

.tag-warning {
  background: rgba(230, 162, 60, 0.1);
  color: var(--warning-color);
}

.tag-danger {
  background: rgba(245, 108, 108, 0.1);
  color: var(--danger-color);
}

.tag-primary {
  background: rgba(64, 158, 255, 0.1);
  color: var(--primary-color);
}

/* ========== Pagination ========== */
.pagination {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: var(--spacing-md) 0;
}

.pager {
  display: flex;
  gap: var(--spacing-xs);
}

.pager-btn {
  min-width: 32px;
  height: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--bg-white);
  border: 1px solid var(--border-color);
  border-radius: var(--radius-sm);
  cursor: pointer;
}

.pager-btn.active {
  background: var(--primary-color);
  border-color: var(--primary-color);
  color: white;
}

/* ========== Modal ========== */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal {
  width: 500px;
  max-width: 90%;
  background: var(--bg-white);
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-lg);
}

.modal-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: var(--spacing-md) var(--spacing-lg);
  border-bottom: 1px solid var(--border-lighter);
}

.modal-close {
  background: none;
  border: none;
  font-size: 24px;
  color: var(--text-secondary);
  cursor: pointer;
}

.modal-body {
  padding: var(--spacing-lg);
  max-height: 60vh;
  overflow-y: auto;
}

.modal-footer {
  display: flex;
  justify-content: flex-end;
  gap: var(--spacing-sm);
  padding: var(--spacing-md) var(--spacing-lg);
  border-top: 1px solid var(--border-lighter);
}

/* ========== Detail Page ========== */
.detail-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: var(--spacing-md);
}

.detail-item {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-xs);
}

.detail-label {
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
}

.detail-value {
  color: var(--text-primary);
}

/* ========== Timeline ========== */
.timeline {
  position: relative;
  padding-left: var(--spacing-lg);
}

.timeline-item {
  position: relative;
  padding-bottom: var(--spacing-lg);
}

.timeline-item:last-child {
  padding-bottom: 0;
}

.timeline-dot {
  position: absolute;
  left: calc(-1 * var(--spacing-lg) + 4px);
  width: 8px;
  height: 8px;
  background: var(--primary-color);
  border-radius: 50%;
}

.timeline-dot::before {
  content: '';
  position: absolute;
  left: 3px;
  top: 8px;
  width: 2px;
  height: calc(100% + var(--spacing-md));
  background: var(--border-color);
}

.timeline-item:last-child .timeline-dot::before {
  display: none;
}

.timeline-title {
  font-weight: 500;
}

.timeline-time {
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
  margin-top: var(--spacing-xs);
}

/* ========== Login Page ========== */
.login-page {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--primary-dark) 100%);
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.login-container {
  width: 100%;
  max-width: 400px;
  padding: var(--spacing-lg);
}

.login-card {
  background: var(--bg-white);
  border-radius: var(--radius-lg);
  padding: var(--spacing-xl);
  box-shadow: var(--shadow-lg);
}

.login-header {
  text-align: center;
  margin-bottom: var(--spacing-xl);
}

.login-logo {
  width: 60px;
  height: 60px;
  background: var(--bg-color);
  border-radius: var(--radius-lg);
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto var(--spacing-md);
  color: var(--primary-color);
}

.login-title {
  font-size: var(--font-size-xl);
  color: var(--text-primary);
}

.input-icon {
  position: relative;
}

.input-icon i {
  position: absolute;
  left: var(--spacing-md);
  top: 50%;
  transform: translateY(-50%);
  color: var(--text-placeholder);
}

.input-icon .input {
  padding-left: 40px;
}

.remember-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.forgot-link {
  color: var(--primary-color);
  text-decoration: none;
  font-size: var(--font-size-sm);
}

.login-footer {
  text-align: center;
  margin-top: var(--spacing-lg);
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
}

.login-footer a {
  color: var(--primary-color);
}
```

---

## 5. 文件结构

```
prototype/
├── index.html          # 入口/首页
├── login.html          # 登录页
├── list.html           # 列表页模板
├── form.html           # 表单页模板
├── detail.html         # 详情页模板
├── css/
│   └── style.css       # 样式文件
├── js/
│   └── app.js          # 交互脚本
└── assets/
    └── avatar.png      # 默认头像
```

---

## 6. 生成规则

### 6.1 页面类型选择

| 功能类型 | 生成页面 | 模板 |
|----------|----------|------|
| 登录认证 | login.html | 登录页模板 |
| 数据列表 | list.html | 列表页模板 |
| 数据新增/编辑 | form.html（弹窗嵌入） | 表单弹窗模板 |
| 数据详情 | detail.html | 详情页模板 |
| 数据统计 | dashboard.html | 仪表盘模板 |

### 6.2 内容填充规则

1. **页面标题**：使用功能名称
2. **表格字段**：按数据需求定义填充
3. **表单字段**：按输入项定义填充
4. **操作按钮**：按功能操作填充
5. **状态标签**：按数据字典填充