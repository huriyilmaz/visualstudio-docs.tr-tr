---
title: 'Idağılım ROR:: GetHelpInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a84e57e97bb781ad3ea0be1ac6766fd94f6f5c30
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573127"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Mümkünse, hatayı açıklayan konunun yardım dosyasının yolunu ve bağlam KIMLIĞINI döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstrFileName`  
 dışı Yardım dosyasının tam yolunu içeren dize. Yardım dosyası yoksa veya bir hata oluşursa, dönüş değeri NULL olur.  
  
 `pdwContext`  
 dışı Hatanın yardım bağlamı KIMLIĞI. Yardım dosyası yoksa (`pbstrFileName` NULL ise), bu parametrenin bir anlamı yoktur.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Sağlayıcıya özgü bir hata oluştu.|  
|`E_INVALIDARG`|`pbstrFileName` veya `pdwContext` NULL.|  
|`E_OUTOFMEMORY`|Sağlayıcı, yardım dosyası yolunun döndürüleceği yeterli bellek ayıramadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, mümkünse hatayı açıklayan konunun yardım dosyasının yolunu ve bağlam KIMLIĞINI döndürür.  
  
> [!NOTE]
> Bu yöntem uygulanmadı.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDispError Arabirimi](../../winscript/reference/idisperror-interface.md)