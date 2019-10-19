---
title: 'IActiveScript:: SetScriptSite | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 063dcc7b580334bff9780e9c209b621ef7e25656
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575324"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Konak tarafından sunulan [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Interface sitesinin betik motoruna bilgilendirir. Diğer herhangi bir [IActiveScript](../../winscript/reference/iactivescript.md) arabirimi yöntemi kullanılmadan önce bu yöntemi çağırın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pScriptSite`  
 'ndaki Betik altyapısının bu örneğiyle ilişkilendirilecek konak tarafından sağlanan betik sitesinin adresi. Site, bu komut dosyası altyapısı örneğine benzersiz olarak atanmalıdır; diğer betik altyapılarıyla paylaştırılamaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_FAIL`|Belirtilmeyen bir hata oluştu; betik altyapısı, siteyi başlatmayı tamamlayamadı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersizdi.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, bir site zaten ayarlanmış).|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)