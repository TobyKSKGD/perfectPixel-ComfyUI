# perfectPixel-ComfyUI
将杂乱的 AI 像素艺术细化并量化为干净、完美像素的Perfect Pixel 的 ComfyUI 节点。

PerfectPixel 代码：https://github.com/theamusing/perfectPixel

本项目仅将 PerfectPixel 的项目写成 ComfyUI 的节点插件，以便调用。具体 PerfectPixel 效果与使用方法参考源代码 github 地址即可。

![节点示例](./Assets/example.png)

Perfect Pixel(Grid Restore) 节点可调节参数为：

- sampling：采样方式
- export_scale：缩放/输出比例
- backend：Auto（自动选择）、OpenCV Backend（带 OpenCV 版本）、Lightweight Backend（轻量级，不带 OpenCV 版本）

## Getting Started

### 一键安装

如果已经安装了 git，在 `ComfyUI/custom_nodes` 下直接使用下面命令安装并重启 ComfyUI 即可：

````bash
git clone https://github.com/TobyKSKGD/perfectPixel-ComfyUI.git
````

### 手动安装

将本项目下载，`perfectPixel-ComfyUI` 项目文件（整个文件）直接复制进 `ComfyUI/custom_nodes` 中，重启 ComfyUI 即可。

在左边的节点搜索栏中搜索 `Perfect Pixel(Grid Restore)` 即可找到本节点。节点具体位于 `图像 -> 后处理 -> Perfect Pixel(Grid Restore)` 中。

## 依赖项

项目依赖 numpy 和 OpenCV（可选）库：

````bash
pip install numpy
pip install opencv-python
````

