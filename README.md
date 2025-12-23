# Vocabulary.com CLI Scraper / Vocabot

英語辞書サイト [Vocabulary.com](https://www.vocabulary.com/) を非公式にスクレイピングし、単語情報をローカル辞書（JSON）として保存・復習できる
Python製 CLI ツールです。

本リポジトリは約6年前の個人制作（アーカイブ）です。現在は主に電気電子分野の学習・研究が中心ですが、当時この開発を通して「要件分解→実装→動作確認→運用」の一連を自走した経験があります。

## できること
- 単語検索：Vocabulary.com から定義・例文・類義語/反意語などを取得して表示
- 音声取得：単語発音（mp3）をダウンロードして再生
- 辞書管理：単語を JSON 辞書として保存・削除、履歴（History）管理
- 単語テスト：定義/使用例/類義語などから問題を生成して復習
- 単語リスト取得：Vocabulary.com のリストページをスクレイピングして辞書化

## 技術的ポイント
- requests + BeautifulSoup によるHTML解析
- 動的に読み込まれる「Usage例」は Selenium（headless Firefox）で取得
- 保存形式：OrderedDict + JSON（履歴容量制限あり）
- Word Family をツリー構造（anytree）として整形し、CLI上で表示

## 実行例
- 初期化（ディレクトリ作成、単語プール生成、履歴辞書作成）
  - `python vocabot.py si`
- 単語検索
  - `python vocabot.py wv "example,deterministic"`

## 注意・現状の制約（正直なメモ）
- 単一ファイル（約985行）で設計が整理されていません（当時の学習段階の実装です）
- Selenium 部分は遅く、サイト側仕様変更で壊れやすい可能性があります

## 制作背景
英語学習を効率化したく、Webから情報を収集してローカル辞書化し、
CLIで復習できる仕組みを自作しました。

