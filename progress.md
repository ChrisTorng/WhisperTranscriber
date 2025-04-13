1. Ask: 針對太長的音檔，它會切斷音檔再給 whisper 進行 STT 解讀。請問 initial_prompt 是否有用在每一段落，還是只有第一段有用? 後續段落是否僅有套用前一段落轉錄的文字? 我希望 initial_prompt 可以反覆套用在每一段上，也就是每一段都要有 initial_prompt 加前一段轉錄文字作為提示。
2. Agent: faster_whisper 資料夾是已經引入 repo 的原始碼的一部份，請為我直接修改。
3. Inline: 增加 debug 輸出要偵錯
4. Agent: 剛增加的 debug 輸出都沒有看到，是否 log level 要調整? 或者執行過程就不會執行到此處?
5. Agent: #terminalSelection 我看 previous segment tokens 裡大多都已包含 initial_prompt，是否不應該反覆引入? 但後面又有一些好像也沒有包含 initial_prompt，是否有什麼潛在問題?
6. Agent: #terminalSelection 目前程式，一開始執行，previous segment tokens 會越來越長，但在執行一段時間後 previous segment tokens 會清空，這是怎麼回事?
7. Ask: 請再詳細解釋為何要使用不同溫度，還有機率/壓縮率在這裡面是什麼作用。
8. Agent: 先前你修改加入 initial_prompt 的機制，應該改為只有在 reset 時才重新加入 initial_prompt，原來的應該可以全部刪掉了。