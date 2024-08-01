---
theme: seriph
background: https://cover.sli.dev
title: History of Architecture
class: text-center
drawings:
  persist: false
transition: fade
mdc: true
hideInToc: true
lineNumbers: true
---

# History of Architecture

2024/08/01 presentation for 社内勉強会

@kazu_kichi_67

<div class="abs-br m-6 flex gap-2">
  <a href="https://x.com/kazu_kichi_67" target="_blank" alt="X" title="Open in X"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-x />
  </a>
  <a href="https://github.com/kazu-kichi-67" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---
src: ./pages/who-am-i.md
hide: false
---

---
hideInToc: true
---

# Agenda

***

<br>
<Toc maxDepth="2"/>

---
hideInToc: true
---

# はじめに

***

- アーキテクチャの思想を知ることの重要性
  - システムの理解を早める
  - アンチパターンを避ける
  - 保守性、品質、開発効率の向上
  - 上流工程への参画
  - <span v-mark.circle.orange>市場価値の向上</span>
- 2025年の崖
  - 既存システムのレガシーシステム化
    - リプレイス案件の増加が予想される
  - IT人材不足
    - 人が多ければいいってもんじゃない
    - 最新トレンドに沿った、リアーキテクティングのスキルが重要

今、<span v-mark.red>本当に現場で求められているスキル</span>を学びましょう

---
hideInToc: true
---

# 注意点

***

<br>

- 情報量が多いので、この場で全てを理解するのは難しいと思います
- 頻出単語の関連性や、IT業界全体の流れを把握し、<span v-mark.red>今後の勉強の足掛かり</span>にしてほしい

---
layout: section
---

# アーキテクチャーの変遷

---
layout: section
---

## システム全体編

---

### モノリス

***

<div class="grid grid-cols-[30%_70%] gap-4">

<div>
<br>

<img src="/monolith.drawio.svg" />

</div>

<div>

<br>

### メリット

<v-click>

- 1つのアプリケーションのため、デプロイが容易
- スタートアップであれば、これで十分な場合も多い

</v-click>

<br>

### デメリット

<v-click>

- アプリケーションが多くなればなるほど複雑化しやすい（Big Ball of Mat: 大きな泥団子）
  - 修正に対する影響範囲が広く、開発スピードが低下する
  - 影響範囲の特定すら難しく、サービス品質が低下する
- 機能毎にスケールすることが出来ない（弾力性×）
- 1つのアプリケーションがダウンすると、そのままサービス停止へ（耐障害性×）

</v-click>

</div>
</div>

---

### マイクロサービス

***

<div class="grid grid-cols-[30%_70%] gap-4">

<div>
<br>

<img src="/microService.drawio.svg" />

</div>

<div>

<br>

### メリット

<v-click>

- 機能毎に疎結合となり、互いに修正の影響を受けづらい
- 機能単位でのデプロイ、スケーリングが可能
- 障害の影響を最小限にできる
- コンテナ環境と相性が良い

</v-click>

<br>

### デメリット

<v-click>

- デプロイ、サービス管理のコストが高い
- マイクロサービス間通信によるオーバーヘッド
- 解析時に流れを追うのが難しい
- トランザクションを貼れないため、データの一貫性を担保しづらい
  - sagaパターン
- マイクロサービス間の境界を見極めるのが難しい

</v-click>

</div>
</div>

---

### モジュラモノリス

***

<div class="grid grid-cols-[30%_70%] gap-4">

<div>
<br>

<img src="/modularMonolith.drawio.svg" />

</div>

<div>

<br>

マイクロサービスのデメリットを緩和できる

### メリット

<v-click>

- デプロイ、サービス管理のコストが低め
- モジュール間のやり取りでオーバーヘッドが少ない
- オーケストレーター層を置いてトランザクション管理することも可能
- モジュール間の境界を見誤っても、リカバリしやすい

</v-click>

<br>

### デメリット

<v-click>

- マイクロサービスほど自由にスケール出来ない
- モジュール境界の管理をしっかりやらないと、モノリスと変わらなくなる

</v-click>

<v-click>

マイクロサービスとモジュラモノリスのハイブリットもおすすめ。
組織のスケールに合わせて少しずつマイクロサービスへ移行する！

</v-click>

</div>
</div>

---
layout: section
---

## フロントエンド編

---

### MVC

***

<div class="grid grid-cols-[30%_70%] gap-4">

<div>
<br>

<img src="/MVC.drawio.svg" />

</div>

