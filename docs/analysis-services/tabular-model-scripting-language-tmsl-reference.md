---
title: 表形式モデルのスクリプト言語 (TMSL) リファレンス |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 713fecbb367ac4717604c14b6f23baab905a993f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34043776"
---
# <a name="tabular-model-scripting-language-tmsl-reference"></a>表形式モデルのスクリプト言語 (TMSL) のリファレンス
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

  Tabular Model Scripting Language (TMSL) は、Analysis Services 表形式モデルのデータベース互換性レベル 1200 以上のコマンドとオブジェクト モデルの定義構文です。 TMSL は、XMLA プロトコルを介して Analysis Services と通信する場所、 [XMLA です。実行](../analysis-services/xmla/xml-elements-methods-execute.md)メソッドは、両方を受け取ります JSON ベース**ステートメント**TMSL だけでなく、従来 XML ベースのスクリプトでスクリプト[Analysis Services スクリプト言語&#40;の ASSL を XMLA&#41; ](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
 TMSL の主要な要素は次のとおりです。  
  
-   表形式モデルのセマンティクスに基づく表形式のメタデータ。 表形式モデルは、テーブル、列、およびリレーションシップで構成されます。 TMSL で同等のオブジェクト定義は、テーブル、列、リレーションシップ、およびなどは今すぐ、当然ながら、です。  
  
     新しいメタデータ エンジンには、これらの定義がサポートしています。  
  
-   オブジェクトの定義は、XML ではなく JSON として構成されています。  
  
 ペイロードは、(JSON または XML) で書式設定方法、を除き TMSL と ASSL の両方がコマンドおよびサーバーの通信とデータの転送に使用される XMLA メソッドへのメタデータを提供する方法に機能的に同等です。  
  
## <a name="how-to-use-tmsl"></a>TMSL を使用する方法  
 TMSL スクリプトを探索する最も簡単な方法はコマンドを使用して、CREATE、ALTER、DELETE、またはプロセス SQL Server Management Studio (SSMS) を既に知っているモデルにします。 既存のモデルを使用するいると仮定した場合、最初の互換性レベル 1200 以上にアップグレードしてください。  
  
1.  使用するコマンドは、検索:[で表形式モデル スクリプト言語コマンド&#40;TMSL&#41;](../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md)  
  
2.  コマンドで使用されるオブジェクトのオブジェクト定義の参照を確認します[オブジェクト定義を表形式モデル スクリプト言語で&#40;TMSL。&#41;](../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md)  
  
3.  TMSL スクリプトを送信するためのメソッドを選択します。  
  
    -   Management Studio での XMLA ウィンドウ  
  
    -   **呼び出す ascmd** AMO PowerShell を使用して ([Invoke ASCmd コマンドレット](../analysis-services/powershell/invoke-ascmd-cmdlet.md))  
  
    -   [Analysis Services DDL 実行タスク](../integration-services/control-flow/analysis-services-execute-ddl-task.md)SSIS でします。  
  
## <a name="model-definition-schema"></a>モデルの定義スキーマ  
 次のスクリーン ショットは、省略形のバージョンの主要なオブジェクトを表示するために折りたたむ、スキーマを示します。  
  
 ![SSAS_TabularMetadata](../analysis-services/media/ssas-tabularmetadata.JPG "SSAS_TabularMetadata")  
  
## <a name="scripting-languages-in-analysis-services"></a>Analysis services スクリプト言語  
 Analysis Services には、ASSL、TMSL スクリプト言語がサポートしています。 以上の互換性レベル 1200 で作成された表形式モデルだけは、JSON 形式に TMS に記載されています。  
  
 [Analysis Services スクリプト言語&#40;の ASSL を XMLA&#41; ](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)が最初のスクリプト言語および多次元モデルと下位の互換性レベル (1100 または 1103) でのテーブル モデルに対してのみのスクリプト言語でがあります。 Assl で表形式モデル 110x、条項に記載された多次元など**キューブ**(モデル) 用と**measuregroup** (テーブル) 用です。  
  
> [!NOTE]  
>  [SQL Server Data Tools (SSDT) を切り替えることで、TMSL を使用する以前のバージョン表形式モデルをアップグレードすることができます、 **CompatibilityLevel** 1200 またはそれ以降。 アップグレードは元に元に戻すことに注意してください。 をアップグレードする前に、元のバージョンを後で必要な場合、モデルをバックアップします。  
  
 次の表は、特定の互換性レベルでの異なるバージョン間での Analysis Services データ モデルのスクリプト言語行列です。  

||||||  
|-|-|-|-|-|  
|**[バージョン]**|**多次元**|**表形式 110x**|**表形式 1200**| **表形式の 1400** |
|Azure Analysis Services|NA|NA|TMSL|TMSL| 
|SQL Server 2017|ASSL|ASSL|TMSL|TMSL| 
|SQL Server 2016|ASSL|ASSL|TMSL|TMSL| 
|SQL Server 2014|ASSL|ASSL|NA|NA|   
|SQL Server 2012|ASSL|ASSL|NA|NA|  

  
## <a name="see-also"></a>参照  
 [Analysis services 表形式モデルの互換性レベル](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Analysis Services スクリプト言語&#40;の ASSL を XMLA&#41;](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
