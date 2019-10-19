---
title: 'IPerPropertyBrowsing2:: GetPredefinedStrings | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55ade724dd9ee5d59feb9d04c5b525ca839a9cec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576769"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Çağıranın, bu özellik için olası değerleri temsil eden, sayılı bir dizi dize işaretçileriyle bir liste kutusu doldurmasına izin verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dispid`  
 'ndaki Çağıranın dize listesi istediği özelliğin dağıtım tanıtıcısı.  
  
 `pCaStrings`  
 dışı Bir dizi dize işaretçisi dizisinin öğe sayısını ve adresini içeren, çağıran ayrılmış, sayılan dizi yapısına yönelik işaretçi. Yöntem başarısız olursa, bellek ayrılmazsa ve yapının içeriği tanımsızdır.  
  
 `pCaCookies`  
 dışı Bir DWORD 'in yöntem tarafından ayrılan dizisinin öğe sayısını ve adresini içeren, çağıran, sayılan dizi yapısına yönelik işaretçi. Yöntem başarısız olursa, bellek ayrılmazsa ve yapının içeriği tanımsızdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Geçerli bir `HRESULT` döndürür, genellikle `S_OK`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IPerPropertyBrowsing2 Arabirimi 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)