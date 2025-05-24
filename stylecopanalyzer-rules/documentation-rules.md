# ドキュメンテーションルール (SA1600-)

ドキュメンテーションルールは、C#コードにおける XMLドキュメントコメントの形式、内容、存在に関するルールを定義します。これらのルールは、APIドキュメントの生成と一貫性のあるコードドキュメンテーションの維持に役立ちます。

## ルール一覧

| ルールID | 名前 | 説明 |
|---------|------|------|
| [SA1600](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1600.md) | ElementsMustBeDocumented | すべての要素（クラス、メソッドなど）にドキュメントコメントを付ける必要があります。 |
| [SA1601](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1601.md) | PartialElementsMustBeDocumented | PartialとマークされているすべてのC#要素にドキュメントコメントを付ける必要があります。 |
| [SA1602](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1602.md) | EnumerationItemsMustBeDocumented | すべての列挙型の項目にドキュメントコメントを付ける必要があります。 |
| [SA1603](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1603.md) | DocumentationMustContainValidXml | ドキュメントコメントは有効なXMLを含む必要があります。 |
| [SA1604](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1604.md) | ElementDocumentationMustHaveSummary | 要素のドキュメントコメントにsummaryタグを含める必要があります。 |
| [SA1605](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1605.md) | PartialElementDocumentationMustHaveSummary | partial要素のドキュメントコメントにsummaryタグを含める必要があります。 |
| [SA1606](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1606.md) | ElementDocumentationMustHaveSummaryText | 要素のドキュメントコメントのsummaryタグにテキストを含める必要があります。 |
| [SA1607](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1607.md) | PartialElementDocumentationMustHaveSummaryText | partial要素のドキュメントコメントのsummaryタグにテキストを含める必要があります。 |
| [SA1608](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1608.md) | ElementDocumentationMustNotHaveDefaultSummary | 要素のドキュメントコメントは、ビジュアルスタジオによって自動生成されたデフォルトのテキストを使用すべきではありません。 |
| [SA1609](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1609.md) | PropertyDocumentationMustHaveValue | プロパティのドキュメントコメントにvalueタグを含める必要があります。 |
| [SA1610](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1610.md) | PropertyDocumentationMustHaveValueText | プロパティのドキュメントコメントのvalueタグにテキストを含める必要があります。 |
| [SA1611](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1611.md) | ElementParametersMustBeDocumented | 要素のすべてのパラメータにparamタグを含むドキュメントを付ける必要があります。 |
| [SA1612](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1612.md) | ElementParameterDocumentationMustMatchElementParameters | 要素のドキュメントコメントのパラメータ名が実際のパラメータ名と一致する必要があります。 |
| [SA1613](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1613.md) | ElementParameterDocumentationMustDeclareParameterName | 要素のパラメータ用のドキュメントコメントには、パラメータ名を含める必要があります。 |
| [SA1614](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1614.md) | ElementParameterDocumentationMustHaveText | 要素のパラメータ用のドキュメントコメントには、パラメータの説明テキストを含める必要があります。 |
| [SA1615](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1615.md) | ElementReturnValueMustBeDocumented | 値を返す要素には、returnsタグを含むドキュメントコメントを付ける必要があります。 |
| [SA1616](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1616.md) | ElementReturnValueDocumentationMustHaveText | 要素のreturnsタグには、戻り値の説明テキストを含める必要があります。 |
| [SA1617](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1617.md) | VoidReturnValueMustNotBeDocumented | void型を返す要素には、returnsタグを含めるべきではありません。 |
| [SA1618](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1618.md) | GenericTypeParametersMustBeDocumented | ジェネリック型パラメータには、typeparamタグを使用してドキュメントを付ける必要があります。 |
| [SA1619](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1619.md) | GenericTypeParametersMustBeDocumentedPartialClass | partial クラスのジェネリック型パラメータには、typeparamタグを使用してドキュメントを付ける必要があります。 |
| [SA1620](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1620.md) | GenericTypeParameterDocumentationMustMatchTypeParameters | ジェネリック型パラメータのドキュメント名が実際の型パラメータ名と一致する必要があります。 |
| [SA1621](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1621.md) | GenericTypeParameterDocumentationMustDeclareParameterName | 型パラメータのドキュメントコメントには、パラメータ名を含める必要があります。 |
| [SA1622](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1622.md) | GenericTypeParameterDocumentationMustHaveText | 型パラメータのドキュメントコメントには、パラメータの説明テキストを含める必要があります。 |
| [SA1623](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1623.md) | PropertySummaryDocumentationMustMatchAccessors | プロパティのsummaryテキストは、プロパティが「取得」されるのか「設定」されるのかを正しく記述する必要があります。 |
| [SA1624](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1624.md) | PropertySummaryDocumentationMustOmitSetAccessorWithRestrictedAccess | 制限付きsetアクセサーを持つプロパティのsummaryテキストは、setを言及すべきではありません。 |
| [SA1625](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1625.md) | ElementDocumentationMustNotBeCopiedAndPasted | 要素のドキュメントコメントは他の要素からコピー＆ペーストすべきではありません。 |
| [SA1626](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1626.md) | SingleLineCommentsMustNotUseDocumentationStyleSlashes | 単一行コメントはドキュメンテーションスタイルのスラッシュ（///）を使用すべきではありません。 |
| [SA1627](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1627.md) | DocumentationTextMustNotBeEmpty | ドキュメントコメントのテキストは空であってはなりません。 |
| [SA1628](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1628.md) | DocumentationTextMustBeginWithACapitalLetter | ドキュメントテキストは大文字で始める必要があります。 |
| [SA1629](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1629.md) | DocumentationTextMustEndWithAPeriod | ドキュメントテキストはピリオドで終わる必要があります。 |
| [SA1630](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1630.md) | DocumentationTextMustContainWhitespace | ドキュメントテキストには空白を含める必要があります。 |
| [SA1631](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1631.md) | DocumentationMustMeetCharacterPercentage | ドキュメントテキストは一定の文字の割合を満たす必要があります。 |
| [SA1632](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1632.md) | DocumentationTextMustMeetMinimumCharacterLength | ドキュメントテキストは最小文字長を満たす必要があります。 |
| [SA1633](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1633.md) | FileMustHaveHeader | ファイルにはヘッダーが必要です。 |
| [SA1634](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1634.md) | FileHeaderMustShowCopyright | ファイルヘッダーには著作権表示が必要です。 |
| [SA1635](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1635.md) | FileHeaderMustHaveCopyrightText | ファイルヘッダーに著作権テキストを含める必要があります。 |
| [SA1636](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1636.md) | FileHeaderCopyrightTextMustMatch | ファイルヘッダーの著作権テキストが一致する必要があります。 |
| [SA1637](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1637.md) | FileHeaderMustContainFileName | ファイルヘッダーにはファイル名を含める必要があります。 |
| [SA1638](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1638.md) | FileHeaderFileNameDocumentationMustMatchFileName | ファイルヘッダーのファイル名ドキュメントが実際のファイル名と一致する必要があります。 |
| [SA1639](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1639.md) | FileHeaderMustHaveSummary | ファイルヘッダーにはサマリーを含める必要があります。 |
| [SA1640](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1640.md) | FileHeaderMustHaveValidCompanyText | ファイルヘッダーには有効な会社テキストを含める必要があります。 |
| [SA1641](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1641.md) | FileHeaderCompanyNameTextMustMatch | ファイルヘッダーの会社名テキストが一致する必要があります。 |
| [SA1642](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1642.md) | ConstructorSummaryDocumentationMustBeginWithStandardText | コンストラクタのサマリードキュメントは標準テキストで始まる必要があります。 |
| [SA1643](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1643.md) | DestructorSummaryDocumentationMustBeginWithStandardText | デストラクタのサマリードキュメントは標準テキストで始まる必要があります。 |
| [SA1644](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1644.md) | DocumentationHeadersMustNotContainBlankLines | ドキュメントヘッダーには空白行を含めるべきではありません。 |
| [SA1645](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1645.md) | IncludeNodeDoesNotContainValidFileAndPath | includeノードが有効なファイルとパスを含んでいません。 |
| [SA1646](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1646.md) | IncludedDocumentationXPathDoesNotExist | 含まれるドキュメンテーションのXPathが存在しません。 |
| [SA1647](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1647.md) | IncludeNodeDoesNotContainValidXPath | includeノードが有効なXPathを含んでいません。 |
| [SA1648](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1648.md) | InheritDocMustBeUsedWithInheritingClass | inheritdocは継承クラスで使用する必要があります。 |
| [SA1649](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1649.md) | FileHeaderFileNameDocumentationMustMatchTypeName | ファイルヘッダーのファイル名ドキュメントが型名と一致する必要があります。 |
| [SA1650](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1650.md) | ElementDocumentationMustBeSpelledCorrectly | 要素のドキュメントは正しくスペルする必要があります。 |
| [SA1651](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1651.md) | DoNotIncludeStandardSummaryInDocumentationXml | 標準のサマリーをドキュメントXMLに含めないでください。 |

