# 保守性ルール (SA1400-)

保守性ルールは、コードの長期的な保守性と品質を確保するためのルールを定義します。これらのルールは、アクセス修飾子の明示的な宣言、コードの冗長性の排除、コードスタイルの一貫性などに焦点を当てています。

## ルール一覧

| ルールID | 名前 | 説明 |
|---------|------|------|
| [SA1400](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1400.md) | AccessModifierMustBeDeclared | アクセス修飾子を明示的に宣言する必要があります。 |
| [SA1401](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1401.md) | FieldsMustBePrivate | フィールドはプライベートでなければなりません。 |
| [SA1402](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1402.md) | FileMayOnlyContainASingleType | ファイルには単一の型のみを含めることができます。 |
| [SA1403](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1403.md) | FileMayOnlyContainASingleNamespace | ファイルには単一の名前空間のみを含めることができます。 |
| [SA1404](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1404.md) | CodeAnalysisSuppressionMustHaveJustification | コード分析の抑制には正当な理由が必要です。 |
| [SA1405](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1405.md) | DebugAssertMustProvideMessageText | Debug.Assert にはメッセージテキストを提供する必要があります。 |
| [SA1406](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1406.md) | DebugFailMustProvideMessageText | Debug.Fail にはメッセージテキストを提供する必要があります。 |
| [SA1407](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1407.md) | ArithmeticExpressionsMustDeclarePrecedence | 算術式は優先順位を明示的に宣言する必要があります。 |
| [SA1408](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1408.md) | ConditionalExpressionsMustDeclarePrecedence | 条件式は優先順位を明示的に宣言する必要があります。 |
| [SA1409](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1409.md) | RemoveUnnecessaryCode | 不必要なコードを削除する必要があります。 |
| [SA1410](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1410.md) | RemoveDelegateParenthesisWhenPossible | 可能な場合はデリゲートの括弧を削除する必要があります。 |
| [SA1411](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1411.md) | AttributeConstructorMustNotUseUnnecessaryParenthesis | 属性コンストラクタは不必要な括弧を使用すべきではありません。 |
| [SA1412](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1412.md) | StoreFilesAsUtf8 | ファイルはUTF-8として保存する必要があります。 |
| [SA1413](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1413.md) | UseTrailingCommasInMultiLineInitializers | 複数行の初期化子では末尾のカンマを使用する必要があります。 |
| [SA1414](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1414.md) | TupleTypesInSignaturesShouldHaveElementNames | シグネチャ内のタプル型には要素名が必要です。 |

## 設定方法

### stylecop.json の設定

保守性ルールの一部は `stylecop.json` でカスタマイズできます：

```json
{
  "$schema": "https://raw.githubusercontent.com/DotNetAnalyzers/StyleCopAnalyzers/master/StyleCop.Analyzers/StyleCop.Analyzers/Settings/stylecop.schema.json",
  "settings": {
    "maintainabilityRules": {
      "topLevelTypes": ["class", "interface", "struct", "enum"]
    }
  }
}
```

主要な設定オプション：

- `topLevelTypes`: SA1402のルールで1ファイルに複数定義を許可する型のリスト（デフォルトは空で、すべての型が1つのファイルに1つだけ許可されます）

### ルールの有効化/無効化

保守性ルールを有効または無効にするには、`.editorconfig` ファイルを使用します：

```editorconfig
# 1ファイルに複数の型を許可する
dotnet_diagnostic.SA1402.severity = none

# フィールドのアクセス修飾子に関するルールを警告として設定
dotnet_diagnostic.SA1401.severity = warning
```

### 一般的なカスタマイズ例

#### 1ファイルに複数の型を許可する

小さな関連する型を1つのファイルにまとめたい場合：

```json
{
  "settings": {
    "maintainabilityRules": {
      "topLevelTypes": ["class", "interface", "struct", "enum", "delegate"]
    }
  }
}
```

または特定のルールを無効化：

```editorconfig
# 1ファイルに複数の型を許可
dotnet_diagnostic.SA1402.severity = none
```

#### アクセス修飾子の要求レベル

アクセス修飾子に関するルールをカスタマイズ：

```editorconfig
# アクセス修飾子を必須とする
dotnet_diagnostic.SA1400.severity = warning

# パブリックフィールドを許可する
dotnet_diagnostic.SA1401.severity = none
```

## 違反の抑制方法

特定の保守性ルール違反を抑制するには、以下の方法があります：

1. コード内での抑制：

   ```csharp
   [SuppressMessage("StyleCop.CSharp.MaintainabilityRules", "SA1401:FieldsMustBePrivate", Justification = "このクラスでは設計上パブリックフィールドが必要です")]
   public class MyClass
   {
       public int PublicField; // 通常はプロパティを使用すべき
   }
   ```

2. グローバルな抑制：

   ```csharp
   [assembly: SuppressMessage("StyleCop.CSharp.MaintainabilityRules", "SA1402:FileMayOnlyContainASingleType", Justification = "小さな関連するクラスをグループ化しています")]
   ```

3. プラグマディレクティブ：

   ```csharp
   #pragma warning disable SA1407 // 算術式は優先順位を明示的に宣言する必要があります
   int result = a + b * c;  // 括弧がないと優先順位が不明確
   #pragma warning restore SA1407 // 算術式は優先順位を明示的に宣言する必要があります
   ```

4. `.editorconfig` ファイルでのカスタマイズ（上述の通り）

## ベストプラクティス

保守性ルールに関するいくつかのベストプラクティス：

### 1. アクセス修飾子の明示的な宣言

C#ではデフォルトのアクセスレベルがあいまいになる可能性があるため、常に明示的なアクセス修飾子を使用することをお勧めします：

```csharp
// 良い例
public class MyClass
{
    private int _myField;
    protected virtual void MyMethod() { }
}

// 悪い例
class MyClass
{
    int _myField;
    virtual void MyMethod() { }
}
```

### 2. 適切なフィールドのカプセル化

データのカプセル化を維持するために、フィールドはプライベートにし、必要に応じてプロパティを通じてアクセスを提供します：

```csharp
// 良い例
public class Person
{
    private string _name;
    public string Name 
    { 
        get => _name; 
        set => _name = value; 
    }
}

// 悪い例
public class Person
{
    public string Name;  // 直接アクセス可能なパブリックフィールド
}
```

### 3. 式の明確性

括弧を使用して、複雑な式の意図を明確にします：

```csharp
// 良い例
int result = a + (b * c);  // 乗算が先に行われることを明示

// 悪い例
int result = a + b * c;  // 優先順位はC#の標準ルールに従いますが、明示的でない
```

### 4. ファイルの構成

一般的に、1ファイルに1つの型を定義することで、コードの構成と管理が容易になります。ただし、小さな密接に関連する型については、`stylecop.json` の `topLevelTypes` 設定を使用して例外を設けることができます。
