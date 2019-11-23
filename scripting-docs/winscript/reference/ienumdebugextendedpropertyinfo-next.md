---
title: 'Ienumdebugextendedpropertyınfo:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Next
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 23ebc3e3fd1f7802f4630be42a594d73f8657e43
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574266"
---
# <a name="ienumdebugextendedpropertyinfonext"></a>IEnumDebugExtendedPropertyInfo::Next
Sabit Listesi dizisinde belirtilen sayıda`ExtendedDebugPropertyInfo` yapısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Alınacak `ExtendedDebugPropertyInfo`yapısı sayısı.  
  
 `rgelt`  
 dışı `ExtendedDebugPropertyInfo` yapıların bir dizisi alındı.  
  
 `pceltFetched`  
 dışı Gerçekten alınan `ExtendedDebugPropertyInfo` yapı sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Geçerli bir `HRESULT`döndürür, genellikle `S_OK`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ienumdebugextendedpropertyınfo arabirimi](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo Yapısı](../../winscript/reference/extendeddebugpropertyinfo-structure.md)