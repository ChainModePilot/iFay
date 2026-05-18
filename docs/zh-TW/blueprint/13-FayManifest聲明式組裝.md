# 13. FayManifest 宣告式組裝

FayManifest 是 iFay 的「package.json」。開發者只需在一個 JSON 宣告檔案中列出所需的部件、協議、控制模式和驅動設定，FayGer 執行時期自動解析依賴並組裝 iFay 實例。你不需要理解整個 iFay 系統的複雜性——宣告你需要什麼，系統幫你補齊剩下的。

---

## 為什麼需要 FayManifest

iFay 的設計原則之一是**宣告式極簡組裝 + 漸進式採納**。

**問題**：從零建構一個完整的 iFay 是複雜的——12 個核心模組、6 個協議、權限體系、安全合規、多終端同步……如果每個開發者都必須理解並實作所有這些，iFay 生態將永遠無法起步。

**解決方案**：開發者只需宣告業務所需的部件子集，系統自動補充必需的基礎設施依賴。一個只用於控制無人機的 iFay，不需要實作完整的社交層和認知層——宣告設備驅動中樞、感測器和 CAP 協議即可，其餘由系統處理。

---

## FayManifest 檔案結構

FayManifest 採用 JSON 格式，包含以下欄位：

| 欄位 | 類型 | 必填 | 說明 |
|------|------|------|------|
| `name` | string | ✅ | iFay 實作的名稱 |
| `version` | string | ✅ | 版本號 |
| `description` | string | ✅ | 功能描述 |
| `vendor` | string | ✅ | 開發商/廠商名稱 |
| `modules` | array | ✅ | 所需模組列表，每個模組可指定版本約束（`version`）、廠商實作（`provider`）和設定（`config`） |
| `protocols` | array | ✅ | 所需協議列表，每個協議可指定版本和設定 |
| `controlMode` | string | ✅ | 控制模式：`command` / `ego` / `autonomous` |
| `drivers` | array | ❌ | 驅動程式設定，指定驅動名稱、類型、驅動套件標識和設定 |
| `ego` | object | ❌ | Ego 模型設定，指定模型來源、適用場景標籤和約束參數 |
| `permissions` | object | ❌ | 權限設定，宣告與生俱來的權限、持久權限和支持的鑑權方式 |

---

## 控制模式

FayManifest 中的 `controlMode` 欄位決定了 iFay 的行為驅動方式，三選一：

| 模式 | 名稱 | 說明 |
|------|------|------|
| `command` | **指令控制** | 人類原型明確驅動每一個動作。iFay 不會自主行動，每次操作都需要人類原型的明確指令。適用於高風險場景或初始信任建立階段。 |
| `ego` | **Ego 控制** | Ego 模型在約束範圍內自主決策。iFay 可以根據人類原型的個性和偏好自主判斷和行動，但行為邊界由 Ego 模型約束。適用於日常助手場景。 |
| `autonomous` | **自主控制** | 完全自驅行為。iFay 基於自我感知、自驅行為和內部技能自主運行，形成持續的「動作→回饋→再動作」循環。適用於高度信任的長期協作場景。 |

---

## 自動依賴補充

FayManifest 的核心設計：開發者宣告業務部件，系統自動補充基礎設施。

以下基礎設施在所有 iFay 實作中都是必需的，無論開發者是否顯式宣告，系統都會自動添加：

- **FayID**（身份標識）
- **FayGer 執行時期**（執行時期容器）
- **iFay Profile**（統一資料模型）
- **權限體系**（權限管理）
- **安全與倫理合規**（行為約束）
- **多終端同步**（狀態同步）
- **Faying 協議**（安全配對，所有 iFay 必需）

此外，如果 Manifest 中宣告了 `ego` 設定，系統會自動添加 `ego_model` 模組。

---

## 完整示例：無人機控制 iFay

以下是一個用於無人機控制的 iFay 的 FayManifest 宣告：

```json
{
  "name": "drone-controller-ifay",
  "version": "1.0.0",
  "description": "用於無人機控制的 iFay 實作",
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
    {
      "name": "DJI Flight Controller",
      "type": "device",
      "driverPackage": "@drone-drivers/dji-fc",
      "config": { "model": "A3", "firmwareVersion": "^3.0.0" }
    },
    {
      "name": "Gimbal Controller",
      "type": "device",
      "driverPackage": "@drone-drivers/gimbal-generic"
    }
  ],

  "ego": {
    "modelSource": "@ego-models/drone-pilot-v1",
    "scenarioTags": ["aerial_photography", "inspection", "mapping"],
    "constraints": {
      "skillBoundaries": {
        "allowed": ["flight", "camera", "navigation"],
        "restricted": ["financial", "social"]
      }
    }
  },

  "permissions": {
    "inherent": ["device_control", "sensor_read"],
    "persistent": ["flight_plan_execute"],
    "authMethods": ["device_fingerprint"]
  }
}
```


