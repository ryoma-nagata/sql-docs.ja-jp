---
title: sp_helpextendedproc (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpextendedproc
- sp_helpextendedproc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpextendedproc
ms.assetid: 7e1f017e-c898-4225-b375-6a73ef9aac7b
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a7e9cc50f543232dea6b5ce39153eee2292284ac
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052250"
---
# <a name="sphelpextendedproc-transact-sql"></a>sp_helpextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在定義されている拡張ストアド プロシージャと、そのストアド プロシージャ (関数) を所有しているダイナミック リンク ライブラリ (DLL) の名前をレポートします。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに [CLR 統合](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpextendedproc [ [@funcname = ] 'procedure' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@funcname =**] **'***プロシージャ***'**  
 情報をレポートする拡張ストアド プロシージャの名前です。 *プロシージャ*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|拡張ストアド プロシージャの名前です。|  
|**dll**|**nvarchar (255)**|DLL の名前です。|  
  
## <a name="remarks"></a>コメント  
 ときに*プロシージャ*が指定されている**sp_helpextendedproc**拡張ストアド プロシージャの指定したレポートします。 このパラメーターが指定されていないときに**sp_helpextendedproc**が属するすべての拡張ストアド プロシージャの名前と各拡張ストアド プロシージャ DLL の名前を返します。  
  
## <a name="permissions"></a>アクセス許可  
 実行する権限**sp_helpextendedproc**に付与されます**パブリック**します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-reporting-help-on-all-extended-stored-procedures"></a>A. すべての拡張ストアド プロシージャに関するヘルプをレポートする  
 次の例では、すべての拡張ストアド プロシージャについてレポートします。  
  
```  
USE master;  
GO  
EXEC sp_helpextendedproc;  
GO  
```  
  
### <a name="b-reporting-help-on-a-single-extended-stored-procedure"></a>B. 特定の拡張ストアド プロシージャに関するヘルプをレポートする  
 次の例では、報告、`xp_cmdshell`拡張ストアド プロシージャ。  
  
```  
USE master;  
GO  
EXEC sp_helpextendedproc xp_cmdshell;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_addextendedproc &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
