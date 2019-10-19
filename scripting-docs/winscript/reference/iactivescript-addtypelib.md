---
title: 'IActiveScript:: AddTypeLib | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 254a5133d42689020eaaae290a1016de4b848100
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575803"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Betik için ad alanına bir tür kitaplığı ekler. Bu, C/C++içindeki `#include` yönergesine benzerdir. Sınıf tanımları, `typedefs` ve adlandırılmış sabitler gibi bir dizi önceden tanımlanmış öğenin, komut dosyasının kullanabileceği çalışma zamanı ortamına eklenmesine izin verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `guidTypeLib`  
 'ndaki Eklenecek tür kitaplığının CLSID değeri.  
  
 `dwMaj`  
 'ndaki Ana sürüm numarası.  
  
 `dwMin`  
 'ndaki İkincil sürüm numarası.  
  
 `dwFlags`  
 'ndaki Seçenek bayrakları. Şunlar olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Tür kitaplığı, ana bilgisayar tarafından kullanılan bir ActiveX denetimini tanımlar.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersizdi.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı henüz yüklenmemiş veya başlatılmamış).|  
|`TYPE_E_CANTLOADLIBRARY`|Belirtilen tür kitaplığı yüklenemedi.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)