---
title: 'IActiveScript:: GetScriptDispatch | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba53f2eccde18bd5b2d9c609ea680b50cb7261c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575756"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Şu anda çalışan betikle ilişkili Yöntemler ve özellikler için `IDispatch` arabirimini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrItemName`  
 'ndaki Çağıranın ilişkili dağıtım nesnesine ihtiyacı olan öğenin adını içeren bir arabelleğin adresi. Bu parametre `NULL` ise, dağıtım nesnesi, komut dosyası tarafından tanımlanan tüm genel yöntemleri ve özellikleri içerir. @No__t_0 arabirimi ve ilişkili `ITypeInfo` arabirimi aracılığıyla, ana bilgisayar betik yöntemlerini çağırabilir veya betik değişkenlerini görüntüleyebilir ve değiştirebilir.  
  
 `ppdisp`  
 dışı Betiğin genel yöntemleriyle ve özellikleriyle ilişkili nesneye bir işaretçi alan bir değişkenin adresi. Betik altyapısı böyle bir nesneyi desteklemiyorsa `NULL` döndürülür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersizdi.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı henüz yüklenmemiş veya başlatılmamış).|  
|`S_FALSE`|Betik altyapısı bir dağıtım nesnesini desteklemez; `ppdisp` parametresi NULL olarak ayarlandı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemler ve Özellikler [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) arabirimi çağırarak eklenebildiğinden, bu yöntemin döndürdüğü `IDispatch` arabirimi yeni yöntemleri ve özellikleri dinamik olarak destekleyebilir. Benzer şekilde, yöntem ve Özellikler eklendiğinde `IDispatch::GetTypeInfo` yöntemi yeni, benzersiz bir `ITypeInfo` arabirimini döndürmelidir. Ancak, bu dil altyapısının `IDispatch` arabirimini döndürülen herhangi bir önceki `ITypeInfo` arabirimiyle uyumsuz bir şekilde değiştirmemelidir. Bu, örneğin, dispIDs 'nin hiçbir şekilde yeniden kullanılmamasını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)