## 設定方法

### stylecop.json の設定

ドキュメンテーションルールでは、特にファイルヘッダーに関する設定を `stylecop.json` でカスタマイズすることができます：

```json
{
  "$schema": "https://raw.githubusercontent.com/DotNetAnalyzers/StyleCopAnalyzers/master/StyleCop.Analyzers/StyleCop.Analyzers/Settings/stylecop.schema.json",
  "settings": {
    "documentationRules": {
      "companyName": "あなたの会社名",
      "copyrightText": "Copyright (c) {companyName}. All rights reserved.",
      "xmlHeader": true,
      "fileNamingConvention": "metadata",
      "documentInterfaces": true,
      "documentExposedElements": true,
      "documentInternalElements": false,
      "documentPrivateElements": false,
      "documentPrivateFields": false
    }
  }
}
```

主要な設定オプション：

- `companyName`: 会社名
- `copyrightText`: 著作権テキスト（`{companyName}` 変数を使用可能）
- `xmlHeader`: XMLファイルヘッダーを使用するかどうか
- `fileNamingConvention`: ファイル命名規則（`metadata` または `stylecop`）
- `documentInterfaces`, `documentExposedElements`など: どのレベルの要素にドキュメントを必須とするか

### ルールの有効化/無効化

ドキュメンテーションルールを有効または無効にするには、`.editorconfig` ファイルを使用します：

