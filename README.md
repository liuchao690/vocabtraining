# VocabHero - 背单词应用

VocabHero是一个背单词工具，采用纯前端实现，无需后端服务即可运行。

## 功能特性

- 用户登录功能
- 多种学习模式支持
- 答题方式测验学习效果
- 记录学习历史和错题本
- 记录学习锚点，下次登录从上次学习位置继续
- 可重置学习锚点

## 环境准备

### 前置要求

- Node.js 16.0 或更高版本
- npm 7.0 或更高版本

### 安装步骤

1. **克隆项目**
   ```bash
   git clone https://github.com/liuchao690/vocabtraining.git
   cd coptraining_test
   ```
2. **安装依赖**
   ```bash
   npm install
   ```

## 模式CSV文件格式说明

### 文件结构

- 所有学习模式的CSV文件都放在 `public/vocab_data/` 目录下
- 每个CSV文件对应一个学习模式
- CSV文件格式为：`单词,翻译`

### 示例

```csv
壳体,ケーシング
叶轮,インペラ
轴,シャフト
```

### 添加新的学习模式

1. 在 `public/vocab_data/` 目录下创建新的CSV文件，例如 `德中.csv`
2. 按照 `单词,翻译` 的格式添加单词
3. 更新 `public/vocab_data/index.json` 文件，将新文件名添加到数组中
   ```json
   [
     "中日1.csv",
     "中英.csv",
     "中英1.csv",
     "法中.csv",
     "英中.csv",
     "德中.csv"
   ]
   ```
4. 刷新浏览器，新的学习模式会自动加载

## 部署步骤

### 开发环境运行

```bash
npm run dev
```

然后在浏览器中访问 `http://localhost:5173`

### 生产环境部署

1. **构建项目**
   ```bash
   npm run build
   ```
2. **部署构建产物**

   构建完成后，`dist` 目录中包含了所有静态文件，可以将其部署到任何静态文件服务器上，例如：
   - Nginx
   - Apache
   - GitHub Pages
   - Vercel
   - Netlify

### Windows 部署教程

1. **安装Node.js**
   - 从 [Node.js官网](https://nodejs.org/) 下载并安装Node.js 16.0或更高版本
   - 安装完成后，打开命令提示符，运行 `node -v` 和 `npm -v` 确认安装成功
2. **克隆项目**
   - 打开命令提示符，运行：
     ```cmd
     git clone <项目地址>
     cd coptraining_test
     ```
3. **安装依赖**
   - 运行：
     ```cmd
     npm install
     ```
4. **构建项目**
   - 运行：
     ```cmd
     npm run build
     ```
5. **部署到本地服务器**
   - 安装本地服务器工具，例如 `serve`：
     ```cmd
     npm install -g serve
     ```
   - 运行：
     ```cmd
     serve dist
     ```
   - 在浏览器中访问 `http://localhost:3000`

### Linux 部署教程

1. **安装Node.js**
   - 在Ubuntu/Debian上：
     ```bash
     sudo apt update
     sudo apt install nodejs npm
     ```
   - 在CentOS/RHEL上：
     ```bash
     sudo yum install nodejs npm
     ```
   - 确认安装成功：
     ```bash
     node -v
     npm -v
     ```
2. **克隆项目**
   - 运行：
     ```bash
     git clone https://github.com/liuchao690/vocabtraining.git
     cd coptraining_test
     ```
3. **安装依赖**
   - 运行：
     ```bash
     npm install
     ```
4. **构建项目**
   - 运行：
     ```bash
     npm run build
     ```
5. **部署到Nginx**
   - 安装Nginx：
     ```bash
     sudo apt install nginx  # Ubuntu/Debian
     sudo yum install nginx  # CentOS/RHEL
     ```
   - 配置Nginx：
     ```bash
     sudo nano /etc/nginx/sites-available/vocabhero
     ```
     添加以下内容：
     ```nginx
     server {
         listen 80;
         server_name example.com;
         root /path/to/coptraining_test/dist;
         index index.html;
         
         location / {
             try_files $uri $uri/ /index.html;
         }
     }
     ```
   - 启用配置：
     ```bash
     sudo ln -s /etc/nginx/sites-available/vocabhero /etc/nginx/sites-enabled/
     sudo nginx -t
     sudo systemctl reload nginx
     ```

## 如何使用

1. **登录**
   - 使用以下默认账号登录：
     - 用户名：admin，密码：admin
     - 用户名：user1，密码：user1
     - 用户名：user2，密码：user2
2. **选择学习模式**
   - 在仪表盘上选择一个学习模式，点击进入
3. **开始学习**
   - 系统会从上次学习的位置继续，或者从开始开始
   - 选择正确的翻译
   - 系统会根据艾宾浩斯记忆曲线安排复习
4. **查看学习历史**
   - 点击"LEARNING HISTORY"查看学习历史
5. **查看错题本**
   - 点击"WRONG BOOK"查看错题本
6. **重置学习进度**
   - 在学习模式卡片上点击"🔄 Start Over"重置学习进度

## 常见问题及解决方案

### 登录失败

- 检查用户名和密码是否正确
- 确保 `users.csv` 文件存在于 `public` 目录中

### 学习模式不显示

- 检查 `public/vocab_data/` 目录是否存在
- 检查 `public/vocab_data/index.json` 文件是否正确配置
- 检查CSV文件格式是否正确

### 单词不显示

- 检查CSV文件格式是否正确
- 确保CSV文件编码为UTF-8

### 本地存储问题

- 清除浏览器缓存和本地存储
- 检查浏览器是否允许本地存储

## 技术栈

- React 18
- Vite
- JavaScript
- LocalStorage

## 许可证

MIT
