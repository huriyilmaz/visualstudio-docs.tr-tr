---
title: 'Iactivescriptauthor:: Removenamedidıtem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveNamedItem
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cade532d2ca276237981855cafe12804307d0bb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572847"
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
Betik yazma altyapısının ad alanından bir `NamedItem` nesnesini kaldırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszName`  
 'ndaki Kaldırılacak `NamedItem` nesnesini tanımlayan arabelleğin adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`S_FALSE`|@No__t_0 nesnesi, betik yazma altyapısının ad alanında yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 [IActiveScript:: Addnamedidıtem](../../winscript/reference/iactivescript-addnameditem.md) , `NamedItem` nesnesini betik yazma altyapısının ad alanına eklemek için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)    
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)