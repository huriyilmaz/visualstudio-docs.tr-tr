---
title: 'Ihata ayıklama Ghelper:: CreatePropertyBrowser | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99aa03470b49d02ee9f0ac1548bd1f8e27d0ab34
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562493"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
Bir VARYANTı sarmalayan bir özellik tarayıcısı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pvar`  
 'ndaki Gezinmek için kök değişken.  
  
 `bstrName`  
 'ndaki Köke verilecek ad.  
  
 `pdat`  
 'ndaki Üzerinde Özellik istemek için iş parçacığı. Bu parametre NULL ise, sıralama yapılmaz.  
  
 `ppdob`  
 dışı Özellik tarayıcısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir DEĞIŞKEN kaydırılan bir özellik tarayıcısı döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ihata ayıklama Ghelper:: CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [Ihata ayıklama Ghelper arabirimi](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty Arabirimi](../../winscript/reference/idebugproperty-interface.md)