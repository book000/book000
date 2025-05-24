# 順序ルール (SA1200-)

順序ルールは、コード要素の配置や順序に関するルールを定義します。これらのルールは、コードの構造を整理し、一貫性のある読みやすいコードベースの維持に役立ちます。

## ルール一覧

| ルールID | 名前 | 説明 |
|---------|------|------|
| [SA1200](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1200.md) | UsingDirectivesMustBePlacedCorrectly | `using` ディレクティブは名前空間の外部に配置する必要があります。 |
| [SA1201](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1201.md) | ElementsMustAppearInTheCorrectOrder | コード要素は正しい順序で記述する必要があります。 |
| [SA1202](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1202.md) | ElementsMustBeOrderedByAccess | コード要素はアクセスレベル順に記述する必要があります。 |
| [SA1203](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1203.md) | ConstantsMustAppearBeforeFields | 定数はフィールドの前に記述する必要があります。 |
| [SA1204](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1204.md) | StaticElementsMustAppearBeforeInstanceElements | 静的な要素はインスタンス要素の前に記述する必要があります。 |
| [SA1205](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1205.md) | PartialElementsMustDeclareAccess | partial要素はアクセス修飾子を宣言する必要があります。 |
| [SA1206](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1206.md) | DeclarationKeywordsMustFollowOrder | 宣言キーワードは正しい順序で記述する必要があります。 |
| [SA1207](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1207.md) | ProtectedMustComeBeforeInternal | `protected` は `internal` の前に記述する必要があります。 |
| [SA1208](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1208.md) | SystemUsingDirectivesMustBePlacedBeforeOtherUsingDirectives | System名前空間のusingディレクティブは他のusingディレクティブの前に配置する必要があります。 |
| [SA1209](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1209.md) | UsingAliasDirectivesMustBePlacedAfterOtherUsingDirectives | usingエイリアスディレクティブは他のusingディレクティブの後に配置する必要があります。 |
| [SA1210](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1210.md) | UsingDirectivesMustBeOrderedAlphabeticallyByNamespace | usingディレクティブは名前空間によってアルファベット順に並べる必要があります。 |
| [SA1211](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1211.md) | UsingAliasDirectivesMustBeOrderedAlphabeticallyByAliasName | usingエイリアスディレクティブはエイリアス名によってアルファベット順に並べる必要があります。 |
| [SA1212](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1212.md) | PropertyAccessorsMustFollowOrder | プロパティアクセサは正しい順序で記述する必要があります（getの後にset）。 |
| [SA1213](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1213.md) | EventAccessorsMustFollowOrder | イベントアクセサは正しい順序で記述する必要があります（addの後にremove）。 |
| [SA1214](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1214.md) | ReadonlyElementsMustAppearBeforeNonReadonlyElements | 読み取り専用要素は非読み取り専用要素の前に記述する必要があります。 |
| [SA1215](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1215.md) | InstanceReadonlyElementsMustAppearBeforeInstanceNonReadonlyElements | インスタンスの読み取り専用要素はインスタンスの非読み取り専用要素の前に記述する必要があります。 |
| [SA1216](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1216.md) | UsingStaticDirectivesMustBePlacedAtTheCorrectLocation | using static ディレクティブは正しい位置に配置する必要があります。 |
| [SA1217](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1217.md) | UsingStaticDirectivesMustBeOrderedAlphabetically | using static ディレクティブはアルファベット順に並べる必要があります。 |

## 設定方法

### stylecop.json の設定

順序ルールの一部は `stylecop.json` でカスタマイズできます：

```json
{
  "$schema": "https://raw.githubusercontent.com/DotNetAnalyzers/StyleCopAnalyzers/master/StyleCop.Analyzers/StyleCop.Analyzers/Settings/stylecop.schema.json",
  "settings": {
    "orderingRules": {
      "usingDirectivesPlacement": "outsideNamespace",
      "systemUsingDirectivesFirst": true,
      "blankLinesBetweenUsingGroups": "require"
    }
  }
}
```

主要な設定オプション：

- `usingDirectivesPlacement`: usingディレクティブの配置場所（`outsideNamespace` または `insideNamespace`）
- `systemUsingDirectivesFirst`: System名前空間のusingディレクティブを最初に配置するかどうか
- `blankLinesBetweenUsingGroups`: usingディレクティブグループ間に空白行を入れるかどうか（`allow`, `require`, `omit`）

### ルールの有効化/無効化

順序ルールを有効または無効にするには、`.editorconfig` ファイルを使用します：

```editorconfig
# usingディレクティブの場所に関するルールを無効化
dotnet_diagnostic.SA1200.severity = none

# コード要素の順序に関するルールを警告として設定
dotnet_diagnostic.SA1201.severity = warning
```

### 一般的なカスタマイズ例

#### usingディレクティブの配置

usingディレクティブの配置場所はプロジェクトの規約によって異なります：

```json
{
  "settings": {
    "orderingRules": {
      "usingDirectivesPlacement": "insideNamespace"
    }
  }
}
```

または、`.editorconfig`でルールを無効化：

```editorconfig
# usingディレクティブの配置に関するルールを無効化
dotnet_diagnostic.SA1200.severity = none
```

#### メンバーの順序

メンバーの順序に関するルールはプロジェクトの規約によって調整できます：

```editorconfig
# アクセスレベル順のルールを無効化
dotnet_diagnostic.SA1202.severity = none

# 静的メンバーとインスタンスメンバーの順序を無効化
dotnet_diagnostic.SA1204.severity = none
```

## 違反の抑制方法

特定の順序ルール違反を抑制するには、以下の方法があります：

1. コード内での抑制：

   ```csharp
   [SuppressMessage("StyleCop.CSharp.OrderingRules", "SA1201:ElementsMustAppearInTheCorrectOrder", Justification = "このクラスでは機能的グループ化を優先します")]
   public class MyClass
   {
       // 順序が標準と異なる要素
   }
   ```

2. グローバルな抑制：

   ```csharp
   [assembly: SuppressMessage("StyleCop.CSharp.OrderingRules", "SA1200:UsingDirectivesMustBePlacedCorrectly", Justification = "プロジェクトではusingディレクティブを名前空間内に配置します")]
   ```

3. プラグマディレクティブ：

   ```csharp
   #pragma warning disable SA1202 // 要素はアクセスレベル順に並べる必要があります
   public class MyClass
   {
       private void PrivateMethod() { }
       public void PublicMethod() { }  // 通常は public が先に来るべき
   }
   #pragma warning restore SA1202 // 要素はアクセスレベル順に並べる必要があります
   ```

4. `.editorconfig` ファイルでのカスタマイズ（上述の通り）

## 推奨される要素の順序

SA1201によって強制される、C#ファイル内での標準的な要素の順序は以下の通りです：

1. 外部エイリアス ディレクティブ
2. using ディレクティブ
3. 名前空間宣言
4. デリゲート
5. 列挙型
6. インターフェース
7. 構造体
8. クラス

クラス、構造体、またはインターフェース内：

1. 定数
2. フィールド
3. コンストラクタ
4. デリゲート
5. イベント
6. 列挙型
7. インターフェース
8. プロパティ
9. インデクサ
10. メソッド
11. 構造体
12. クラス

また、SA1202、SA1203、SA1204などの他のルールと併用すると、アクセスレベル、読み取り専用ステータス、静的/インスタンスの区別などにも順序が適用されます。
