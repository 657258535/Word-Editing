# Word-Editing

一个功能完善的在线Word文档查看与编辑工具，支持.doc和.docx格式文件的上传、预览、编辑和保存。

## 🚀 功能特点

- **文档上传**：支持选择本地Word文档或直接拖放文件上传
- **格式转换**：自动将Word文档转换为HTML格式进行预览和编辑
- **富文本编辑**：提供强大的文本编辑功能，支持格式化、图片插入、列表等
- **图片处理**：自动将文档中的图片转换为Base64格式，无需额外服务器存储
- **文档保存**：可将编辑后的内容保存为Word文档（.docx格式）
- **响应式设计**：自适应不同屏幕尺寸，提供良好的用户体验
- **实时预览**：编辑内容实时显示，所见即所得

## 🛠️ 技术栈

- **前端框架**：原生HTML5 + CSS3 + JavaScript
- **文档转换**：[Mammoth.js](https://github.com/mwilliamson/mammoth.js) - 用于Word文档转HTML
- **富文本编辑器**：[TinyMCE](https://www.tiny.cloud/) - 提供专业的文本编辑功能
- **文件处理**：[FileSaver.js](https://github.com/eligrey/FileSaver.js/) - 客户端文件保存
- **HTML转Word**：[html-docx-js](https://github.com/evidenceprime/html-docx-js) - 将HTML转换为Word格式

## 📦 快速开始

### 1. 克隆项目

```bash
git clone https://github.com/657258535/Word-Editing.git
cd Word-Editing
```

### 2. 运行项目

由于项目是纯前端实现，无需服务器环境，直接在浏览器中打开 `index.html` 文件即可使用：

```bash
# 在Windows上
start index.html

# 在macOS上
open index.html

# 在Linux上
xdg-open index.html
```

或者通过本地服务器运行（推荐）：

```bash
# 使用Python 3
python -m http.server 8000

# 使用Node.js (需要安装http-server)
npx http-server -p 8000

# 然后在浏览器中访问 http://localhost:8000
```

## 📖 使用说明

### 上传文档

1. **点击上传**：点击"选择Word文档"按钮，从本地文件系统选择.doc或.docx格式的文件
2. **拖放上传**：直接将.doc或.docx文件拖放到上传区域

### 编辑文档

文档上传后，会自动转换为HTML格式并显示在编辑器中：

- 使用工具栏进行文本格式化（粗体、斜体、下划线等）
- 插入列表、表格、图片等内容
- 使用撤销/重做功能管理编辑历史

### 保存文档

点击右上角的"保存Word文档"按钮，即可将编辑后的内容保存为.docx格式的Word文档到本地。

## 📋 浏览器兼容性

| 浏览器 | 版本要求 |
|--------|----------|
| Chrome | 60+      |
| Firefox | 55+     |
| Safari | 12+      |
| Edge | 79+      |

## 🎨 项目结构

```
Word-Editing/
├── index.html    # 主页面文件（包含所有HTML、CSS和JavaScript代码）
├── README.md     # 项目说明文档
├── LICENSE       # 许可证文件
└── .gitattributes # Git属性配置
```

## 🔧 核心功能实现

### 1. 文档转换

使用Mammoth.js将Word文档转换为HTML：

```javascript
const result = await mammoth.convertToHtml({ arrayBuffer: arrayBuffer }, {
    convertImage: mammoth.images.imgElement(function(image) {
        return image.read("base64").then(function(base64) {
            return `<img src="data:${image.contentType};base64,${base64}" alt="文档图片">`;
        });
    })
});
```

### 2. 富文本编辑

使用TinyMCE提供专业的编辑功能：

```javascript
tinymce.init({
    selector: '#editor',
    width: '100%',
    height: '100%',
    plugins: 'advlist autolink lists link image charmap print preview anchor searchreplace visualblocks code fullscreen insertdatetime media table paste code help wordcount',
    toolbar: 'undo redo | formatselect | bold italic backcolor | alignleft aligncenter alignright alignjustify | bullist numlist outdent indent | removeformat | help'
});
```

### 3. 文档保存

使用html-docx-js和FileSaver.js将HTML转换为Word文档并保存：

```javascript
const docxBlob = htmlDocx.asBlob(htmlContent);
saveAs(docxBlob, fileName);
```

## 📝 许可证

本项目采用MIT许可证，详见[LICENSE](LICENSE)文件。

## 🤝 贡献

欢迎提交Issue和Pull Request来改进项目！

## 📧 联系方式

如有问题或建议，欢迎通过以下方式联系：

- GitHub Issues: [https://github.com/657258535/Word-Editing/issues](https://github.com/657258535/Word-Editing/issues)

---

**享受在线编辑Word文档的便捷体验！** ✨
