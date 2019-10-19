---
title: 'IActiveScript:: GetScriptSite | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 567c7b5c1ead5388e6ec9c67d6ab6f9f580adf20
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575740"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Windows komut dosyası altyapısı ile ilişkili site nesnesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `iid`  
 'ndaki İstenen arabirimin tanımlayıcısı.  
  
 `ppvSiteObject`  
 dışı Konağın site nesnesine arabirim işaretçisini alan konumun adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersizdi.|  
|`E_NOINTERFACE`|Belirtilen arabirim desteklenmiyor.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`S_FALSE`|Hiçbir site ayarlanmadı; `ppvSiteObject` parametresi `NULL` olarak ayarlanır.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)