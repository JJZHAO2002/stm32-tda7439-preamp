# STM32 + TDA7439 智能音频前级（KiCad 草稿）

项目：STM32 + TDA7439 智能音频前级（KiCad 草稿）
版本：v0.1 草稿
作者：由 Copilot 生成（JJZHAO2002 会话）

默认配置（已确认）：
- MCU: STM32F103C8T6 (LQFP48)
- 音频处理: TDA7439
- 显示: SSD1306 128x64 I2C 模组（I2C 共线 PB6/PB7）
- 红外接收: TSOP4838 (PA0)
- 输出缓冲运放: MCP6002 (SOIC-8, 单电源示例)
- 电源: 单 12V 输入 -> LDO_AUDIO (V_AUDIO) 与 LDO_3V3 (MCU/logic)
- 存储: MCU 内 Flash（无外接 EEPROM）
- PCB: 4 层 (Top / GND / PWR / Bottom)

本交付物（草稿）包括：
- connections.netlist：关键 net 与引脚映射（用于在 KiCad 中建立原理图）
- bom.csv：初步 BOM（可用于元件下单）
- sheets.md：每个原理图页的说明与 symbol/footprint 建议（便于在 KiCad 中绘制）
- placement_and_pcb_rules.md：元件放置建议、层叠和布线/DRC 规则
- next_steps.txt：后续可选工作（生成 .sch/.kicad_pcb 并上传 GitHub）

说明：这是一份“草稿规格/净表”，可直接用于在 KiCad 中绘制原理图与 PCB。我可以把这些内容直接生成 KiCad 项目文件并打包为 ZIP（或上传到 GitHub），只需你确认或提供仓库信息。
