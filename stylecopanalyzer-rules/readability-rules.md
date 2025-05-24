# 可読性ルール (SA1100-)

可読性ルールは、コードの可読性と明確さを向上させるための規則を定義します。これらのルールは、コードの構造、演算子の使用方法、命名規則などに焦点を当て、他の開発者がコードを理解しやすくします。

## ルール一覧

| ルールID | 名前 | 説明 |
|---------|------|------|
| [SA1100](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1100.md) | DoNotPrefixCallsWithBaseUnlessLocalImplementationExists | オーバーライドやローカル実装が存在しない限り、継承したメンバーの呼び出しに`base.`プレフィックスを使用すべきではありません。 |
| [SA1101](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1101.md) | PrefixLocalCallsWithThis | インスタンスメンバーの呼び出しには`this.`プレフィックスを使用すべきです。 |
| [SA1102](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1102.md) | QueryClauses | クエリ句は前の句と同じ行に記述したり、次の行に記述したりすべきではありません。 |
| [SA1103](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1103.md) | QueryClausesMustBeOnSeparateLinesOrAllOnOneLine | クエリ句は別々の行に記述するか、すべて1行に記述する必要があります。 |
| [SA1104](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1104.md) | QueryClauseMustBeginOnNewLineWhenPreviousClauseSpansMultipleLines | 前の句が複数行にまたがる場合、クエリ句は新しい行から始める必要があります。 |
| [SA1105](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1105.md) | QueryClausesSpanningMultipleLinesMusBeginOnOwnLine | 複数行にまたがるクエリ句は、独自の行から始める必要があります。 |
| [SA1106](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1106.md) | CodeMustNotContainEmptyStatements | コードに空のステートメントを含めるべきではありません。 |
| [SA1107](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1107.md) | CodeMustNotContainMultipleStatementsOnOneLine | 1行に複数のステートメントを記述すべきではありません。 |
| [SA1108](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1108.md) | BlockStatementsMustNotContainEmbeddedComments | ブロックステートメントに埋め込みコメントを含めるべきではありません。 |
| [SA1109](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1109.md) | BlockStatementsMustNotContainEmbeddedRegions | ブロックステートメントに埋め込みリージョンを含めるべきではありません。 |
| [SA1110](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1110.md) | OpeningParenthesisMustBeOnDeclarationLine | 開始括弧はメソッド、インデクサ、またはコンストラクタの宣言行にあるべきです。 |
| [SA1111](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1111.md) | ClosingParenthesisMustBeOnLineOfLastParameter | 終了括弧は最後のパラメータと同じ行にあるか、宣言行にあるべきです。 |
| [SA1112](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1112.md) | ClosingParenthesisMustBeOnLineOfOpeningParenthesis | 終了括弧は開始括弧と同じ行にあるべきです。 |
| [SA1113](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1113.md) | CommaMustBeOnSameLineAsPreviousParameter | コンマは前のパラメータと同じ行にあるべきです。 |
| [SA1114](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1114.md) | ParameterListMustFollowDeclaration | パラメータリストは宣言の直後に記述する必要があります。 |
| [SA1115](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1115.md) | ParameterMustFollowComma | パラメータはコンマの直後に記述する必要があります。 |
| [SA1116](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1116.md) | SplitParametersMustStartOnLineAfterDeclaration | 分割されたパラメータリストは、宣言の次の行から開始する必要があります。 |
| [SA1117](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1117.md) | ParametersMustBeOnSameLineOrSeparateLines | パラメータは同じ行に記述するか、それぞれ別の行に記述する必要があります。 |
| [SA1118](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1118.md) | ParameterMustNotSpanMultipleLines | パラメータは複数行にまたがるべきではありません。 |
| [SA1119](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1119.md) | StatementMustNotUseUnnecessaryParenthesis | ステートメントは不必要な括弧を使用すべきではありません。 |
| [SA1120](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1120.md) | CommentsMustContainText | コメントはテキストを含む必要があります。 |
| [SA1121](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1121.md) | UseBuiltInTypeAlias | ビルトイン型のエイリアスを使用すべきです（例：`int`ではなく`System.Int32`）。 |
| [SA1122](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1122.md) | UseStringEmptyForEmptyStrings | 空の文字列には`String.Empty`を使用すべきです。 |
| [SA1123](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1123.md) | DoNotPlaceRegionsWithinElements | 要素内にリージョンを配置すべきではありません。 |
| [SA1124](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1124.md) | DoNotUseRegions | リージョンを使用すべきではありません。 |
| [SA1125](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1125.md) | UseShorthandForNullableTypes | Nullable型には省略形を使用すべきです（例：`Nullable<int>`ではなく`int?`）。 |
| [SA1126](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1126.md) | PrefixCallsCorrectly | メソッド呼び出しには適切なプレフィックスを使用する必要があります。 |
| [SA1127](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1127.md) | GenericTypeConstraintsMustBeOnOwnLine | ジェネリック型の制約は独自の行に記述する必要があります。 |
| [SA1128](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1128.md) | ConstructorInitializerMustBeOnOwnLine | コンストラクタ初期化子は独自の行に記述する必要があります。 |
| [SA1129](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1129.md) | DoNotUseDefaultValueTypeConstructor | 値型のデフォルトコンストラクタを使用すべきではありません。 |
| [SA1130](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1130.md) | UseLambdaSyntaxForAnonymousMethods | 匿名メソッドにはラムダ構文を使用すべきです。 |
| [SA1131](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1131.md) | UseReadableConditions | 読みやすい条件を使用すべきです（定数を左側に置かない）。 |
| [SA1132](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1132.md) | DoNotCombineFields | フィールド宣言を結合すべきではありません。 |
| [SA1133](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1133.md) | DoNotCombineAttributes | 属性を結合すべきではありません。 |
| [SA1134](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1134.md) | AttributesMustNotShareLine | 属性は行を共有すべきではありません。 |
| [SA1135](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1135.md) | UsingDirectivesMustBeQualified | using ディレクティブは完全修飾名を使用すべきです。 |
| [SA1136](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1136.md) | EnumValuesShouldBeOnSeparateLines | 列挙型の値は別々の行に記述する必要があります。 |
| [SA1137](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1137.md) | ElementsShouldHaveTheSameIndentation | 同じレベルの要素は同じインデントを持つべきです。 |
| [SA1139](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1139.md) | UseLiteralsSuffixNotationInsteadOfCasting | キャストの代わりにリテラルのサフィックス表記を使用すべきです。 |
| [SA1141](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1141.md) | UseTupleSyntax | タプル構文を使用すべきです。 |
| [SA1142](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1142.md) | ReferToTupleElementsByName | タプル要素は名前で参照すべきです。 |
| [SX1101](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SX1101.md) | DoNotPrefixLocalMembersWithThis | ローカルメンバーに`this.`プレフィックスを使用すべきではありません（SA1101の代替ルール）。 |

