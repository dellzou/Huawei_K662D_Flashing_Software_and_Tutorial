# 华为 K662D 工具包

配套文章：[华为 K662D 从猫改光猫：开 Telnet、改 boardinfo 与 R22 升级](https://xiaozou123.cn/huawei-k662d-fttr-optical-modem-mode/)

K662D 是 FTTR 从机：2GE + Wi-Fi 6，光纤或以太上行，出厂必须配合 HN8145XR 使用。改 boardinfo 可以把它变成通用版 AP，或独立光猫。

## 三种身份

| 身份 | 0x0000001b | customize.txt |
|---|---|---|
| 运营商从机 | DESKCTAP / DESKUNAP / DESKCMCC4AP | `COMMON DESKxxxAP:FTTRAP` |
| 通用版 AP | FTTREDGE | `COMMON FTTREDGE` |
| 独立光猫 | CHINA4 | `COMMON CHINA4` |

注意是 `CHINA4`，不是 V173-50 的 `CHINA`。

## 文件

| 文件 | 字节 | SHA256（前 32 位） |
|---|---|---|
| `HN8145XR_shell.bin` | 13,569 | `a09b714957eea0da268b5267cbe6aed6…` |
| `HW_Dollar2.exe` | 161,280 | `d3110469d8cccc7ca479105393e047fa…` |
| `Huawei_Config_Crypto.exe` | 1,794,560 | `8f005af234f73a456f5e4a127ed4624c…` |
| `ONT_V500R19C00.exe` | 3,503,060 | `a3dfc3daaf05fbff5b0da523dbb50b07…` |
| `V500R019_C20C30_shell9.bin` | 13,569 | `07a34e5878cba76aceef9027301df706…` |
| `putty.exe` | 574,976 | `a92c1d668f6d060db06535ad346221d2…` |
| `r20shell.bin` | 17,665 | `a247b6b6095139da2ec8b679a1d85c78…` |
| `tftpd64.exe` | 146,656 | `988292db5e71fa50b090ce2bfe668137…` |

三个补全包按固件代际选：R021 用 `HN8145XR_shell.bin`，R020 用 `r20shell.bin`，R019 的 C20/C30 批次用 `V500R019_C20C30_shell9.bin`。

## Release

`K662d_V500R021C00SPC156.bin`，43 MB。R22 不靠本地刷，是先刷到 R21 S156 后由主猫推送。

## 注意

- 改之前备份 `hw_boardinfo`、`hw_boardinfo.bak`、`customize.txt` 三个文件，缺一不可。
- 用 `restorehwmode.sh` 变成光猫模式后，切不回 AP，只能回传整套备份。
- 工具无签名，杀软会拦，SHA256 对得上再用。

