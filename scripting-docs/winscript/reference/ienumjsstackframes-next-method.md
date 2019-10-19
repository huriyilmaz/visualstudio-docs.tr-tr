---
title: 'Ienumjsstackframes:: Next yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumJsStackFrames.Next
apilocation:
- jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c24ef399a7b12a1bffe8313c09be47d6a6a3b6c8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575526"
---
# <a name="ienumjsstackframesnext-method"></a>IEnumJsStackFrames::Next Yöntemi
Belirtilen kare sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cFrameCount`  
 'ndaki Alınacak çerçeve sayısı.  
  
 `pFrames`  
 dışı Çerçevelerin depolanacak dizi.  
  
 `pcFetched`  
 dışı Döndürülen çerçeve sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IEnumJsStackFrames Arabirimi](../../winscript/reference/ienumjsstackframes-interface.md)