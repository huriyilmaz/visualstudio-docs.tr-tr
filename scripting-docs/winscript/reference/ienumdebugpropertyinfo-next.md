---
title: 'Ienumdebugpropertyınfo:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Next
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b99631c217ca56dce91512403dfb6623cd1e7641
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574192"
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
Sabit Listesi dizisinde belirtilen sayıda `DebugPropertyInfo` yapısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Alınacak `DebugPropertyInfo`structures sayısı.  
  
 `rgelt`  
 dışı @No__t_0 yapıların bir dizisi alındı.  
  
 `pceltFetched`  
 dışı Gerçekten alınan `DebugPropertyInfo` yapılarının sayısını döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Geçerli bir `HRESULT` döndürür, genellikle `S_OK`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ienumdebugpropertyınfo arabirimi](../../winscript/reference/ienumdebugpropertyinfo-interface.md)    
 [DebugPropertyInfo Yapısı](../../winscript/reference/debugpropertyinfo-structure.md)