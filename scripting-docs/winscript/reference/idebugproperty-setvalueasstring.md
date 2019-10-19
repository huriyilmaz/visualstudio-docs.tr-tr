---
title: 'Idebugproperty:: SetValueAsString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.SetValueAsString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::SetValueAsString
ms.assetid: cad8d7b2-19a5-4a29-9000-cafdecdc238b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67e12652056442d9ac162be7af3a0d9e2b61b82c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574936"
---
# <a name="idebugpropertysetvalueasstring"></a>IDebugProperty::SetValueAsString
Belirli bir dizeden bir özelliğin değerini ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetValueAsString (  
   LPCOLESTR pszValue,  
   UINTnRadix,  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszValue`  
 'ndaki Ayarlanacak değer.  
  
 `nRadix`  
 'ndaki Herhangi bir sayısal bilgiyi yorumlamak için kullanılan Radix.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Geçerli bir `HRESULT` döndürür, genellikle `S_OK`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugProperty Arabirimi](../../winscript/reference/idebugproperty-interface.md)