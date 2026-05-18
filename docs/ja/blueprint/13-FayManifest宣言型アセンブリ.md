# 13. FayManifest 宣言型アセンブリ

FayManifestはiFayの「package.json」である。開発者は1つのJSON宣言ファイルに必要な部品、プロトコル、制御モード、ドライバー設定を列挙するだけで、FayGerランタイムが自動的に依存関係を解析しiFayインスタンスを組み立てる。iFayシステム全体の複雑さを理解する必要はない——必要なものを宣言すれば、システムが残りを補完する。

---

## なぜFayManifestが必要か

iFayの設計原則の一つは**宣言型ミニマルアセンブリ＋漸進的採用**である。

**問題**：完全なiFayをゼロから構築するのは複雑——12のコアモジュール、6つのプロトコル、権限体系、セキュリティコンプライアンス、マルチ端末同期……すべての開発者がこれらすべてを理解し実装しなければならないなら、iFayエコシステムは永遠に立ち上がらない。

**解決策**：開発者はビジネスに必要な部品のサブセットを宣言するだけで、システムが必須のインフラ依存関係を自動補完する。

---

## FayManifestファイル構造

| フィールド | タイプ | 必須 | 説明 |
|------|------|------|------|
| `name` | string | ✅ | iFay実装の名称 |
| `version` | string | ✅ | バージョン番号 |
| `description` | string | ✅ | 機能説明 |
| `vendor` | string | ✅ | 開発元/ベンダー名 |
| `modules` | array | ✅ | 必要なモジュールリスト |
| `protocols` | array | ✅ | 必要なプロトコルリスト |
| `controlMode` | string | ✅ | 制御モード：`command` / `ego` / `autonomous` |
| `drivers` | array | ❌ | ドライバー設定 |
| `ego` | object | ❌ | Egoモデル設定 |
| `permissions` | object | ❌ | 権限設定 |

---

## 制御モード

| モード | 名称 | 説明 |
|------|------|------|
| `command` | **指令制御** | ヒューマンプライム（Human Prime）がすべてのアクションを明示的に駆動。高リスクシナリオや初期信頼構築段階に適用。 |
| `ego` | **Ego制御** | Egoモデルが制約範囲内で自律的に意思決定。日常アシスタントシナリオに適用。 |
| `autonomous` | **自律制御** | 完全な自律行動。高度な信頼の長期協力シナリオに適用。 |

---

## 自動依存関係補完

以下のインフラはすべてのiFay実装で必須であり、開発者が明示的に宣言するかどうかに関わらずシステムが自動追加する：

- **FayID**（身分識別）
- **FayGerランタイム**（ランタイムコンテナ）
- **iFay Profile**（統一データモデル）
- **権限体系**（権限管理）
- **セキュリティ・倫理コンプライアンス**（行動制約）
- **マルチ端末同期**（状態同期）
- **Fayingプロトコル**（安全ペアリング）

---

## 完全な例：無人機制御iFay

```json
{
  "name": "drone-controller-ifay",
  "version": "1.0.0",
  "description": "無人機制御用のiFay実装",
  "vendor": "DroneAI Corp",
  "modules": [
    { "id": "device_driver_hub", "version": "^1.0.0" },
    { "id": "sensor", "config": { "types": ["gps", "imu", "camera", "lidar"] } },
    { "id": "invoke_skill", "version": "^1.0.0" },
    { "id": "registered_skill", "config": { "preload": ["flight_control", "obstacle_avoidance"] } }
  ],
  "protocols": [
    { "id": "cap_protocol", "config": { "targets": ["flight_controller", "gimbal", "camera"] } },
    { "id": "dtp_protocol", "config": { "bandwidth": "high", "realtime": true } }
  ],
  "controlMode": "ego",
  "drivers": [
    { "name": "DJI Flight Controller", "type": "device", "driverPackage": "@drone-drivers/dji-fc", "config": { "model": "A3", "firmwareVersion": "^3.0.0" } },
    { "name": "Gimbal Controller", "type": "device", "driverPackage": "@drone-drivers/gimbal-generic" }
  ],
  "ego": {
    "modelSource": "@ego-models/drone-pilot-v1",
    "scenarioTags": ["aerial_photography", "inspection", "mapping"],
    "constraints": { "skillBoundaries": { "allowed": ["flight", "camera", "navigation"], "restricted": ["financial", "social"] } }
  },
  "permissions": {
    "inherent": ["device_control", "sensor_read"],
    "persistent": ["flight_plan_execute"],
    "authMethods": ["device_fingerprint"]
  }
}
```

---

## iFACTSとの統合

iFACTS（iFay Architecture Conformance Test Suite）はFayManifestの宣言内容に基づき、その実装が通過すべきコンプライアンステストを決定する。

テスト範囲：
- **L1 単部品コンプライアンス**：各宣言モジュールとプロトコルが独立仕様に適合するか検証
- **L2 インターフェースコンプライアンス**：モジュール間のインターフェース対接が正しいか検証
- **L3 統合コンプライアンス**：エンドツーエンドフローの完全性を検証
- **L4 行動コンプライアンス**：システムレベルの行動制約を検証

---

## フェーズ別最小部品構成

| フェーズ | 新規モジュール | 新規プロトコル |
|------|----------|----------|
| **フェーズ1**：人間操作のシミュレーション | FayID、クレデンシャル管理、一人称トレーサー、シミュレーテッドオペレーション、Egoモデル | Fayingプロトコル、インタラクティブ会話プロトコル |
| **フェーズ2**：クライアントの直接接管 | センサー、デバイスドライバーハブ、登録スキル、スキル呼び出し、パーソナルデータヒープ | CAP（Control Authority Protocol）、DTP（Data Tunnel Protocol） |
| **フェーズ3**：仮想世界のインターフェース | 外部知識 | SSP（Skill Sharing Protocol） |
| **フェーズ4**：完全な擬人化 | セルフアウェアネス、自律行動、内部スキル、アラインド意識 | テレパシープロトコル |
| **フェーズ5**：価値分配 | GMChain、MeriToken | — |

> **クロスフェーズインフラ**（全フェーズ必須）：FayGerランタイム、iFay Profile、権限体系、セキュリティ・倫理コンプライアンス、マルチ端末同期。

---

### 関連ドキュメント

- [iFACTS](./14-iFACTSコンプライアンス検証) — コンプライアンス検証
- [ロードマップ](./04-ロードマップ) — フェーズ構成
- [デバイスドライバーハブ](./12.1-デバイスドライバーハブ) — ドライバー設定