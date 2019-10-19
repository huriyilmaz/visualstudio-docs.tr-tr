---
title: 'Iactivescripterror:: GetSourcePosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ed307f988a3e5bf77ff978c466eda6e5dfee18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576891"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Komut dosyası altyapısı bir betik çalıştırırken bir hata oluştuğunda kaynak kodundaki konumu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdwSourceContext`  
 dışı Bağlamı tanımlayan bir tanımlama bilgisi alan bir değişkenin adresi. Bu parametrenin yorumu, konak uygulamasına bağlıdır.  
  
 `pulLineNumber`  
 dışı Hatanın gerçekleştiği kaynak dosyadaki satır numarasını alan bir değişkenin adresi.  
  
 `pichCharPosition`  
 dışı Hatanın gerçekleştiği satırdaki karakter konumunu alan bir değişkenin adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa `S_OK` döndürür veya konum alınalındıysa `E_FAIL`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)