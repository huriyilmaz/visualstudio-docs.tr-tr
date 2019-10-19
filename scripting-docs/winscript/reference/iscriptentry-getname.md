---
title: 'Icriptentry:: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetName
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c99cda48a20efb41b2535645ccdb50be8bb6d6bc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575446"
---
# <a name="iscriptentrygetname"></a>IScriptEntry::GetName
Tek bir nesneyi temsil eden girişler (örneğin, bir işlev) için, nesnenin adını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstr`  
 dışı @No__t_0 betik bloğu tarafından temsil edilen nesnenin adı. Bir girdi tek bir nesneyi temsil ediyorsa NULL döndürülür.  
  
 Alt girişler tek bir işlev nesnesini temsil eder.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Icriptentry arabirimi](../../winscript/reference/iscriptentry-interface.md)    
 [IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)