---
title: 'Ihata ayıklama Ghelper:: CreatePropertyBrowserEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowserEx
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d64d9dad54e029dc4c76e8b7e6c7a3f0299b0cb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576495"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Bir VARYANTı sarmalayan ve DEĞIŞKEN değerlerinin veya VARTYPE türlerinin dizelere özel dönüştürülmesine izin veren bir özellik tarayıcısı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
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
  
 `pdf`  
 'ndaki Çeşitler için özel biçimlendirme sağlayan nesne.  
  
 `ppdob`  
 dışı Özellik tarayıcısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir DEĞIŞKEN sarmalayan ve DEĞIŞKEN değerlerinin veya VARTYPE türlerinin dizelere özel dönüştürülmesine izin veren bir özellik tarayıcısı döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ihata ayıklama Ghelper:: CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [Ihata ayıklama Ghelper arabirimi](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty Arabirimi](../../winscript/reference/idebugproperty-interface.md)