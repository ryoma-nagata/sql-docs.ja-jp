---
title: パス式のステップで軸の指定 |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- attribute axis [SQL Server]
- axis step [XQuery]
- descendant axis
- self axis
- path expressions [XQuery]
- child axis
- descendant-or-self axis
- parent axis
ms.assetid: c44fb843-0626-4496-bde0-52ca0bac0a9e
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2acb1aa6b9eddd2cf30f97da0d594db56b94e456
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38046880"
---
# <a name="path-expressions---specifying-axis"></a>パス式 - 軸の指定
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  パス式の軸ステップには、次のコンポーネントが含まれてます。  
  
-   軸  
  
-   A[ノード テスト](../xquery/path-expressions-specifying-node-test.md)  
  
-   [(省略可能) 0 個以上のステップ修飾子](../xquery/path-expressions-specifying-predicates.md)  
  
 詳細については、次を参照してください。[パス式&#40;XQuery&#41;](../xquery/path-expressions-xquery.md)します。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の XQuery 実装では、次の軸ステップがサポートされています。  
  
|軸|説明|  
|----------|-----------------|  
|**child**|コンテキスト ノードの子を返します。|  
|**descendant**|コンテキスト ノードのすべての子孫を返します。|  
|**parent**|コンテキスト ノードの親を返します。|  
|**attribute**|コンテキスト ノードの属性を返します。|  
|**self**|コンテキスト ノード自身を返します。|  
|**descendant-or-self**|コンテキスト ノード自身とその子孫をすべて返します。|  
  
 すべての軸を除く、**親**軸は順方向軸です。 **親**軸は、ドキュメントの階層で後方に検索するので、逆方向軸です。 たとえば、相対パス式 `child::ProductDescription/child::Summary` には 2 つのステップがあり、各ステップが `child` 軸を指定します。 最初の手順の取得、 \<ProductDescription > コンテキスト ノードの子要素。 各\<ProductDescription > 要素ノード、2 番目の手順の取得、\<概要 > 子要素ノード。  
  
 相対パス式では、`child::root/child::Location/attribute::LocationID`は次の 3 つのステップがあります。 最初の 2 つの手順をそれぞれ指定、`child`軸、および 3 番目の手順を指定します、`attribute`軸。 内の XML ドキュメントの製造手順に対して実行されたときに、 **Production.ProductModel**テーブル、式を返します、`LocationID`の属性、\<場所 > 子要素ノード、の\<ルート > 要素。  
  
## <a name="examples"></a>使用例  
 このトピックのクエリ例は、に対して指定されています**xml**内の列を入力、 **AdventureWorks**データベース。  
  
### <a name="a-specifying-a-child-axis"></a>A. child 軸の指定  
 特定の製品モデルの場合、次のクエリを取得、\<機能 > の子要素ノード、 \<ProductDescription > 要素ノードに格納されている製品カタログの説明から、`Production.ProductModel`テーブル。  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  /child::PD:ProductDescription/child::PD:Features')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   `query()`のメソッド、 **xml**データ型は、パス式を指定します。  
  
-   パス式の両方のステップが、`child` 軸およびノード名 (`ProductDescription`、`Features`) をノード テストとして指定しています。 ノード テストについては、次を参照してください。[パス式のステップでノード テストを指定する](../xquery/path-expressions-specifying-node-test.md)します。  
  
### <a name="b-specifying-descendant-and-descendant-or-self-axes"></a>B. descendant 軸と descendant-or-self 軸の指定  
 次の例では、descendant 軸と descendant-or-self 軸を使用します。 この例では、クエリがに対して指定されて、 **xml**型の変数。 XML インスタンスは、生成された結果の違いをわかりやすく示すために単純化してあります。  
  
```  
declare @x xml  
set @x='  
<a>  
 <b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
 </b>  
</a>'  
declare @y xml  
set @y = @x.query('  
  /child::a/child::b  
')  
select @y  
```  
  
 次の結果では、式から `<b>` 要素ノードの `<a>` 子要素ノードが返されます。  
  
```  
<b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
</b>  
```  
  
 この式で、  
  
 `/child::a/child::b/descendant::*`、のすべての子孫を要求している、<`b`> 要素ノード。  
  
 ノード テストのアスタリスク (*) によって、ノード名がノードテストとして表されます。 そのため、descendant 軸の主ノード型 (要素ノード) によって、返されるノードの型が決まります。 つまり、式はすべて要素ノードを返します。 テキスト ノードは返されません。 プライマリ ノード タイプとノード テストの関係の詳細については、次を参照してください。[パス式のステップでノード テストを指定する](../xquery/path-expressions-specifying-node-test.md)トピック。  
  
 つまり、次の結果に示すように、要素ノード <`c`> と <`d`> が返されます。  
  
```  
<c>text2  
     <d>text3</d>  
</c>  
<d>text3</d>  
```  
  
 Descendant 軸ではなく子孫または self 軸を指定する場合`/child::a/child::b/descendant-or-self::*`のコンテキスト ノードを返します要素 <`b`> とその子孫です。  
  
 結果を次に示します。  
  
```  
<b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
</b>  
  
<c>text2  
     <d>text3</d>  
</c>  
  
<d>text3</d>   
```  
  
 に対して次のサンプル クエリ、 **AdventureWorks**データベースのすべての子孫にあたる要素ノードの取得、<`Features`> の子要素、<`ProductDescription`> 要素。  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  /child::PD:ProductDescription/child::PD:Features/descendant::*  
')  
FROM  Production.ProductModel  
WHERE ProductModelID=19  
```  
  
### <a name="c-specifying-a-parent-axis"></a>C. parent 軸の指定  
 次のクエリは、`Production.ProductModel` テーブルに保存されている製品カタログ XML ドキュメントの <`ProductDescription`> 要素の <`Summary`> 子要素を返します。  
  
 この例では、parent 軸を使用して、<`Feature`> 要素の親を返し、<`ProductDescription`> 要素の <`Summary`> 子要素を取得します。  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  
/child::PD:ProductDescription/child::PD:Features/parent::PD:ProductDescription/child::PD:Summary  
')  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
  
```  
  
 このクエリ例では、パス式で `parent` 軸が使用されています。 次に示すように、この式を parent 軸を使用せずに書き直すこともできます。  
  
```  
/child::PD:ProductDescription[child::PD:Features]/child::PD:Summary  
```  
  
 次の例では、parent 軸の有用な使い方を示します。  
  
 格納されている各の製品モデル カタログの説明、 **CatalogDescription**の列、 **ProductModel**テーブルには、`<ProductDescription>`を持つ要素、`ProductModelID`属性と`<Features>`次のフラグメントで示すように、子要素。  
  
```  
<ProductDescription ProductModelID="..." >  
  ...  
  <Features>  
    <Feature1>...</Feature1>  
    <Feature2>...</Feature2>  
   ...  
</ProductDescription>  
```  
  
 クエリは、反復子変数を設定`$f`の要素の子を返します FLWOR ステートメントで、`<Features>`要素。 詳細については、次を参照してください。 [FLWOR ステートメントおよびイテレーション&#40;XQuery&#41;](../xquery/flwor-statement-and-iteration-xquery.md)します。 機能ごとに、`return`句は、次の形式で XML を構築します。  
  
```  
<Feature ProductModelID="...">...</Feature>  
<Feature ProductModelID="...">...</Feature>  
```  
  
 追加する、`ProductModelID`各`<Feature`> 要素、`parent`軸を指定します。  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
  for $f in /child::PD:ProductDescription/child::PD:Features/child::*  
  return  
   <Feature  
     ProductModelID="{ ($f/parent::PD:Features/parent::PD:ProductDescription/attribute::ProductModelID)[1]}" >  
          { $f }  
   </Feature>  
')  
FROM  Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 結果の一部を次に示します。  
  
```  
<Feature ProductModelID="19">  
  <wm:Warranty   
   xmlns:wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
    <wm:Description>parts and labor</wm:Description>  
  </wm:Warranty>  
</Feature>  
<Feature ProductModelID="19">  
  <wm:Maintenance   
   xmlns:wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <wm:NoOfYears>10 years</wm:NoOfYears>  
    <wm:Description>maintenance contract available through your dealer   
                  or any AdventureWorks retail store.</wm:Description>  
  </wm:Maintenance>  
</Feature>  
<Feature ProductModelID="19">  
  <p1:wheel   
   xmlns:p1="http://www.adventure-works.com/schemas/OtherFeatures">  
      High performance wheels.  
  </p1:wheel>  
</Feature>  
```  
  
 なお、述語`[1]`シングルトン値が返されるように、パスで式を追加します。  
  
  
