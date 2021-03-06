---
title: シーケンス式 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sequence [XQuery]
- expressions [XQuery], sequence
- filtering sequences [XQuery]
ms.assetid: 41e18b20-526b-45d2-9bd9-e3b7d7fbce4e
caps.latest.revision: 22
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 34c26b529aeaee5e9f80ecc0a1a07d3cb8cedbf4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38048740"
---
# <a name="sequence-expressions-xquery"></a>シーケンス式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、アイテムのシーケンスの構築、フィルター処理、および組み合わせに使用される、XQuery 演算子がサポートされます。 項目には、アトミック値またはノードを指定できます。  
  
## <a name="constructing-sequences"></a>シーケンスの構築  
 コンマ演算子を使用して、複数のアイテムを 1 つのシーケンスに連結するシーケンスを構築できます。  
  
 シーケンスには、重複する値を含めることができます。 入れ子になったシーケンス、つまりシーケンス内にシーケンスがある場合、入れ子が解除され 1 つのシーケンスになります。 たとえば、シーケンス (1, 2, (3, 4, (5))) は (1, 2, 3, 4, 5) になります。 次に、シーケンス構築の例を示します。  
  
### <a name="example-a"></a>例 A  
 次のクエリは 5 つのアトミック値のシーケンスを返します。  
  
```  
declare @x xml  
set @x=''  
select @x.query('(1,2,3,4,5)')  
go  
-- result 1 2 3 4 5  
```  
  
 次のクエリは 2 つのノードのシーケンスを返します。  
  
```  
-- sequence of 2 nodes  
declare @x xml  
set @x=''  
select @x.query('(<a/>, <b/>)')  
go  
-- result  
<a />  
<b />  
```  
  
 次のクエリではアトミック値とノードのシーケンスが構築されているので、エラーが返されます。 これは異種シーケンスと呼ばれ、サポートされていません。  
  
```  
declare @x xml  
set @x=''  
select @x.query('(1, 2, <a/>, <b/>)')  
go  
```  
  
### <a name="example-b"></a>例 B  
 次のクエリでは、異なる長さの 4 つのシーケンスを 1 つのシーケンスに組み合わせることにより、アトミック値のシーケンスが構築されます。  
  
```  
declare @x xml  
set @x=''  
select @x.query('(1,2),10,(),(4, 5, 6)')  
go  
-- result = 1 2 10 4 5 6  
```  
  
 FLOWR および ORDER BY を使用して、シーケンスを並べ替えることができます。  
  
```  
declare @x xml  
set @x=''  
select @x.query('for $i in ((1,2),10,(),(4, 5, 6))  
                  order by $i  
                  return $i')  
go  
```  
  
 使用して、シーケンス内の項目をカウントすることができます、 **fn:count()** 関数。  
  
```  
declare @x xml  
set @x=''  
select @x.query('count( (1,2,3,(),4) )')  
go  
-- result = 4  
```  
  
### <a name="example-c"></a>例 C  
 AdditionalContactInfo 列に対して次のクエリを指定、 **xml** Contact テーブル内の型。 この列には、1 つ以上の追加の電話番号、ポケットベル番号、住所などの追加の連絡先情報が格納されます。 \<TelephoneNumber >、\<ポケットベル >、他のノードは、ドキュメントの任意の場所に記述できます。 クエリは、すべてを含むシーケンスを構築、 \<telephoneNumber > 続けて、コンテキスト ノードの子、\<ポケットベル > の子。 戻り値の式のコンマ シーケンス演算子の使用に注意してください`($a//act:telephoneNumber, $a//act:pager)`します。  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS act,  
 'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS aci)  
  
SELECT AdditionalContactInfo.query('  
   for $a in /aci:AdditionalContactInfo   
   return ($a//act:telephoneNumber, $a//act:pager)  
') As Result  
FROM Person.Contact  
WHERE ContactID=3  
```  
  
 結果を次に示します。  
  
```  
<act:telephoneNumber xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  <act:number>333-333-3333</act:number>  
</act:telephoneNumber>  
<act:telephoneNumber xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  <act:number>333-333-3334</act:number>  
</act:telephoneNumber>  
<act:pager xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  <act:number>999-555-1244</act:number>  
  <act:SpecialInstructions>  
Page only in case of emergencies.  
</act:SpecialInstructions>  
</act:pager>  
```  
  
## <a name="filtering-sequences"></a>シーケンスのフィルター処理  
 式に述語を追加することにより、式で返されるシーケンスをフィルター処理できます。 詳細については、次を参照してください。[パス式&#40;XQuery&#41;](../xquery/path-expressions-xquery.md)します。 たとえば次のクエリは、3 つの <`a`> 要素ノードのシーケンスを返します。  
  
```  
declare @x xml  
set @x = '<root>  
<a attrA="1">111</a>  
<a></a>  
<a></a>  
</root>'  
SELECT @x.query('/root/a')  
```  
  
 結果を次に示します。  
  
```  
<a attrA="1">111</a>  
<a />  
<a />  
```  
  
 のみを取得する <`a`> 要素を属性 attrA を持つ、述語でフィルターを指定することができます。 結果のシーケンスには、<`a`> 要素が 1 つだけ含まれます。  
  
```  
declare @x xml  
set @x = '<root>  
<a attrA="1">111</a>  
<a></a>  
<a></a>  
</root>'  
SELECT @x.query('/root/a[@attrA]')  
```  
  
 結果を次に示します。  
  
```  
<a attrA="1">111</a>  
```  
  
 パス式で述語を指定する方法の詳細については、次を参照してください。[パス式のステップで述語を指定する](../xquery/path-expressions-specifying-predicates.md)します。  
  
 次の例では、サブツリーのシーケンス式を構築し、次にフィルターをシーケンスに適用します。  
  
```  
declare @x xml  
set @x = '  
<a>  
  <c>C under a</c>  
</a>  
<b>    
   <c>C under b</c>  
</b>  
<c>top level c</c>  
<d></d>  
'  
```  
  
 内の式`(/a, /b)`サブツリーを持つシーケンスが構築`/a`と`/b`式を結果として得られるシーケンスから要素をフィルター処理と`<c>`します。  
  
```  
SELECT @x.query('  
  (/a, /b)/c  
')  
```  
  
 結果を次に示します。  
  
```  
<c>C under a</c>  
<c>C under b</c>  
```  
  
 次の例では、述語フィルターが適用されます。 式は、要素を検索します。 <`a`> と <`b`> 要素が含まれている <`c`>。  
  
```  
declare @x xml  
set @x = '  
<a>  
  <c>C under a</c>  
</a>  
<b>    
   <c>C under b</c>  
</b>  
  
<c>top level c</c>  
<d></d>  
'  
SELECT @x.query('  
  (/a, /b)[c]  
')  
```  
  
 結果を次に示します。  
  
```  
<a>  
  <c>C under a</c>  
</a>  
<b>  
  <c>C under b</c>  
</b>  
```  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   XQuery 範囲式はサポートされません。  
  
-   シーケンスは同種でなければなりません。 具体的には、シーケンス内のすべてのアイテムは、ノードまたはアトミック値のいずれかにする必要があります。 この点は静的にチェックされます。  
  
-   Union、Intersect、または Except の各演算子を使用したノード シーケンスの組み合わせはサポートされません。  
  
## <a name="see-also"></a>参照  
 [XQuery 式](../xquery/xquery-expressions.md)  
  
  
