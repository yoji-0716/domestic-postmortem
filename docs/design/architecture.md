# アーキテクチャ

## レイヤー構成（DDDライク）

```
presentation/   # Controller, View (Thymeleaf)
application/    # UseCase, ApplicationService
domain/         # Entity, ValueObject, Repository (interface), DomainService
infrastructure/ # Repository (impl), Scheduler, DB設定
```

## パッケージ構成

```
com.example.domesticpostmortem/
├── presentation/
│   └── controller/
├── application/
│   └── usecase/
├── domain/
│   ├── model/
│   ├── repository/
│   └── service/
└── infrastructure/
    ├── repository/
    └── scheduler/
```

## 週次実績の自動生成

- `infrastructure/scheduler/` にSpring `@Scheduled` を用いたバッチジョブを配置
- 毎週月曜日の深夜に前週の `weekly_summary` と `load_balance` を自動生成する

## 技術スタック

| 役割 | 技術 |
|------|------|
| フレームワーク | Spring Boot 3.3.5 |
| ビュー | Thymeleaf |
| ORM | Spring Data JPA |
| DB（本番） | PostgreSQL |
| DB（テスト） | H2 |
| Java | 21 |