```editorconfig
# ファイルヘッダーの要件を無効化
dotnet_diagnostic.SA1633.severity = none

# プライベートメンバーのドキュメントを要求しない
dotnet_diagnostic.SA1600.severity = suggestion
```

### 一般的なカスタマイズ例

#### ドキュメント要件のレベル設定

多くのプロジェクトでは、パブリックAPIのみドキュメントを必須とし、内部実装の詳細はオプションとすることがあります：

```json
{
  "settings": {
    "documentationRules": {
      "documentExposedElements": true,
      "documentInternalElements": false,
      "documentPrivateElements": false
    }
  }
}
```

さらに、`.editorconfig`で特定のルールを調整：

```editorconfig
# パラメータと戻り値のドキュメントは警告として設定
dotnet_diagnostic.SA1611.severity = warning
dotnet_diagnostic.SA1615.severity = warning

# ジェネリックパラメータのドキュメントをオプションに設定
dotnet_diagnostic.SA1618.severity = suggestion
```

#### ファイルヘッダーのカスタマイズ

プロジェクト固有のファイルヘッダーを設定：

```json
{
  "settings": {
    "documentationRules": {
      "companyName": "あなたの会社名",
      "copyrightText": "Copyright (c) {companyName} {year}. All rights reserved.\nLicensed under the MIT License. See LICENSE file for license information.",
      "xmlHeader": true
    }
  }
}
```

## 違反の抑制方法

特定のドキュメンテーションルール違反を抑制するには、以下の方法があります：

1. コード内での抑制：

   ```csharp
   [SuppressMessage("StyleCop.CSharp.DocumentationRules", "SA1600:ElementsMustBeDocumented", Justification = "内部ユーティリティメソッド")]
   private void InternalHelper()
   {
       // メソッドの実装
   }
   ```

2. グローバルな抑制：

   ```csharp
   [assembly: SuppressMessage("StyleCop.CSharp.DocumentationRules", "SA1633:FileMustHaveHeader", Justification = "このプロジェクトではファイルヘッダーを使用しません")]
   ```

3. プラグマディレクティブ：

   ```csharp
   #pragma warning disable SA1600 // 要素にはドキュメントを付ける必要があります
   internal class InternalHelper
   {
       // クラスの実装
   }
   #pragma warning restore SA1600 // 要素にはドキュメントを付ける必要があります
   ```

4. `.editorconfig` ファイルでのカスタマイズ（上述の通り）
