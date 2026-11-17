# RSConnect To Snap7

ABB RobotStudio Smart Component 库，用于通过 [Snap7](https://sourceforge.net/projects/snap7/) / Sharp7 将 RobotStudio 中的 I/O 信号连接到西门子 S7 系列 PLC。

## 插件文件（`plugins/`）

可直接在 RobotStudio 中安装使用：

| 文件 | 说明 |
|------|------|
| `RSConnectDIOToSnap7.rslib` | 连接 **DI/DO**（数字量输入/输出）到西门子 PLC |
| `RSConnectGIOToSnap7.rslib` | 连接 **GI/GO**（组输入/组输出）到西门子 PLC |

### 安装方法

1. 打开 RobotStudio
2. **File → Library → Install Library...**
3. 选择对应的 `.rslib` 文件

### 使用说明（属性配置）

- **PLC_Addr**：PLC 的 IPv4 地址（PLCSim 需配合 [NetToPLCSim](http://nettoplcsim.sourceforge.net/)）
- **PLC_Rack / PLC_Slot**：
  - S7-300：Rack=0, Slot=2
  - S7-400：见 HW Config
  - S7-1200/1500：Rack=0, Slot=1
- **DI/DO 版本**：`DI_Number` / `DO_Number` 设置连接数量，`DI_Address_x` / `DO_Address_x` 支持 `Ax.y`、`Qx.y`、`Mx.y`、`DBx.DBXy.z`
- **GI/GO 版本**：`GI_ByteNumber` / `GO_ByteNumber` 设置字节数，`GI_FirstByteAddress` / `GO_FirstByteAddress` 支持 `ABx`、`QBx`、`MBx`、`DBx.DBBy`
- **Connect** 信号：启动与 PLC 的连接
- **Read** 信号：手动读取一次 DI/GI（仿真运行时会连续读取；DO/GO 在变化时自动写入）

## 源码（`source/`）

两个 Visual Studio 解决方案（C#），二次开发前请阅读各仓库的 `README.md`：

- 需要更新 `ABB.Robotics.*` 引用到本机 RobotStudio SDK 路径
- 需要配置 Post Build Events 中的 `LibraryCompiler.exe` 路径
- 需要修正 XML 中的 `xsi:schemaLocation`

## 来源

基于 [DenisFR/RSConnectDIOToSnap7](https://github.com/DenisFR/RSConnectDIOToSnap7) 和 [DenisFR/RSConnectGIOToSnap7](https://github.com/DenisFR/RSConnectGIOToSnap7)（v1.0.1），遵循其 LICENSE。

错误排查可参考 [Snap7 论坛](https://sourceforge.net/p/snap7/discussion/)。
