---
title: 'Icriptentry:: GetItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetItemName
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcd1b83fa6d22fafc2123645f1f252fa1325f7f1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575457"
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
Bir `IScriptEntry` nesnesini tanımlayan öğe adını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstr`  
 dışı Öğe adını içeren bir arabelleğin adresi. Öğe adı, ana bilgisayar tarafından girişi tanımlamak için kullanılır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 nesneler için, [ıactivescriptauthor:: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)kullanarak öğe adını ayarlarsınız. Diğer arabirimler için, [ıcriptentry:: setItemName](../../winscript/reference/iscriptentry-setitemname.md)kullanarak öğe adını ayarlarsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IScriptEntry Arabirimi](../../winscript/reference/iscriptentry-interface.md)