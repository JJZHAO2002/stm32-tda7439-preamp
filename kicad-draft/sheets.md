KiCad 原理图页建议（hierarchical sheets）:

SHEET: power.sch
- 内容: DC IN jack (J1), 保护元件 (fuse, TVS), LDO_AUDIO, LDO_3V3, decoupling caps, power nets (VIN_12V, V_AUDIO, V_3V3), CHASSIS_GND net tie
- Symbols/footprints:
  - J1_PWR -> DC_JACK_PCB
  - LDOs -> SOT23-5 footprints, add adj caps per datasheet
  - TVS -> SMBJ or SMD part on VIN

SHEET: audio_frontend.sch
- 内容: RCA inputs (J_RCA_INx), input RC/FB/ferrite, TDA7439 symbol U2, input coupling caps, audio ground pour net (GND_ANALOG)
- Footprint:
  - RCA -> RCA-FEMALE (TH)
  - TDA7439 -> use generic SOIC or package from manufacturer; ensure pin mapping matches datasheet
  - coupling caps -> 0805 (2.2uF or 4.7uF)

SHEET: mcu_ui.sch
- 内容: U1 STM32F103 symbol, I2C pullups, SSD1306 module connector, encoder (ENC A/B + push), buttons, IR receiver symbol
- Footprint:
  - U1 -> LQFP48_7x7mm (check KiCad library)
  - SSD1306 -> 4-pin header or module footprint (0.1" x 4)
  - Encoder -> through-hole 5-pin or module footprint
  - TSOP -> SOT-23-3 or special footprint

SHEET: outputs_connectors.sch
- 内容: Output buffers (U3 MCP6002), output coupling caps, RCA_OUT connectors, testpoints, SWD header
- Footprint:
  - MCP6002 -> SOIC-8
  - RCA_OUT -> RCA-FEMALE
  - SWD -> 2x5 1.27/2.54mm as needed

符号/封装映射建议（KiCad 标准库关键名参考）
- STM32F103C8T6 -> Device: "STM32F1xx" symbol from community libs; footprint LQFP48
- MCP6002 -> "MCP6002" symbol in op amp lib; footprint SOIC-8
- TDA7439 -> 若无现成 symbol，请用 generic IC symbol 并手动映射引脚；footprint 根据 datasheet 选 SOIC/SSOP
- RCA -> Connector library -> "RCA-Female" 或 自建 footprint
- SSD1306 module -> 使用 generic 4pin module header footprint
