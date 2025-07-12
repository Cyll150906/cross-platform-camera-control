# 跨平台视频设备控制工具

一个兼容v4l2-ctl的跨平台视频设备控制工具，支持Windows、Linux和macOS。

## 🌟 功能

- ✅ **跨平台支持**: Windows, Linux, macOS
- ✅ **设备枚举**: 列出所有可用的视频设备
- ✅ **格式查询**: 显示支持的视频格式、分辨率、帧率
- ✅ **参数控制**: 查看和设置设备控制参数（亮度、对比度等）
- ✅ **v4l2-ctl 兼容**: 命令行界面兼容v4l2-ctl
- ✅ **多后端支持**: DirectShow (Windows), V4L2 (Linux), AVFoundation (macOS), OpenCV (备用)

## 🚀 快速开始

### 安装

```bash
# 从源码安装
git clone https://github.com/yaoian/cross-platform-camera-control.git
cd cross-platform-camera-control
pip install -r requirements.txt

# 或者作为包安装
pip install cross-platform-camera-control
```

### 基本用法

```bash
# 显示帮助
python v4l2_ctl_cross.py -h

# 列出所有视频设备
python v4l2_ctl_cross.py --list-devices

# 显示支持的格式
python v4l2_ctl_cross.py -d /dev/video0 --list-formats-ext

# 显示设备控件
python v4l2_ctl_cross.py -d /dev/video0 -L

# 设置控制参数
python v4l2_ctl_cross.py -d /dev/video0 -c brightness=50
python v4l2_ctl_cross.py -d /dev/video0 -c brightness=50,contrast=75
```

## 📋 示例输出

**设备列表:**
```
USB Camera: (USB\VID_1BCF&PID_2C9A&MI_00\6&33F8E1A6&0&0000):
        /dev/video0
```

**控制参数:**
```
User Controls

brightness: 50 (range: 0-100) - Brightness
contrast: 50 (range: 0-100) - Contrast
saturation: 50 (range: 0-100) - Saturation
```

## 🏗️ 架构

```
VideoDeviceController (抽象基类)
├── WindowsVideoController (Windows 实现)
│   ├── DirectShow API (主要)
│   └── OpenCV (备用)
├── LinuxVideoController (Linux 实现)
│   └── V4L2 API
└── MacOSVideoController (macOS 实现)
    └── AVFoundation API
```

## 📦 平台特定依赖

### Windows
```bash
pip install pywin32 opencv-python
```

### Linux
```bash
pip install v4l2-python opencv-python
# 或
sudo apt-get install python3-v4l2
```

### macOS
```bash
pip install pyobjc opencv-python pyobjc-framework-AVFoundation
```

## 📁 项目结构

```
├── video_device_controller.py  # 抽象基类和接口
├── windows_directshow.py       # Windows DirectShow 实现
├── opencv_fallback.py          # OpenCV 备用实现
├── v4l2_ctl_cross.py          # 命令行界面
├── setup.py                   # 包配置
├── requirements.txt           # 依赖
└── README.md                  # 项目文档
```

## 🔧 开发状态

### ✅ 已完成功能
- [x] 项目架构设计
- [x] Windows 平台基本实现
- [x] OpenCV 备用方案
- [x] 命令行界面
- [x] 设备枚举
- [x] 基本格式查询
- [x] 基本参数控制

### 🚧 进行中
- [ ] 完善 DirectShow 实现
- [ ] Linux V4L2 实现
- [ ] macOS AVFoundation 实现
- [ ] 高级参数控制
- [ ] 错误处理优化
- [ ] 单元测试
- [ ] 性能优化

## 📊 与原始 C++ 项目对比

| 功能 | C++ v4w2-ctl | Python 版本 |
|---|---|---|
| 平台支持 | 仅 Windows | Windows/Linux/macOS |
| 设备枚举 | ✅ | ✅ |
| 格式查询 | ✅ | ✅ (基本) |
| 参数控制 | ✅ | ✅ (基本) |
| DirectShow | ✅ 完成 | 🔄 开发中 |
| V4L2 支持 | ❌ | 🔄 计划中 |
| 安装 | 需要编译 | pip install |

## 🛠️ 构建原始 C++ 项目

```bash
# 使用 MinGW
g++ -o v4w2-ctl.exe v4w2-ctl.cpp ClsDirectShow.cpp -lole32 -loleaut32 -lstrmiids

# 测试
./v4w2-ctl.exe -h
./v4w2-ctl.exe --list-devices
```

## 🤝 贡献

1. Fork 项目
2. 创建功能分支
3. 提交你的修改
4. 推送到分支
5. 打开一个 Pull Request

## 📄 许可证

MIT 许可证 - 与原始项目相同

## 🙏 致谢

- 原始项目作者: hry2566
- OpenCV 社区
- Python 社区库维护者

## 📞 支持

如果你遇到任何问题或有任何疑问，请在 GitHub 上 [提出一个 issue](https://github.com/yaoian/cross-platform-camera-control/issues)。