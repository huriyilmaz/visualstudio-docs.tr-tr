---
title: 'IActiveScriptSite:: GetDocVersionString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ecc592b6b7fcae5f516a3c1dd111c027e67b6dc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571124"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Geçerli belge sürümünü benzersiz bir şekilde tanımlayan, ana bilgisayar tanımlı bir dize alır. İlgili belge Windows betiği kapsamı dışında değiştiyse (bir HTML sayfasında Notepad ile düzenlenmekte olduğu gibi), betik altyapısı bunu kalıcı durumuyla birlikte kaydedebilir ve komut dosyasının bir sonraki yüklenilişinde yeniden derlemeyi zorunlu hale getirebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrVersionString`  
 dışı Ana bilgisayar tanımlı belge sürümü dizesinin adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa `S_OK` döndürür veya bu yöntem desteklenmiyorsa `E_NOTIMPL`.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 döndürülürse, komut dosyası altyapısı, betiğin belgeyle eşitlenmiş olduğunu varsaymalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)