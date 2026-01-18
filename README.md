# perfectPixel-ComfyUI
将杂乱的 AI 像素艺术细化并量化为干净、完美像素的Perfect Pixel 的 ComfyUI 节点。

PerfectPixel 代码：https://github.com/theamusing/perfectPixel

本项目将 PerfectPixel 的项目写成 ComfyUI 的节点插件，以便调用。具体 PerfectPixel 效果与只用方法参考源代码 github 地址即可。

![节点示例](./Assets/example.png)

## Getting Started

将本项目的 `PerfectPixelComfy` 文件直接复制进 `ComfyUI/custom_nodes` 中，重启 ComfyUI 即可。

在左边的节点搜索栏中搜索 `Perfect Pixel(Grid Restore)` 即可找到本节点。节点具体位于 `图像 -> 后处理 -> Perfect Pixel(Grid Restore)` 中。

项目依赖 numpy 和 OpenCV（可选）库：

````bash
pip install numpy
pip install opencv-python
````

