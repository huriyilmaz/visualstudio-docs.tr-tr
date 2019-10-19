---
title: 'IActiveScriptSite:: Getlcıd | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 913ca23ac687fdd080a778afb1dcba2e4dcdd6b8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570744"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Konağın Kullanıcı arabirimiyle ilişkili yerel ayar tanımlayıcısını alır. Betik altyapısı, altyapı tarafından oluşturulan hata dizelerinin ve diğer kullanıcı arabirimi öğelerinin uygun dilde göründüğünden emin olmak için tanımlayıcıyı kullanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `plcid`  
 dışı Betik altyapısı tarafından görüntülenen kullanıcı arabirimi öğeleri için yerel ayar tanıtıcısını alan bir değişkenin adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_NOTIMPL`|Bu yöntem uygulanmadı. Sistem tanımlı yerel ayarı kullanın.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem `E_NOTIMPL` döndürürse, sistem tanımlı yerel ayar tanımlayıcısı kullanılmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)