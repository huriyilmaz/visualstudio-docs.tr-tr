---
title: 'Idebugproperty:: Geiddeınfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130d11c8ed6bb21210d129bb9aace779db3bd54b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562397"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Özelliği için genişletilmiş bilgileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cInfos`  
 'ndaki Genişletilmiş bilgi nesnelerinin sayısı.  
  
 `rgguidExtendedInfo`  
 'ndaki Aynı anda birden fazla genişletilmiş bilgi öğesinin alınabilmesi için bir dizi `GUID`s geçirilir.  
  
 `pExtendedInfo`  
 dışı Genişletilmiş özellik bilgilerini almak için kullanılabilecek `VARIANT`s dizisini döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Geçerli bir `HRESULT` döndürür, genellikle `S_OK`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim, bu nesne için genişletilmiş bilgileri alır. API yalnızca, `IDebugProperty::GetPropertyInfo` kullanımı tarafından alınmayan bilgileri alma amacıyla mevcuttur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugProperty Arabirimi](../../winscript/reference/idebugproperty-interface.md)