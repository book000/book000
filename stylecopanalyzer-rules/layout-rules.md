# レイアウトルール (SA1500-)

レイアウトルールは、コードの物理的な構造やフォーマットに関するルールを定義します。これらのルールは、ブレースの配置、コードの行間隔、空白行など、コードの視覚的な一貫性を確保するのに役立ちます。

## ルール一覧

| ルールID | 名前 | 説明 |
|---------|------|------|
| [SA1500](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1500.md) | BracesForMultiLineStatementsMustNotShareLine | 複数行のステートメントのブレースは、独自の行に配置する必要があります。 |
| [SA1501](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1501.md) | StatementMustNotBeOnSingleLine | 開始ブレースと終了ブレースを持つステートメントは一行にすべて記述すべきではありません。 |
| [SA1502](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1502.md) | ElementMustNotBeOnSingleLine | 開始ブレースと終了ブレースを持つ要素は一行にすべて記述すべきではありません。 |
| [SA1503](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1503.md) | CurlyBracketsMustNotBeOmitted | 制御ブロックの中括弧を省略すべきではありません。 |
| [SA1504](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1504.md) | AllAccessorsMustBeSingleLineOrMultiLine | すべてのアクセサは、単一行または複数行のいずれかで記述する必要があります。 |
| [SA1505](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1505.md) | OpeningBracesMustNotBeFollowedByBlankLine | 開始ブレースの後に空白行を入れるべきではありません。 |
| [SA1506](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1506.md) | ElementDocumentationHeadersMustNotBeFollowedByBlankLine | 要素のドキュメンテーションヘッダーの後に空白行を入れるべきではありません。 |
| [SA1507](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1507.md) | CodeMustNotContainMultipleBlankLinesInARow | コードに連続する複数の空白行を含めるべきではありません。 |
| [SA1508](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1508.md) | ClosingBracesMustNotBePrecededByBlankLine | 終了ブレースの前に空白行を入れるべきではありません。 |
| [SA1509](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1509.md) | OpeningBracesMustNotBePrecededByBlankLine | 開始ブレースの前に空白行を入れるべきではありません。 |
| [SA1510](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1510.md) | ChainedStatementBlocksMustNotBePrecededByBlankLine | 連鎖したステートメントブロックの前に空白行を入れるべきではありません。 |
| [SA1511](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1511.md) | WhileDoFooterMustNotBePrecededByBlankLine | while-do文のフッターの前に空白行を入れるべきではありません。 |
| [SA1512](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1512.md) | SingleLineCommentsMustNotBeFollowedByBlankLine | 単一行コメントの後に空白行を入れるべきではありません。 |
| [SA1513](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1513.md) | ClosingBraceMustBeFollowedByBlankLine | 終了ブレースの後には空白行を入れる必要があります。 |
| [SA1514](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1514.md) | ElementDocumentationHeaderMustBePrecededByBlankLine | 要素のドキュメンテーションヘッダーの前には空白行を入れる必要があります。 |
| [SA1515](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1515.md) | SingleLineCommentMustBePrecededByBlankLine | 単一行コメントの前には空白行を入れる必要があります。 |
| [SA1516](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1516.md) | ElementsMustBeSeparatedByBlankLine | 要素間は空白行で区切る必要があります。 |
| [SA1517](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1517.md) | CodeMustNotContainBlankLinesAtStartOfFile | ファイルの先頭に空白行を含めるべきではありません。 |
| [SA1518](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1518.md) | UseLineEndingsCorrectlyAtEndOfFile | ファイルの末尾では行末文字を正しく使用する必要があります。 |
| [SA1519](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1519.md) | BracesMustNotBeOmittedFromMultiLineChildStatement | 複数行の子ステートメントからブレースを省略すべきではありません。 |
| [SA1520](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1520.md) | UseBracesConsistently | ブレースは一貫して使用する必要があります。 |

## 設定方法

### stylecop.json の設定

レイアウトルールの多くは直接 `stylecop.json` でカスタマイズすることはできませんが、以下の関連設定が可能です：

```json
{
  "$schema": "https://raw.githubusercontent.com/DotNetAnalyzers/StyleCopAnalyzers/master/StyleCop.Analyzers/StyleCop.Analyzers/Settings/stylecop.schema.json",
  "settings": {
    "indentation": {
      "indentationSize": 4,
      "tabSize": 4,
      "useTabs": false
    }
  }
}
```

### ルールの有効化/無効化

レイアウトルールを有効または無効にするには、`.editorconfig` ファイルを使用します：

```editorconfig
# SA1503（中括弧省略の禁止）を無効化
dotnet_diagnostic.SA1503.severity = none

# SA1513（終了ブレース後の空白行の要求）を警告として設定
dotnet_diagnostic.SA1513.severity = warning
```

### 一般的なカスタマイズ例

#### 制御文のブレース

ブレースの使用に関するルールは意見が分かれることが多いです。一部のチームでは単一行の制御文にブレースを省略することを好みます：

```editorconfig
# 制御ブロックの中括弧省略を許可
dotnet_diagnostic.SA1503.severity = none
```

#### 空白行の制御

空白行に関するルールもプロジェクトごとのスタイル選好に合わせてカスタマイズすることができます：

```editorconfig
# 連続する複数の空白行を許可
dotnet_diagnostic.SA1507.severity = none

# 単一行コメントの前の空白行要件を無効化
dotnet_diagnostic.SA1515.severity = none
```

## 違反の抑制方法

特定のレイアウトルール違反を抑制するには、以下の方法があります：

1. コード内での抑制：

   ```csharp
   [SuppressMessage("StyleCop.CSharp.LayoutRules", "SA1503:CurlyBracketsMustNotBeOmitted", Justification = "単一行の制御文で読みやすくするため")]
   public void SomeMethod()
   {
       if (condition) DoSomething();
   }
   ```

2. グローバルな抑制：

   ```csharp
   [assembly: SuppressMessage("StyleCop.CSharp.LayoutRules", "SA1503:CurlyBracketsMustNotBeOmitted", Justification = "このプロジェクトでは単一行の制御文でブレースを省略します")]
   ```

3. プラグマディレクティブ：

   ```csharp
   #pragma warning disable SA1503 // 制御ブロックの中括弧を省略すべきではありません
   if (condition) DoSomething();
   #pragma warning restore SA1503 // 制御ブロックの中括弧を省略すべきではありません
   ```

4. `.editorconfig` ファイルでのカスタマイズ（上述の通り）