<div>

<br>

- Classic MVC、MVC 2とか存在する
- Controllerが入力を受け付けて、Model-Viewの橋渡しを行う
- Struts、Spring MVC、Laravel、CakePHP、FuelPHP、Ruby on Rails

<br>

### メリット

<v-click>

- View（画面のレイアウト）とModel(ビジネスロジックやデータ管理)を分離できる
- 同じModelでViewだけ切り替えることが可能

</v-click>

<br>

### デメリット

<v-click>

- 大規模アプリケーションでは、Controllerが肥大化しやすい
- ViewとModelの結合度が高くなりがち

</v-click>

</div>
</div>

---

### MVP

***

<div class="grid grid-cols-[30%_70%] gap-4">

<div>
<br>

<img src="/MVP.drawio.svg" />

</div>

<div>

<br>

- PresenterがModelとViewの仲介を行う

<br>

### メリット

<v-click>

- Presenterがイベントハンドリングを担う
 - ViewがModelの変更を監視する(Observe)パターン
 - パッシブビュー(Passive View)
- パッシブビューによって完全にViewと分離できるので、よりテストがしやすい

</v-click>

<br>

### デメリット

<v-click>

- Presenterが肥大化しやすい
- ViewとPresenterの1対1の関係が必要で、柔軟性に欠ける場合がある

</v-click>

</div>
</div>

---

### MVVM

***

<div class="grid grid-cols-[30%_70%] gap-4">

<div>
<br>

<img src="/MVVM.drawio.svg" />

</div>

<div>

<br>

- データバインディング
  - React.js: 単方向バインディング、Vue.ja: 双方向バインディング

<br>

### メリット

<v-click>

- MVPとそこまで変わらないが、ViewとViewModelの連携をフレームワークが担ってくれる

</v-click>

<br>

### デメリット

<v-click>

- 最初の学習コストが高い

</v-click>

</div>
</div>

---
layout: section
---

## バックエンド編

---

### レイヤードアーキテクチャ

***

<div class="grid grid-cols-[30%_70%] gap-4">

<div>
<br>

```mermaid
flowchart LR
    subgraph "レイヤードアーキテクチャ"
    direction TB
    A["プレゼンテーション（インターフェース）層"]
    B["ユースケース(アプリケーション)層"]
    C["ドメイン(ビジネスロジック)層"]
    D["インフラストラクチャー（データアクセス）層"]
    
    A --> B
    B --> C
    C --> D
    end

    style A fill:#FFA500,stroke:#000,stroke-width:2px,color:#000
    style B fill:#FFFF00,stroke:#000,stroke-width:2px,color:#000
    style C fill:#ADD8E6,stroke:#000,stroke-width:2px,color:#000
    style D fill:#90EE90,stroke:#000,stroke-width:2px,color:#000
```

※ 矢印は依存の向き

※ 3層の場合もある（層の数に決まりはない）

</div>

<div>

<br>

### メリット

<v-click>

- 各層に特定の役割（責務）を与えることで、コードの見通しが良くなる（単一責任の原則 SRP）
- 上層の変更に対して、下層が影響を受けない
  - 使い回しが出来る

</v-click>

<br>

### デメリット

<v-click>

- 下層の変更によって、上層が影響を受ける
- つまり、インフラストラクチャーを変更すると、ビジネスロジックが影響を受けてしまう

</v-click>

</div>
</div>

---

### ヘキサゴナルアーキテクチャ

***

<div class="grid grid-cols-[30%_70%] gap-4">

<div>
<br>

<img src="/HexagonalArchitecture.drawio.svg" />

<br>

```mermaid
flowchart LR
    subgraph "依存性逆転の原則(DIP)"
    direction TB
    A["プレゼンテーション層"]
    B["ユースケース層"]
    C["ドメイン層"]
    D["インフラストラクチャー層"]
    
    A --> B
    B --> C
    D --> C
    end

    style A fill:#FFA500,stroke:#000,stroke-width:2px,color:#000
    style B fill:#FFFF00,stroke:#000,stroke-width:2px,color:#000
    style C fill:#ADD8E6,stroke:#000,stroke-width:2px,color:#000
    style D fill:#90EE90,stroke:#000,stroke-width:2px,color:#000
```

</div>

<div>

<br>

- 別名、Ports and Adapters

<br>

### メリット

<v-click>

- Port層によってApplicationが守られているので、外部の変更に対して強い
- Application（ビジネスロジック）の独立性が高く、テストが容易

</v-click>

