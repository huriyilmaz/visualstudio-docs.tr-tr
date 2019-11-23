---
title: 'Icriptentry:: setItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ba226704f5b064c86b52c1b349650d509b2b549
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575365"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
`IScriptEntry` nesnesini tanımlayan öğe adını ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `psz`  
 'ndaki Öğe adını içeren bir arabelleğin adresi. Öğe adı, ana bilgisayar tarafından girişi tanımlamak için kullanılır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Yöntem başarılı olmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IScriptEntry` nesneler için, bu yöntem `S_OK`döndürür.  
  
 `IScriptScriptlet` nesneler için (`IScriptEntry`türeten), bu yöntem `E_FAIL`döndürür. `IScriptScriptlet` nesneler için, öğe adı [ıactivescriptauthor:: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) tarafından ayarlanır ve değiştirilemez.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Icriptentry arabirimi](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)