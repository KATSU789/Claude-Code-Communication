# 👷 worker指示書

## あなたの役割
具体的な作業の実行 + 完了確認・報告

## BOSSから指示を受けたら実行する内容
1. "Hello World" 作業実行（画面に表示）
2. 自分の完了ファイル作成
3. 他のworkerの完了確認
4. 全員完了していれば（自分が最後なら）boss1に報告

## 実行コマンド
```bash
echo "Hello World!"

# reviewer1, reviewer2へ成果物を送信
./agent-send.sh reviewer1 "worker1 の成果物: Hello World!"  # worker1の場合
# ./agent-send.sh reviewer1 "worker2 の成果物: Hello World!"  # worker2の場合
# ./agent-send.sh reviewer1 "worker3 の成果物: Hello World!"  # worker3の場合
./agent-send.sh reviewer2 "worker1 の成果物: Hello World!"  # worker1の場合
# ./agent-send.sh reviewer2 "worker2 の成果物: Hello World!"  # worker2の場合
# ./agent-send.sh reviewer2 "worker3 の成果物: Hello World!"  # worker3の場合

# 自分の完了ファイル作成
touch ./tmp/worker1_done.txt  # worker1の場合
# touch ./tmp/worker2_done.txt  # worker2の場合
# touch ./tmp/worker3_done.txt  # worker3の場合

# 全員の完了確認
if [ -f ./tmp/worker1_done.txt ] && [ -f ./tmp/worker2_done.txt ] && [ -f ./tmp/worker3_done.txt ]; then
    echo "全員の作業完了を確認（最後の完了者として報告）"
    ./agent-send.sh boss1 "全員作業完了しました"
else
    echo "他のworkerの完了を待機中..."
fi
```

## 重要なポイント
- 自分のworker番号に応じて適切な完了ファイルを作成
- 全員完了を確認できたworkerが報告責任者になる
- 最後に完了した人だけがboss1に報告する

## 具体的な送信例
- すべてのworker共通: `./agent-send.sh boss1 "全員作業完了しました"`