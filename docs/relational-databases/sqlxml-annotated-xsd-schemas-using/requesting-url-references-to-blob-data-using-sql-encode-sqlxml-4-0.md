---
title: 'Sql を使用して BLOB データへの URL 参照の要求: エンコード (SQLXML 4.0) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sql:encode
- encode annotation
- URL references to BLOB data [SQLXML]
- references to BLOB data [SQLXML]
- annotated XSD schemas, URL references to BLOB data
- requesting URL references to BLOB data
- BLOBs, URL references
- Base 64-encoded format
ms.assetid: 2f8cd93b-c636-462b-8291-167197233ee0
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 537e2656730c7659edd22ac68722bf43e892ad3d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32970657"
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a>sql:encode を使用した、BLOB データへの URL 参照の要求 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  注釈付き XSD スキーマで、属性 (または要素) が Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の BLOB 列にマップされた場合、XML 内に返されるデータは Base 64 エンコード形式になります。  
  
 バイナリ形式で BLOB データ取得を指定する場合は、データへの参照 (URI) を返すを後で使用できます、 **sql: エンコード**注釈。 指定できます**sql: エンコード**属性または単純型の要素にします。  
  
 指定して、 **sql: エンコード**注釈フィールドの値ではなく、フィールドへの URL が返されることを示すためにします。 **sql: エンコード**URL 内の単一選択の生成に、主キーに依存します。 使用して、主キーを指定することができます、 **sql:key-フィールド**注釈。  
  
 **Sql: エンコード**"url"または"default"の値は、注釈を割り当てられていることができます。 "default" の場合、データは Base 64 エンコード形式で返されます。  
  
 **Sql: エンコード**で注釈を使用することはできません**sql:use-cdata** id、IDREF、IDREFS、NMTOKEN、または NMTOKENS 属性型またはします。 これも使用できません xsd**固定**属性。  
  
> [!NOTE]  
>  BLOB 型の列は、キーの一部または外部キーとして使用することはできません。  
  
## <a name="examples"></a>使用例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、次を参照してください。 [SQLXML の例を実行するための要件](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)です。  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a>A. BLOB データへの URL 参照を取得するため、sql:encode を指定する  
 この例では、マッピング スキーマを指定します**sql: エンコード**上、 **LargePhoto** (Base 64 - でバイナリ データを取得する代わりに、特定の製品写真への URI 参照を取得する属性エンコードされた形式)。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="ProductPhoto" sql:relation="Production.ProductPhoto"   
               sql:key-fields="ProductPhotoID" >  
   <xsd:complexType>  
      <xsd:attribute name="ProductPhotoID"  type="xsd:int"  />  
     <xsd:attribute name="LargePhoto" type="xsd:string" sql:encode="url" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 sqlEncode.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 sqlEncode.xml を保存したディレクトリに sqlEncodeT.xml として保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sqlEncode.xml">  
            /ProductPhoto[@ProductPhotoID=100]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (sqlEncode.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlEncode.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に使用する ADO](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
 結果を次に示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
