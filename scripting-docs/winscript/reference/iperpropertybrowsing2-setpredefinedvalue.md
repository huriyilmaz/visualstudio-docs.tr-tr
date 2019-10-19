---
title: 'IPerPropertyBrowsing2:: Setpredefineddeğeri | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.SetPredefinedValue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::SetPredefinedValue
ms.assetid: 3aff5300-c5a4-4d9b-9d47-a75b64014ac4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a823a04082b7e19b2c1bc475c1070cc501789e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576243"
---
# <a name="iperpropertybrowsing2setpredefinedvalue"></a>IPerPropertyBrowsing2::SetPredefinedValue
@No__t_0 tarafından belirtilen özelliğin değerini ayarlar. Önceden tanımlanmış değer, belirteç ile tanımlanır `dwCookie.`  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetPredefinedValue(  
   DISPID  dispid,  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dispid`  
 'ndaki Önceden tanımlanmış bir değerin ayarlandığı özelliğin dağıtım tanıtıcısı.  
  
 `dwCookie`  
 'ndaki Ayarlanacak değeri tanımlayan belirteç.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Geçerli bir `HRESULT` döndürür, genellikle `S_OK`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IPerPropertyBrowsing2 Arabirimi 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)