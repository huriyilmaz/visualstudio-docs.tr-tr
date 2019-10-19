---
title: "IJsDebugDataTarget:: Readnullsonlandır' dize yöntemi | Microsoft Docs"
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67d6ee6c8dad81865767b0b944ef311fc0de0063
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572406"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString Yöntemi
Hedeften belirtilen sayıda karakteri okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki Okunacak adres.  
  
 `characterSize`  
 [in] dizedeki her karakterin boyutu  
  
 `maxCharacters`  
 'ndaki Okunacak maksimum karakter sayısı. maxCharacters makul olmalıdır. 128 MB 'tan fazla bellek için herhangi bir istek başarısız olur.  Dize maxCharacters 'den büyükse, sonuç dizesi maxCharacters sonra kesilir.  
  
 `pString`  
 dışı Hedeften okunan BSTR.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Kesilmişse S_FALSE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugDataTarget Arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)