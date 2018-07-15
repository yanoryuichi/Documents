# ステージングを取り消す（INDEXを戻す）

### あるファイルのステージングを取り消す

```bash
vi test.txt               # (1) test.txtを修正する
git add test.txt          # (2) test.txtをステージングする
git reset HEAD test.txt   # (3) 上のステージングを取り消す（INDEXをHEADに戻す）
                          #     test.txtは修正されたまま（INDEXがHEADに戻っただけで、ワーキングツリーはそのまま）
```

- git reset HEAD の代わりに git reset --mixed HEAD と省略せずに指定してもいい

### 修正したファイル戻す

```bash
git checkout test.txt      # test.txtは(1)で修正される前の状態に戻った。
```
