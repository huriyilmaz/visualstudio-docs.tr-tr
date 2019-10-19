---
title: 'Ijsenumdebugproperty:: Next yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsEnumDebugProperty.Next
apilocation:
- jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48c4506d783093395b2d88b7a71d56e3a89d24e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573985"
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next Yöntemi
Bu nesnenin özelliklerini okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `count`  
 'ndaki Okunacak özellik sayısı.  
  
 `ppDebugProperty`  
 dışı Özellik tarayıcısını temsil eden nesne.  
  
 `pActualCount`  
 dışı Nesnenin gerçek özellik sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsEnumDebugProperty Arabirimi](../../winscript/reference/ijsenumdebugproperty-interface.md)