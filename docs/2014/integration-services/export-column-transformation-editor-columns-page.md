---
title: 列エクスポート変換エディター ([列] ページ) |Microsoft Docs
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
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
caps.latest.revision: 28
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b427d8a727f0db31b63d43efbe00378c7ef0f18b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207452"
---
# <a name="export-column-transformation-editor-columns-page"></a>[列エクスポート変換エディター] ([列] ページ)
  **[列エクスポート変換エディター]** ダイアログ ボックスの **[列]** ページを使用すると、ファイルに抽出するデータ フロー内の列を指定できます。 列エクスポート変換でファイルにデータを追加するか、既存のファイルを上書きするかどうかを指定できます。  
  
 列エクスポート変換の詳細については、「 [Export Column Transformation](data-flow/transformations/export-column-transformation.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[列の抽出]**  
 テキストまたは画像データを持つ入力列の一覧から選択します。 すべての行には、 **[列の抽出]** と **[ファイル パス列]** の定義が含まれます。  
  
 **[ファイル パス列]**  
 ファイル パスとファイル名を持つ入力列の一覧から選択します。 すべての行には、 **[列の抽出]** と **[ファイル パス列]** の定義が含まれます。  
  
 **[追加の許可]**  
 変換により、既存のファイルにデータを追加するかどうかを指定します。 既定値は `false` です。  
  
 **[強制的に切り捨て]**  
 変換により、データを書き込む前に既存のファイルの内容を削除するかどうかを指定します。 既定値は `false` です。  
  
 **[バイト順マークの書き込み]**  
 バイト順マーク (BOM) をファイルに書き込むかどうかを指定します。 BOM がかどうか、データが書き込まれるのみ、`DT_NTEXT`または DT_WSTR データ型で、既存のデータ ファイルには追加されません。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [列エクスポート変換エディター&#40;エラー出力 ページ&#41;](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
