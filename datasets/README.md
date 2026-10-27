# Image datasets

画像の分類単位は `gNN`。生成画像そのものと、比較条件を混ぜない。

```text
datasets/
├── README.md
├── manifest.example.jsonl
├── g00_shishi/
│   └── shishi.png
└── g01_girl/
    ├── lora/
    │   └── seed-000042.png
    └── no_lora/
        └── seed-000042.png
```

## Groups

- **g00_shishi** — シシ。LoRAの学習対象・生成結果の単体確認用。実際の画像ファイル名は manifest に記録する。
- **g01_girl/lora** — 少女を含むプロンプトで LoRA を適用した画像。
- **g01_girl/no_lora** — 同じプロンプト・seed・生成設定で LoRA を適用せずに生成した対照画像。

## Pairing rules

- LoRAあり／なしは同一の `experiment_id` で対にする。
- 可能な限り prompt、seed、解像度、steps、CFG を一致させる。
- `manifest.example.jsonl` をコピーして、実ファイルに合わせて記録する。
- 生成画像はバイナリなので、この Git リポジトリには原則として置かず、Kaggle Dataset 側に保存する。このツリーは構成・スキーマの見本。
