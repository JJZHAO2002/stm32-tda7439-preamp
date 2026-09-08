PCB 层叠（推荐 4 层）：
- L1 Top: 元件与信号
- L2 GND: 整面接地平面（优先）
- L3 PWR: V_AUDIO / V_3V3 (可分割)
- L4 Bottom: 信号 / 辅助

板材参数（建议）
- Copper: 1 oz
- Min track width: 8 mil (0.2 mm) for signals, 24–40 mil for power depending on current
- Min annular ring: 0.15 mm
- Via drill: 0.3–0.4 mm

元件放置优先级（物理位置与对齐）
1. RCA 输入/输出：放在板边（机箱侧），外壳接地 pad 到 CHASSIS_GND
2. TDA7439：靠近 RCA 输入，短音频路径
3. 输出缓冲 (MCP6002)：靠近 TDA 输出与 RCA 输出
4. 模拟 LDO 与 decaps：靠近 TDA 与 buffer
5. MCU 与 OLED、编码器、按键：靠面板侧，方便走线到面板孔位
6. IR 接收：放在板边无遮挡、前面板视野区域
7. SWD：靠近 MCU，便于编程

接地处理
- 在 4 層设计中以 L2 為整面地；將敏感模擬元件地直接連接到 L2
- RCA 外殼使用 CHASSIS_GND，若需把 CHASSIS_GND 與 GND_IN（板地）連接，使用單點或可焊跳線/淨 tie（避免地回路）

走線與 EMI
- 模擬信號盡量短且對稱走線（L/R 一起），遠離 MCU 高速線
- I2C 上加 33R 串聯阻尼（靠近 MCU），並在 pull-up 一側放置上拉電阻
- 在 I2C 與其他數字信號周圍設置 keepout 區，避免與模擬敏感線並行

測試點與調試
- 放置 TP_V3V3, TP_V_AUDIO, TP_GND, TP_I2C_SCL, TP_I2C_SDA, TP_TDA_OUT_L, TP_TDA_OUT_R
- 在 TDA 的 SCL/SDA 附近放置小 I2C test header（2 pin 或 4 pin），便於邏輯分析器

DRC 建議
- 設置 net class: AUDIO (12 mil), I2C (8 mil), POWER (40 mil)
- Keepout: 將數字高速區域與模擬區域之間設為 keepout buffer 3–5 mm
- Zone pour: GND pour on L1 over L2, use thermals for SMD pads but solid for large ground pads near RCA

製造與裝配注意
- RCA 整理：RCA 插座的機械固定區域加銅鉚合或加支撐孔
- 避免在 RCA 側面放置高零件（如大型電解電容）會導致裝殼空間衝突
- 在 LDO、散熱器或熱敏器件下增加額外銅層以幫助散熱
