# ADR 0004: DDDライクなレイヤーアーキテクチャの採用

## ステータス
承認済み

## コンテキスト
このプロジェクトはドメイン設計を人間が担い、実装をAIに委ねる戦略を取る。
AIが設計意図を正確に反映したコードを生成するために、明確な構造が必要だった。

## 決定
DDDを参考にした4層アーキテクチャを採用する。

```
presentation/   # Controller, View
application/    # UseCase
domain/         # Entity, ValueObject, Repository（interface）, DomainService
infrastructure/ # Repository（impl）, Scheduler
```

## 理由
- ドメインロジックをinfrastructureから分離することで、テストが容易になる
- 各層の責務が明確なため、AIへの実装指示が具体的に書ける
- リポジトリをinterfaceとして定義することで、本番（JPA）とテスト（H2）の切り替えが容易

## 結果
- パッケージ構成はクラス図（`docs/design/class-diagram.md`）に従う
- ドメイン層はSpring等のフレームワークに依存しない純粋なJavaクラスとする