<br>

### デメリット

<v-click>

- 初期の設計が複雑になりがち
- 小規模なシステムだと過剰な設計になりうる

</v-click>

</div>
</div>

---

### オニオンアーキテクチャ

***

<div class="grid grid-cols-[30%_70%] gap-4">

<div>
<br>

<img src="/OnionArchitecture.svg" />

</div>

<div>

<br>

- ドメインを中心にして設計される
- 外から中への依存

<br>

### メリット

<v-click>

- ドメインが何にも依存せず、外側の影響を受けない
- テストが容易
- ビジネスロジックの再利用性が高い

</v-click>

<br>

### デメリット

<v-click>

- 小規模なシステムには不向き

</v-click>

</div>
</div>

---

### クリーンアーキテクチャ

***

<div class="grid grid-cols-[30%_70%] gap-4">

<div>
<br>
<br>

<img src="/CleanArchitecture.jpg" />

</div>

<div>

<br>

- ドメイン（エンティティ）を中心にして設計される
- 外から中への依存

<br>

### メリット

<v-click>

- テストが容易
- フレームワークやデータベースの変更に強い
- ビジネスロジックの明確な分離

</v-click>

<br>

### デメリット

<v-click>

- 小規模なシステムだと、作るものが多く冗長になりうる
- 初期の学習コストが最も高い

</v-click>

</div>
</div>

---

### ドメイン駆動設計（DDD）

***

<br>

- 戦術的DDD
  - 実装パターンやレイヤー設計のパターン
  - Repository、Domain Service、Value Object、Entityなど
  - こちらのみ：軽量DDD

- <span v-mark.circle.orange>戦略的DDD</span>
  - ドメイン（システムにおける本質的に重要な部分、ビジネスロジック）をモデリングする手法
  - ユビキタス言語、境界づけられたコンテキスト、ドメインエキスパート、サブドメインなど
  - 手法：イベントストーミング、ユースケース分析、ドメインストーリーテリングなど

---
layout: section
---

# トレンド

---
layout: section
---

## CQRS

---

### CQRS

***

<div class="grid grid-cols-[30%_70%] gap-4">

<div>
<br>

<img src="/CQRS.drawio.svg" />

</div>

<div>

<br>

- Command Query Responsibility Segregation: コマンド・クエリ責務分離
- 複数の集約単位を跨るようなリードモデルが欲しくなる
  - 一覧画面のようなもの、N+1問題

### メリット

<v-click>

- ドメインモデルの最適化
- 更新系（NoSQL）と参照系（RDB）それぞれスケーリングが可能

</v-click>

### デメリット

<v-click>

- データ整合性の管理
  - 結果整合性を受け入れられるか
- システムが増えるにつれ、管理コストも増加
  - NewSQLの利用: Cloud Spanner、TiDB、CockroachDB
- コマンドとクエリの2つのモデル開発、テスト
  - GraphQL等の活用、自動化

</v-click>

</div>
</div>

---
layout: section
---

## Event Scourcing

---

### Event Scourcing

***

<div class="grid grid-cols-[30%_70%] gap-4">

<div>
<br>

<img src="/ES.drawio.svg" />

</div>

<div>

<br>

- CQRSとはセットで語られることがほとんど
- Axon, Kafka、Amazon Kinesis、SQS、Akkaなど

### メリット

<v-click>

- 耐障害性
- 弾力性
- リトライ、履歴、ロールバック、キャッシュ、流量制限等の責務を移譲
  - 高凝縮・疎結合

</v-click>

### デメリット

<v-click>

- システムの複雑化、非同期通信による設計難易度
  - 結果のポーリングや、冪等性の担保など
- 障害時に追いづらい
  - オブザーバビリティが重要
  - OpenTelemetry、Prometheus、Datadog、New Relic、Dynatraceなど

</v-click>

</div>
</div>

---

### 参考文献

***

<br>

- [SOLID原則](https://www.alpha.co.jp/blog/202302_01/)
- [リアクティブ宣言](https://www.reactivemanifesto.org/)
- [CQRSパターン](https://learn.microsoft.com/ja-jp/azure/architecture/patterns/cqrs)
- [イベントソーシングパターン](https://learn.microsoft.com/ja-jp/azure/architecture/patterns/event-sourcing)
- [アーキテクチャ特集](https://findy-tools.io/articles)

---
layout: center
class: text-center
hideInToc: true
---

# End

良いエンジニアライフを！

<PoweredBySlidev mt-10 />
