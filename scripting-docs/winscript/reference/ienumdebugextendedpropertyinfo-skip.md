---
title: 'Ienumdebugextendedpropertyınfo:: Skip | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Skip
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e5c187f3484154a2758b67300c98d4cb9fc9023
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574237"
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
Sabit Listesi dizisinde belirtilen sayıda `ExtendedDebugPropertyInfo` yapısını atlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Atlanacak numaralandırma dizisindeki `ExtendedDebugPropertyInfo` yapılarının sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Geçerli bir `HRESULT`döndürür, genellikle `S_OK`. `S_FALSE` döndürür ve `celt`, Numaralandırıcının sonundaki öğe sayısından büyükse, geçerli öğe işaretçisini numaralandırmanın sonuna ayarlar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ienumdebugextendedpropertyınfo arabirimi](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo Yapısı](../../winscript/reference/extendeddebugpropertyinfo-structure.md)