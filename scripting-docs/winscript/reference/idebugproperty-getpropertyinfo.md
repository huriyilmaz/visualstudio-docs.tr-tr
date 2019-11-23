---
title: 'Idebugproperty:: GetPropertyInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0698e09cd9643322a237a81d971248577fd97e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562329"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Bir yöntemi veya dizini oluşturulmuş özelliği açıklayan `IDebugProperty` değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwFields`  
 'ndaki `DebugPropertyInfo` yapısında doldurulacak alanları belirleyen `DBGPROP_INFO_FLAGS` sabitlerini belirtir.  
  
 `nRadix`  
 'ndaki Herhangi bir sayısal bilgiyi biçimlendirmede kullanılacak Radix.  
  
 `pPropertyInfo`  
 dışı Özelliği tanımlayan `DebugPropertyInfo` yapısını döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Geçerli bir `HRESULT`döndürür, genellikle `S_OK`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugproperty arabirimi](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [DebugPropertyInfo Yapısı](../../winscript/reference/debugpropertyinfo-structure.md)