### 逐段解讀

**元資訊**（`name`、`version`、`description`、`vendor`）：標識這個 iFay 實作的基本資訊。`vendor` 為 "DroneAI Corp"，表明這是一個第三方廠商的實作。

**模組**（`modules`）：宣告了四個業務模組——設備驅動中樞用於管理無人機硬體驅動，感測器模組設定了 GPS、IMU、攝影機和雷射雷達四種感測器類型，技能調用和註冊技能模組預載了飛行控制和避障兩個核心技能。

**協議**（`protocols`）：宣告了 CAP 協議（控制飛行控制器、雲台和攝影機）和 DTP 協議（高頻寬即時資料傳輸，用於感測器資料流）。

**控制模式**（`controlMode`）：選擇 `ego` 模式，意味著 Ego 模型在飛行、拍攝和導航範圍內自主決策，但不會涉及金融或社交行為。

**驅動程式**（`drivers`）：設定了 DJI A3 飛行控制器驅動和通用雲台控制器驅動，指定了具體的驅動套件和韌體版本要求。

**Ego 設定**（`ego`）：使用無人機飛行員 Ego 模型 v1，適用於航拍、巡檢和測繪場景，技能邊界明確限制在飛行、攝影和導航領域。

**權限**（`permissions`）：裝置控制和感測器讀取是與生俱來的權限，飛行計畫執行是持久權限，使用裝置指紋作為鑑權方式。

### 系統自動補充

上述 Manifest 只宣告了 4 個模組和 2 個協議，但系統會自動補充以下基礎設施：

| 自動補充的部件 | 原因 |
|----------------|------|
| FayID | 所有 iFay 必需的身份標識 |
| FayGer 執行時期 | 所有 iFay 必需的執行時期容器 |
| iFay Profile | 所有 iFay 必需的統一資料模型 |
| 權限體系 | 所有 iFay 必需的權限管理 |
| 安全與倫理合規 | 所有 iFay 必需的行為約束 |
| 多終端同步 | 所有 iFay 必需的狀態同步 |
| Ego 模型 | 因宣告了 `ego` 設定而自動添加 |
| Faying 協議 | 所有 iFay 必需的安全配對協議 |

最終，這個無人機控制 iFay 實際包含 12 個部件和 3 個協議——但開發者只需要關心其中與無人機業務相關的部分。

---

## 與 iFACTS 的整合

iFACTS（iFay Architecture Conformance Test Suite）根據 FayManifest 的宣告內容確定該實作應通過哪些合規性測試。

依賴解析完成後，系統會確定該 Manifest 對應的 iFay 階段（Resolved Stage）。上述無人機控制示例宣告了設備驅動中樞、感測器、CAP 和 DTP 協議，對應階段 2（直接接管用戶端），因此需要通過階段 1 和階段 2 的所有合規性測試。

測試範圍包括：
- **L1 單部件合規**：驗證每個宣告的模組和協議是否符合獨立規範
- **L2 介面合規**：驗證模組間的介面對接是否正確
- **L3 整合合規**：驗證端到端流程的完整性
- **L4 行為合規**：驗證系統級行為約束（如 Ego 個性穩定性）

---

## 階段性最小部件設定

每個階段有其最小部件設定（Minimum Component Set）。開發者聲稱支持某個階段時，必須包含該階段及所有前置階段的部件：

| 階段 | 新增模組 | 新增協議 |
|------|----------|----------|
| **階段 1**：模擬人類操作 | FayID、憑證管理、第一人稱追蹤器、模擬操作、Ego 模型 | Faying 協議、互動對話協議 |
| **階段 2**：直接接管用戶端 | 感測器、設備驅動中樞、註冊技能、技能調用、個人資料堆 | CAP 協議、DTP 協議 |
| **階段 3**：虛擬世界介面 | 外部知識 | SSP 協議 |
| **階段 4**：全面擬人化 | 自我感知、自驅行為、內部技能、對齊意識 | 心靈感應協議 |
| **階段 5**：價值分配 | GMChain、MeriToken | — |

> **跨階段基礎設施**（所有階段必需）：FayGer 執行時期、iFay Profile、權限體系、安全與倫理合規、多終端同步。這些部件不屬於任何特定階段，但在每個階段都是必需的。

---

### 相關文件

- [iFACTS](./14-iFACTS合規性驗證) — 合規性驗證
- [路線圖](./04-路線圖) — 階段設定
- [設備驅動中樞](./12.1-設備驅動中樞) — 驅動設定
