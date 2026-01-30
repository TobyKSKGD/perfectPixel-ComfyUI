# perfectPixel-ComfyUI

将杂乱的 AI 像素艺术细化并量化为干净、完美像素的 **Perfect Pixel** 的 ComfyUI 节点。

> Perfect Pixel 原项目（核心算法）：
>  https://github.com/theamusing/perfectPixel

本项目**仅提供 Perfect Pixel 的 ComfyUI 节点封装（插件皮）**，不包含核心算法实现本身。
 节点运行时会调用 **Perfect Pixel 官方 Python 包** 中的实现，以保证算法始终与原作者保持一致。

------

## 节点说明

![节点示例](./Assets/example.png)

**Perfect Pixel (Grid Restore)** 节点可调节参数：

- **sampling**：采样方式
- **export_scale**：输出缩放比例
- **backend**：
  - `Auto`：自动选择可用后端
  - `OpenCV Backend`：基于 OpenCV 的高性能版本（推荐）
  - `Lightweight Backend`：仅 NumPy 的轻量版本（无 OpenCV）

------

## Getting Started

### 一键安装（推荐）

如果你已经安装了 Git，请在 `ComfyUI/custom_nodes` 目录下执行：

```bash
git clone https://github.com/TobyKSKGD/perfectPixel-ComfyUI.git
```

然后 **在 ComfyUI 使用的 Python 环境中** 安装 Perfect Pixel 官方包：

```bash
pip install "perfect-pixel[opencv]"
```

安装完成后，重启 ComfyUI 即可。

> ⚠️ 注意：
>  **必须使用 ComfyUI 正在运行的 Python 环境来执行 pip install**。
>  如果你不确定如何在 Windows 下为 ComfyUI 安装 Python 依赖，请查看本文档最后的
>  👉[在 ComfyUI 的 Python 环境中安装依赖（Windows）](#在 ComfyUI 的 Python 环境中安装依赖（Windows）)

------

### 手动安装（不推荐，但可用）

> ⚠️ 手动安装适用于你**无法使用 pip** 或 **需要完全离线部署** 的情况。

1. **下载本仓库（节点插件皮）**

   将 `perfectPixel-ComfyUI` 整个文件夹复制到：

   ```
   ComfyUI/custom_nodes
   ```

2. **下载 Perfect Pixel 原作者仓库**

   前往原项目仓库并下载或克隆：

   ```
   https://github.com/theamusing/perfectPixel
   ```

3. **复制核心算法文件**

   从原作者仓库中，将以下两个文件：

   ```
   ./src/perfect_pixel/perfect_pixel.py
   ./src/perfect_pixel/perfect_pixel_noCV2.py
   ```

   复制到节点目录：

   ```
   ComfyUI/custom_nodes/perfectPixel-ComfyUI/PerfectPixelComfy/
   ```

4. 重启 ComfyUI

------

### 节点位置

重启后，在左侧节点搜索栏中搜索：

```
Perfect Pixel (Grid Restore)
```

节点位置为：

```
Image → Post Processing → Perfect Pixel (Grid Restore)
```

------

## 依赖项说明

### 推荐方式（自动同步作者更新）

使用官方 Python 包（推荐）：

```bash
pip install "perfect-pixel[opencv]"
```

- 自动包含：
  - `numpy`
  - `opencv-python`
- 后续作者更新算法后，只需 `pip install -U perfect-pixel` 即可同步

------

### 仅 NumPy（轻量模式）

```bash
pip install perfect-pixel
```

------

## 在 ComfyUI 的 Python 环境中安装依赖（Windows）

⚠️ **非常重要：ComfyUI 通常使用的是“内置 Python”，而不是你的系统 Python / Conda。**

### 第一步：确认 ComfyUI 使用的 Python

在 Windows 下运行任意一个 ComfyUI 启动脚本（如 `run_cpu.bat`、`run_nvidia_gpu.bat`）。

在启动日志中找到类似内容：

```
** Python executable: G:\ComfyUI\ComfyUI_windows_portable\python_embeded\python.exe
```

这一行中的路径，就是 **ComfyUI 正在使用的 Python 环境**。

------

### 第二步：使用该 Python 安装依赖

请在命令行中，使用你自己的路径替换下面的示例：

```
[你的 ComfyUI Python 路径]\python.exe -m pip install -U pip
[你的 ComfyUI Python 路径]\python.exe -m pip install "perfect-pixel[opencv]"
```

#### 示例（Windows Portable 版本）：

```bash
G:\ComfyUI\ComfyUI_windows_portable\python_embeded\python.exe -m pip install -U pip
G:\ComfyUI\ComfyUI_windows_portable\python_embeded\python.exe -m pip install "perfect-pixel[opencv]"
```

> ❗不要使用：
>
> ```bash
> pip install xxx
> ```
>
> 如果你不确定当前 pip 属于哪个 Python，请**始终使用 `python.exe -m pip` 的方式**。

------

## 设计说明（给进阶用户）

- 本节点**不内置 Perfect Pixel 核心算法代码**
- 节点仅负责：
  - ComfyUI 数据结构适配
  - 后端选择与参数桥接
- 算法实现全部来自：
  - `pip install perfect-pixel`
- 这样可以：
  - 避免代码重复
  - 自动跟随原作者更新
  - 减少维护成本与版本分叉
