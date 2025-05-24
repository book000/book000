# 命名規則 (SA1300-)

命名規則は、変数、型、メンバー、その他のコード要素の命名規則を定義します。これらのルールは、コードベース全体で一貫した命名規則を維持するために役立ちます。

## ルール一覧

| ルールID | 名前 | 説明 |
|---------|------|------|
| [SA1300](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1300.md) | ElementMustBeginWithUpperCaseLetter | C#の要素は大文字で始まる必要があります。 |
| [SA1301](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1301.md) | ElementMustBeginWithLowerCaseLetter | このルールは現在使用されていません。 |
| [SA1302](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1302.md) | InterfaceNamesMustBeginWithI | インターフェース名は「I」で始まる必要があります。 |
| [SA1303](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1303.md) | ConstFieldNamesMustBeginWithUpperCaseLetter | 定数フィールド名は大文字で始まる必要があります。 |
| [SA1304](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1304.md) | NonPrivateReadonlyFieldsMustBeginWithUpperCaseLetter | 非プライベートの読み取り専用フィールドは大文字で始まる必要があります。 |
| [SA1305](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1305.md) | FieldNamesMustNotUseHungarianNotation | フィールド名にハンガリアン表記法を使用してはいけません。 |
| [SA1306](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1306.md) | FieldNamesMustBeginWithLowerCaseLetter | フィールド名は小文字で始まる必要があります。 |
| [SA1307](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1307.md) | AccessibleFieldsMustBeginWithUpperCaseLetter | アクセス可能なフィールド名は大文字で始まる必要があります。 |
| [SA1308](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1308.md) | VariableNamesMustNotBePrefixed | 変数名にはプレフィックスを付けるべきではありません。 |
| [SA1309](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1309.md) | FieldNamesMustNotBeginWithUnderscore | フィールド名はアンダースコアで始めるべきではありません。 |
| [SA1310](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1310.md) | FieldNamesMustNotContainUnderscore | フィールド名にアンダースコアを含めるべきではありません。 |
| [SA1311](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1311.md) | StaticReadonlyFieldsMustBeginWithUpperCaseLetter | 静的な読み取り専用フィールドは大文字で始まる必要があります。 |
| [SA1312](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1312.md) | VariableNamesMustBeginWithLowerCaseLetter | 変数名は小文字で始まる必要があります。 |
| [SA1313](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1313.md) | ParameterNamesMustBeginWithLowerCaseLetter | パラメーター名は小文字で始まる必要があります。 |
| [SA1314](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1314.md) | TypeParameterNamesMustBeginWithT | タイプパラメーター名は「T」で始まる必要があります。 |
| [SX1309](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SX1309.md) | FieldNamesMustBeginWithUnderscore | フィールド名はアンダースコアで始まる必要があります。（SA1309の代替ルール） |
| [SX1309S](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SX1309S.md) | StaticFieldNamesMustBeginWithUnderscore | 静的フィールド名はアンダースコアで始まる必要があります。 |

## 設定方法

### stylecop.json の設定

命名規則の多くは `stylecop.json` ファイルでカスタマイズすることができません。代わりに、ルールセットファイルでルールの有効/無効や重大度を設定します。

### ルールの有効化/無効化

命名規則を有効または無効にするには、`.editorconfig` ファイルや Visual Studio のルールセットファイルを使用します。

`.editorconfig` ファイルの例：

```editorconfig
# 全てのフィールド名にアンダースコアのプレフィックスを許可する（SA1309を無効化）
dotnet_diagnostic.SA1309.severity = none

# 代わりにSX1309を有効化
dotnet_diagnostic.SX1309.severity = warning
```

### 一般的なカスタマイズ例

#### アンダースコアのプレフィックス

SA1309（アンダースコアのプレフィックスを禁止）とSX1309（アンダースコアのプレフィックスを要求）は相反するルールです。プロジェクトの規約に合わせていずれかを選択します：

```editorconfig
# アンダースコアプレフィックスを禁止
dotnet_diagnostic.SA1309.severity = warning
dotnet_diagnostic.SX1309.severity = none

# または、アンダースコアプレフィックスを要求
dotnet_diagnostic.SA1309.severity = none
dotnet_diagnostic.SX1309.severity = warning
```

#### ハンガリアン表記法

SA1305（ハンガリアン表記法の禁止）はハンガリアン表記法を検出しようとしますが、誤検出が多いため、無効にすることも検討できます：

```editorconfig
# ハンガリアン表記法のチェックを無効化
dotnet_diagnostic.SA1305.severity = none
```

## 違反の抑制方法

特定の命名規則違反を抑制するには、以下の方法があります：

1. コード内での抑制：

   ```csharp
   [SuppressMessage("StyleCop.CSharp.NamingRules", "SA1309:FieldNamesMustNotBeginWithUnderscore", Justification = "私たちのコーディング規約ではプライベートフィールドにアンダースコアプレフィックスを使用します。")]
   private string _myField;
   ```

2. グローバルな抑制：

   ```csharp
   [assembly: SuppressMessage("StyleCop.CSharp.NamingRules", "SA1309:FieldNamesMustNotBeginWithUnderscore", Justification = "私たちのコーディング規約ではプライベートフィールドにアンダースコアプレフィックスを使用します。")]
   ```

3. プラグマディレクティブ：

   ```csharp
   #pragma warning disable SA1309 // フィールド名はアンダースコアで始めるべきではありません
   private string _myField;
   #pragma warning restore SA1309 // フィールド名はアンダースコアで始めるべきではありません
   ```

4. `.editorconfig` ファイルでのカスタマイズ（上述の通り）
