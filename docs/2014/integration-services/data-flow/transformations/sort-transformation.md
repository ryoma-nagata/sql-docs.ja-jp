---
title: 並べ替え変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sorttrans.f1
helpviewer_keywords:
- Sort transformation
- descending sorts
- ascending sorts
- sorting data [Integration Services]
- multiple sorts
- duplicate data [Integration Services]
ms.assetid: 728c9351-84a8-4a89-be4d-d50d4adc04e0
caps.latest.revision: 50
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5155e1bc61e5a02d29420d20b1e2970693dda1da
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150723"
---
# <a name="sort-transformation"></a>並べ替え変換
  並べ替え変換は、入力データを昇順または降順で並べ替え、並べ替えたデータを変換出力にコピーします。 入力には複数の並べ替えを適用できます。各並べ替えは、並べ替えの順序を決定する数値によって識別されます。 順序の数値が最も小さい列が最初に並べ替えられ、順序の数値の大きさの順に列が並べ替えられます。 たとえば、 **CountryRegion** という名前の列の並べ替え順序が 1 で、 **City** という名前の列の並べ替え順序が 2 の場合、出力は、国または地域、次に都市の順に並べ替えられます。 正の値は昇順の並べ替えを表し、負の値は降順の並べ替えを表します。 並べ替えを行わない列の並べ替え順序は 0 です。 並べ替えを選択されていない列は、並べ替えられた列と共に、自動的に変換出力にコピーされます。  
  
 並べ替え変換には、比較オプションのセットが含まれており、変換による列の文字列データの処理方法を決定します。 詳しくは、「 [Comparing String Data](../comparing-string-data.md)」をご覧ください。  
  
> [!NOTE]  
>  並べ替え変換では、GUID は Transact-SQL で ORDER BY 句を使用したときと同じ順序では並べ替えられません。 並べ替え変換では、0 ～ 9 で始まる GUID は A ～ F で始まる GUID の前に並べ替えられますが、ORDER BY 句では [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]での実装と同じく、並べ替え変換とは異なる順番で並べ替えられます。 詳細については、「[ORDER BY 句 (Transact-SQL)](/sql/t-sql/queries/select-order-by-clause-transact-sql)」を参照してください。  
  
 また、並べ替え変換では、並べ替えの実行時に重複する行を削除できます。 重複する行とは、並べ替えキーの値が同じ行のことです。 並べ替えキーの値は、使用する文字列比較オプションに基づいて生成されます。したがって、リテラル文字列が異なっていても、並べ替えキーの値は同じとなる場合があります。 並べ替え変換は、値は異なるが並べ替えキーが同じ入力列の行を、重複していると識別します。  
  
 並べ替え変換には、`MaximumThreads`パッケージが読み込まれるときに、プロパティ式で更新可能なカスタム プロパティ。 詳細については、「[Integration Services &#40;SSIS&#41; の式](../../expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../../expressions/use-property-expressions-in-packages.md)」、および「[変換のカスタム プロパティ](transformation-custom-properties.md)」を参照してください。  
  
 この変換は 1 つの入力と 1 つの出力をとります。 エラー出力はサポートされていません。  
  
## <a name="configuration-of-the-sort-transformation"></a>並べ替え変換の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[並べ替え変換エディター]** ダイアログ ボックスで設定できるプロパティについては、「 [並べ替え変換エディター](../../sort-transformation-editor.md)」を参照してください。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../../common-properties.md)  
  
-   [変換のカスタム プロパティ](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 コンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## <a name="related-content"></a>関連コンテンツ  
 codeplex.com のサンプル「 [SortDeDuplicateDelimitedString カスタム SSIS コンポーネント](http://go.microsoft.com/fwlink/?LinkId=220821)」  
  
## <a name="see-also"></a>参照  
 [データ フロー](../data-flow.md)   
 [Integration Services の変換](integration-services-transformations.md)  
  
  
