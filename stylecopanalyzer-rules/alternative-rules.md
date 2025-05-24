# 代替ルール (SX-)

代替ルールは、StyleCopの標準的な動作とは異なる代替スタイルを提供するためのルールです。これらのルールは通常、StyleCopの標準ルールと直接矛盾するため、同時に使用することはできません。

## ルール一覧

| ルールID | 名前 | 説明 |
|---------|------|------|
| [SX1101](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SX1101.md) | DoNotPrefixLocalMembersWithThis | ローカルクラスのメンバーに `this.` プレフィックスを使用すべきではありません。 |
| [SX1309](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SX1309.md) | FieldNamesMustBeginWithUnderscore | フィールド名はアンダースコアで始まる必要があります。（SA1309の代替） |
| [SX1309S](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SX1309S.md) | StaticFieldNamesMustBeginWithUnderscore | 静的フィールド名はアンダースコアで始まる必要があります。 |

## 設定方法

### 標準ルールと代替ルールの切り替え

代替ルールを使用する場合は、対応する標準ルールを無効にする必要があります。以下に一般的な例を示します：

#### `this` キーワードの使用（SX1101 vs SA1101）

```editorconfig
# thisキーワードを要求する（標準ルール）
dotnet_diagnostic.SA1101.severity = warning
dotnet_diagnostic.SX1101.severity = none

# または、thisキーワードを禁止する（代替ルール）
dotnet_diagnostic.SA1101.severity = none
dotnet_diagnostic.SX1101.severity = warning
```

#### フィールド名のアンダースコアプレフィックス（SX1309 vs SA1309）

```editorconfig
# アンダースコアプレフィックスを禁止する（標準ルール）
dotnet_diagnostic.SA1309.severity = warning
dotnet_diagnostic.SX1309.severity = none

# または、アンダースコアプレフィックスを要求する（代替ルール）
dotnet_diagnostic.SA1309.severity = none
dotnet_diagnostic.SX1309.severity = warning
```

### 一般的なカスタマイズ例

#### アンダースコアプレフィックスの適用対象

SX1309（非静的フィールド）とSX1309S（静的フィールド）を個別に設定することで、どのタイプのフィールドにアンダースコアプレフィックスを適用するかをカスタマイズできます：

```editorconfig
# 標準ルールを無効化
dotnet_diagnostic.SA1309.severity = none

# 非静的フィールドにアンダースコアプレフィックスを要求
dotnet_diagnostic.SX1309.severity = warning

# 静的フィールドにはアンダースコアプレフィックスを要求しない
dotnet_diagnostic.SX1309S.severity = none
```

## 違反の抑制方法

特定の代替ルール違反を抑制するには、以下の方法があります：

1. コード内での抑制：

   ```csharp
   [SuppressMessage("StyleCop.CSharp.NamingRules", "SX1309:FieldNamesMustBeginWithUnderscore", Justification = "このケースではアンダースコアプレフィックスを使用しません。")]
   private string myField;
   ```

2. グローバルな抑制：

   ```csharp
   [assembly: SuppressMessage("StyleCop.CSharp.NamingRules", "SX1309:FieldNamesMustBeginWithUnderscore", Justification = "このプロジェクトではアンダースコアプレフィックスを使用しません。")]
   ```

3. プラグマディレクティブ：

   ```csharp
   #pragma warning disable SX1309 // フィールド名はアンダースコアで始める必要があります
   private string myField;
   #pragma warning restore SX1309 // フィールド名はアンダースコアで始める必要があります
   ```

## ベストプラクティスとガイドライン

1. **チーム全体での一貫性**: 標準ルールと代替ルールのどちらかを選択する場合は、チーム全体で一貫して使用することが重要です。

2. **既存のコードベースとの互換性**: 既存のコードベースが特定のスタイルに従っている場合は、それに合わせたルールを選択すると移行が容易になります。

3. **他のツールとの互換性**: 使用するIDEやコードジェネレーターが特定のスタイルに合わせて設定されている場合は、それに合わせたルールを選択することを検討してください。

4. **プロジェクトごとの一貫性**: 異なるプロジェクトで異なるスタイルを採用する場合でも、各プロジェクト内では一貫したスタイルを維持することが重要です。
