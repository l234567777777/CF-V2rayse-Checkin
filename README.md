# 鑷姩绛惧埌绯荤粺

> 鍩轰簬 Cloudflare Workers 鐨勬満鍦鸿嚜鍔ㄧ鍒拌剼鏈紝鏀寔 V2rayse 鍜?SSPanel 涓ょ鏈哄満绫诲瀷锛屽唴缃?Web 绠＄悊闈㈡澘銆?
## 鍔熻兘鐗规€?
- **鍙屽钩鍙版敮鎸?*锛歏2rayse / SSPanel 鏈哄満鑷姩绛惧埌
- **Web 绠＄悊闈㈡澘**锛氬彲瑙嗗寲閰嶇疆銆佹墜鍔ㄨЕ鍙戠鍒般€佹煡鐪嬫棩蹇?- **Telegram 鎺ㄩ€?*锛氱鍒扮粨鏋滃疄鏃舵帹閫佸埌 TG锛堟敮鎸佽嚜瀹氫箟 Bot 鎴栧唴缃?Bot锛?- **瀹氭椂浠诲姟**锛氭敮鎸?Cloudflare Cron Trigger 鑷姩鎵ц
- **Cookie 鑷姩绠＄悊**锛氱櫥褰曟€佽嚜鍔ㄧ淮鎶わ紝鏃犻渶鎵嬪姩骞查
- **閲嶈瘯鏈哄埗**锛氬け璐ヨ嚜鍔ㄩ噸璇?3 娆?
## 蹇€熷紑濮?
### 1. 閮ㄧ讲鍒?Cloudflare Workers

1. 鐧诲綍 [Cloudflare Workers](https://workers.cloudflare.com/)
2. 鍒涘缓鏂?Worker
3. 灏?`index.js` 鍐呭澶嶅埗鍒?Worker 缂栬緫鍣ㄤ腑
4. 淇濆瓨骞堕儴缃?
### 2. 閰嶇疆鐜鍙橀噺

鍦?Worker 璁剧疆 鈫?**Variables and Secrets** 涓坊鍔狅細

| 鍙橀噺鍚?| 蹇呭～ | 璇存槑 |
|--------|------|------|
| `JC` / `DOMAIN` | 鉁?| 鏈哄満鍩熷悕锛堝 `https://xxx.com`锛?|
| `ZH` / `USER` | 鉁?| 鐧诲綍閭 |
| `MM` / `PASS` | 鉁?| 鐧诲綍瀵嗙爜 |
| `TYPE` | 鉁?| 鏈哄満绫诲瀷锛歚v2rayse` 鎴?`sspanel` |
| `TGTOKEN` / `TG_TOKEN` | 鉂?| Telegram Bot Token锛堣嚜瀹氫箟 Bot锛?|
| `TGID` / `TG_ID` | 鉂?| Telegram Chat ID |

> **娉ㄦ剰**锛歚TGTOKEN` 鍜?`TGID` 閮戒笉濉椂锛屼娇鐢ㄥ唴缃?Bot 鎺ㄩ€侊紙闇€濉啓 `TGID`锛夈€?
### 3. 璁剧疆瀹氭椂浠诲姟

鍦?Worker 璁剧疆 鈫?**Triggers** 鈫?**Cron Triggers** 涓坊鍔狅細

```
0 6 * * *
```

琛ㄧず姣忓ぉ鏃╀笂 6:00 鑷姩鎵ц绛惧埌銆?
### 4. 璁块棶绠＄悊闈㈡澘

閮ㄧ讲鍚庤闂?Worker 鐨?URL锛堝 `https://your-worker.your-subdomain.workers.dev/`锛夛紝杈撳叆瀵嗙爜鍗冲彲鐧诲綍绠＄悊闈㈡澘銆?
闈㈡澘鍔熻兘锛?- 鏌ョ湅褰撳墠閰嶇疆淇℃伅锛堣劚鏁忔樉绀猴級
- 鎵嬪姩瑙﹀彂绛惧埌
- 娴嬭瘯 Telegram 鎺ㄩ€?- 瀹炴椂鏌ョ湅绛惧埌鏃ュ織

## 椤圭洰缁撴瀯

```
鈹溾攢鈹€ index.js          # 涓绘枃浠讹紙Cloudflare Worker 鍏ュ彛锛?鈹溾攢鈹€ README.md         # 椤圭洰璇存槑
鈹溾攢鈹€ wrangler.toml     # Cloudflare Workers 閰嶇疆鏂囦欢锛堝彲閫夛級
鈹斺攢鈹€ .gitignore        # Git 蹇界暐瑙勫垯
```

## 鎶€鏈爤

- **Runtime**: Cloudflare Workers (V8 Isolate)
- **API**: Fetch API
- **Auth**: SHA-256 鍝堝笇楠岃瘉
- **UI**: 鍘熺敓 HTML/CSS/JS锛堟棤妗嗘灦渚濊禆锛?
## 瀹夊叏璇存槑

- 绠＄悊闈㈡澘浣跨敤 SHA-256 鍝堝笇楠岃瘉锛屽瘑鐮佷笉瀛樺偍鍦ㄥ鎴风
- 閰嶇疆淇℃伅鍦ㄩ潰鏉夸腑鑴辨晱鏄剧ず
- Telegram 鎺ㄩ€佷腑鐨勫瘑鐮佷娇鐢?`<tg-spoiler>` 鏍囩闅愯棌

## 甯歌闂

**Q: 绛惧埌杩斿洖"绛惧埌澶辫触"浣嗗疄闄呮垚鍔熶簡锛?*

A: 鏌愪簺 V2rayse 绔欑偣杩斿洖鐨?JSON 缁撴瀯涓嶅悓锛堝 `summary.points` 鑰岄潪 `awardedPoints`锛夈€備唬鐮佸凡鍐呯疆澶氱鎴愬姛鍒ゅ畾閫昏緫锛屽閬囬棶棰樿鏌ョ湅鏃ュ織涓殑鍘熷鍝嶅簲銆?
**Q: 濡備綍鏌ョ湅璇︾粏鏃ュ織锛?*

A: 鍦ㄧ鐞嗛潰鏉跨偣鍑?鎵嬪姩鎵ц绛惧埌"锛屾棩蹇椾細瀹炴椂鏄剧ず鍦ㄥ彸渚ф帶鍒跺彴銆備篃鍙湪 Cloudflare Workers 鐨?**Logs** 涓煡鐪嬨€?
**Q: 鏀寔澶氫釜鏈哄満鍚屾椂绛惧埌鍚楋紵**

A: 褰撳墠鐗堟湰姣忎釜 Worker 瀹炰緥鍙敮鎸佷竴涓満鍦恒€傚闇€澶氭満鍦猴紝鍙儴缃插涓?Worker 瀹炰緥銆?
## License

MIT