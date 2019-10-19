---
title: 'IJsDebugDataTarget:: ReadBSTR yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadBSTR
apilocation:
- jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b125f58b4be279eac167b803ed6a683c1fb04ddf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572446"
---
# <a name="ijsdebugdatatargetreadbstr-method"></a>IJsDebugDataTarget::ReadBSTR Yöntemi
Hata ayıklama hedefinden bir BSTR okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki Okunacak adres.  
  
 `pString`  
 dışı Hata ayıklama hedefinden okunan BSTR.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Adres geçerli değilse, E_JsDEBUG_INVALID_MEMORY_ADDRESS döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugDataTarget Arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)