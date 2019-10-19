---
title: 'Idağılım ROR:: GetSource | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetSource
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07c87585a92415f0b910210a56efa47e6f91417b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573095"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Hatayı oluşturan sınıf veya uygulama için dile bağlı programlı tanımlayıcıyı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstrSource`  
 dışı Bir programlı tanımlayıcı içeren dize, form `progname.objectname`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, özel durumun gerçekleştiği sınıfı veya uygulamayı belirlemede kullanılır. Programlı tanımlayıcı, çağırma sırasında sağlanan yerel ayar tanıtıcısı (LCıD) tarafından belirtilen dilde döndürülebilecek.  
  
> [!NOTE]
> Bu yöntem uygulanmadı.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDispError Arabirimi](../../winscript/reference/idisperror-interface.md)