## 設定方法

### stylecop.json の設定

可読性ルールの一部は `stylecop.json` でカスタマイズできます：

```json
{
  "$schema": "https://raw.githubusercontent.com/DotNetAnalyzers/StyleCopAnalyzers/master/StyleCop.Analyzers/StyleCop.Analyzers/Settings/stylecop.schema.json",
  "settings": {
    "readabilityRules": {
      "allowBuiltInTypeAliases": true
    }
  }
}
```

主要な設定オプション：

- `allowBuiltInTypeAliases`: `System.Int32` などのビルトイン型エイリアスの使用を許可するかどうか

### ルールの有効化/無効化

可読性ルールを有効または無効にするには、`.editorconfig` ファイルを使用します：

```editorconfig
# this キーワードのプレフィックスに関するルールの設定
dotnet_diagnostic.SA1101.severity = none  # this プレフィックスを要求しない
dotnet_diagnostic.SX1101.severity = warning  # this プレフィックスを禁止する

# String.Empty の使用を要求しない
dotnet_diagnostic.SA1122.severity = none
```

### 一般的なカスタマイズ例

#### `this` キーワードの使用

`this` キーワードの使用については、プロジェクトチームによって異なる規約があります。SA1101（`this.` を要求）とSX1101（`this.` を禁止）は反対のルールなので、プロジェクトの規約に合わせて1つを選択します：

```editorconfig
# this プレフィックスを要求する場合
dotnet_diagnostic.SA1101.severity = warning
dotnet_diagnostic.SX1101.severity = none

# または、this プレフィックスを禁止する場合
dotnet_diagnostic.SA1101.severity = none
dotnet_diagnostic.SX1101.severity = warning
```

#### リージョンディレクティブの使用

リージョンディレクティブの使用についても意見が分かれることがあります：

```editorconfig
# リージョンの使用を許可
dotnet_diagnostic.SA1124.severity = none
```

#### その他のカスタマイズ

```editorconfig
# 空文字列に "" の使用を許可（String.Empty を強制しない）
dotnet_diagnostic.SA1122.severity = none

# Nullable 型に完全修飾名を許可
dotnet_diagnostic.SA1125.severity = suggestion
```

## 違反の抑制方法

特定の可読性ルール違反を抑制するには、以下の方法があります：

1. コード内での抑制：

   ```csharp
   [SuppressMessage("StyleCop.CSharp.ReadabilityRules", "SA1101:PrefixLocalCallsWithThis", Justification = "チームの規約では this プレフィックスを使用しません")]
   public class MyClass
   {
       private int _value;
       
       public void SetValue(int value)
       {
           _value = value; // this. プレフィックスなし
       }
   }
   ```

2. グローバルな抑制：

   ```csharp
   [assembly: SuppressMessage("StyleCop.CSharp.ReadabilityRules", "SA1124:DoNotUseRegions", Justification = "コードの論理的なセクションの区別にリージョンを使用します")]
   ```

3. プラグマディレクティブ：

   ```csharp
   #pragma warning disable SA1122 // 空文字列には String.Empty を使用すべきです
   string empty = "";
   #pragma warning restore SA1122 // 空文字列には String.Empty を使用すべきです
   ```

4. `.editorconfig` ファイルでのカスタマイズ（上述の通り）
