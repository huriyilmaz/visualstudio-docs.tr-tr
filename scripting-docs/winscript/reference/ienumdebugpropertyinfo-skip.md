---
title: 'Ienumdebugpropertyınfo:: Skip | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba634409fb051c37534c824efb20e33eda245e8a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574163"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Sabit Listesi dizisinde belirtilen sayıda `DebugPropertyInfo` yapısını atlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Atlanacak numaralandırma dizisindeki `DebugPropertyInfo` yapılarının sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Geçerli bir `HRESULT` döndürür, genellikle `S_OK`. @No__t_0 döndürür ve `celt`, Numaralandırıcının sonundaki öğe sayısından büyükse, geçerli öğe işaretçisini numaralandırmanın sonuna ayarlar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ienumdebugpropertyınfo arabirimi](../../winscript/reference/ienumdebugpropertyinfo-interface.md)    
 [DebugPropertyInfo Yapısı](../../winscript/reference/debugpropertyinfo-structure.md)