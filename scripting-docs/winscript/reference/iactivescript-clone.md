---
title: 'IActiveScript:: Clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbaad29cb31af26a0f26a1c679a900192fc77041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575794"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Geçerli komut dosyası altyapısını (yani geçerli yürütme durumu) klonlar, geçerli iş parçacığında hiç sitesi olmayan yüklü bir betik altyapısı döndürüyor. Bu yeni betik altyapısının özellikleri, başlangıç durumuna geri geçirilse de orijinal komut dosyası altyapısının bulunduğu özelliklerle aynı olacaktır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppscript`  
 dışı Kopyalanmış betik altyapısının [IActiveScript](../../winscript/reference/iactivescript.md) arabirimine bir işaretçi alan bir değişkenin adresi. Konak, başlatılmış durumda ve bu nedenle kullanılabilir olacak şekilde, yeni komut dosyası altyapısında bir site oluşturmalı ve [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) yöntemini çağırmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_NOTIMPL`|Bu yöntem desteklenmiyor.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı henüz yüklenmemiş veya başlatılmamış).|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 yöntemi `IPersist*::Save`, `CoCreateInstance` ve `IPersist*::Load` en iyi duruma getirmedir. bu nedenle, yeni betik altyapısının durumu özgün komut dosyası altyapısının durumu kaydedilip yeni bir komut dosyası altyapısına yüklenip yüklenilmiş gibi olmalıdır. Adlandırılmış öğeler kopyalanmış betik altyapısında yinelenir, ancak her öğe için belirli nesne işaretçileri unutulur ve [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) yöntemiyle elde edilir. Bu, iş parçacığı başına giriş noktaları (bir Grup modeli) ile aynı nesne modelinin kullanılmasını sağlar.  
  
 Bu yöntem, aynı betiğin birden fazla örneğini çalıştırabilirler çok iş parçacıklı sunucu konakları için kullanılır. Betik altyapısı `E_NOTIMPL` döndürebilir, bu durumda ana bilgisayar kalıcı durumu çoğaltıp ve bir `IPersist*` arabirimiyle bir komut dosyası altyapısının yeni bir örneğini oluşturarak aynı sonucu elde edebilir.  
  
 Bu yöntem, temel olmayan iş parçacıklarından, nesneleri barındırmak için temel olmayan bir belirtme çizgisine veya [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) arabirimine yol açmadan çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)