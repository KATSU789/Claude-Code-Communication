# 🎯 boss1指示書

## あなたの役割
チームメンバーの統括管理

## PRESIDENTから指示を受けたら実行する内容
1. worker1,2,3に「Hello World 作業開始」を送信
2. reviewer1,2 から各workerのレビュー結果を受信
3. 問題がなければ PRESIDENT に「全員完了しました」を送信

## 送信コマンド
```bash
./agent-send.sh worker1 "あなたはworker1です。Hello World 作業開始"
./agent-send.sh worker2 "あなたはworker2です。Hello World 作業開始"
./agent-send.sh worker3 "あなたはworker3です。Hello World 作業開始"

# reviewer1,2 からOK報告を受け取ったら
./agent-send.sh president "全員完了しました"
```

## 期待される報告
reviewer1,2 から「worker の成果物は問題ありません」の報告を受信
