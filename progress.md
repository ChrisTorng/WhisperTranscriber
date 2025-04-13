1. Ask: 針對太長的音檔，它會切斷音檔再給 whisper 進行 STT 解讀。請問 initial_prompt 是否有用在每一段落，還是只有第一段有用? 後續段落是否僅有套用前一段落轉錄的文字? 我希望 initial_prompt 可以反覆套用在每一段上，也就是每一段都要有 initial_prompt 加前一段轉錄文字作為提示。
2. Agent: faster_whisper 資料夾是已經引入 repo 的原始碼的一部份，請為我直接修改。
3. Inline: 增加 debug 輸出要偵錯
4. Agent: 剛增加的 debug 輸出都沒有看到，是否 log level 要調整? 或者執行過程就不會執行到此處?
5. Agent: #terminalSelection 我看 previous segment tokens 裡大多都已包含 initial_prompt，是否不應該反覆引入? 但後面又有一些好像也沒有包含 initial_prompt，是否有什麼潛在問題?
6. Agent: #terminalSelection 目前程式，一開始執行，previous segment tokens 會越來越長，但在執行一段時間後 previous segment tokens 會清空，這是怎麼回事?
7. Ask: 請再詳細解釋為何要使用不同溫度，還有機率/壓縮率在這裡面是什麼作用。
8. Agent: 先前你修改加入 initial_prompt 的機制，應該改為只有在 reset 時才重新加入 initial_prompt，原來的應該可以全部刪掉了。

以下 9-16 因數值都不對而放棄:
9.  Agent: 在音檔被切分時，計算並顯示每段音檔的轉錄耗時，平均每分鐘轉錄音檔多久及多少個字。轉錄完成後，顯示所有轉錄耗時及平均每分鐘轉錄音檔多久及多少個字。以上的顯示不止是在 debug 輸出，也加入 txt 輸出，但不能加入 srt 檔。
10. Agent: 我要的「每段顯示」的每段，是指每個 segment，大約 30 秒內，如 #terminalSelection 是兩段。目前顯示的段落處理耗時的數量太多了，我要的是一段顯示一筆而已。另 txt 每段輸出，一樣不是逐句輸出，是逐段。另輸出處理耗時要單獨成行，不要像目前的附在每行之後。也就是原本的 txt 輸出轉錄行不要動，只有新增行來顯示處理耗時。
11. Agent: 修正錯誤
12. Edit: @workspace /fix
13. Ask o1: 請修正此行錯誤。
14. Agent: 目前的段落 字數/分鐘: 2.00 每個都是 2.00，我認為都是錯誤。總計中的 總音檔長度/平均處理速度/ 平均字數/分鐘 值我認為也是錯誤的，請仔細檢查。
15. Agent: 是
16. Agent: #terminalSelection 修正錯誤

退回 commit 步驟 8 繼續:
17. 