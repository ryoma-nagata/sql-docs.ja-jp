---
title: '更新プログラムを送信する: UpdateBatch メソッド |Microsoft ドキュメント'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 87123797-831f-48e0-94b5-f669f9ca194a
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a791806a21a2e1260a39dcadad62894e7eb85cb
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272481"
---
# <a name="sending-the-updates-updatebatch-method"></a>更新プログラムを送信する: UpdateBatch メソッド
次のコードは、adLockBatchOptimistic およびを CursorLocation LockType プロパティを設定して、バッチ モードでレコード セットを表示します。 2 つの新しいレコードを追加して、元の値を保存、既存のレコードのフィールドの値を変更し、データ ソースへの変更を返信する UpdateBatch を呼び出します。  
  
## <a name="remarks"></a>コメント  
  
```  
'BeginBatchUpdate  
    strConn = "Provider=SQLOLEDB;Initial Catalog=Northwind;" & _  
              "Data Source=MySQLServer;Integrated Security=SSPI;"  
  
    strSQL = "SELECT ShipperId, CompanyName, Phone FROM Shippers"  
  
    Set objRs1 = New ADODB.Recordset  
    objRs1.CursorLocation = adUseClient  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
  
    ' Change value of Phone field for first record in Recordset, saving value  
    ' for later restoration.  
    intId = objRs1("ShipperId")  
    sPhone = objRs1("Phone")  
  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Add two new records  
    For i = 0 To 1  
        objRs1.AddNew  
        objRs1(1) = "New Shipper #" & CStr((i + 1))  
        objRs1(2) = "(nnn) 555-" & i & i & i & i  
    Next i  
  
    ' Send the updates  
    objRs1.UpdateBatch  
'EndBatchUpdate  
```  
  
 現在のレコードを編集している UpdateBatch メソッドを呼び出すと、新しいレコードを追加する、ADO は自動的に Update メソッドを呼び出して、プロバイダーに変更を一括送信する前に、現在のレコードに保留中の変更を保存する場合。  
  
## <a name="see-also"></a>参照  
 [バッチ モード](../../../ado/guide/data/batch-mode.md)
