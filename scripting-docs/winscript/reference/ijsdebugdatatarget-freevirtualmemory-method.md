---
title: 'IJsDebugDataTarget:: FreeVirtualMemory yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 835302249e95c89625c07c6d1ef3d7cbaf2905e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577616"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory Yöntemi
Hedef işlemin sanal adres alanı içindeki bir bellek bölgesini serbest bırakır ve/veya kaydeder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki Belleğin serbest olması gereken hedef işlem içindeki adres.  
  
 `size`  
 'ndaki Yürütülecek bayt sayısı. Bir bellek bölgesini serbest bırakmak için bu değer sıfır olmalıdır.  
  
 `freeType`  
 'ndaki Gerçekleştirilecek serbest işlemin türünü gösterir. Bu genellikle, belirtilen sayfa bölgelerini serbest bırakır (MEM_RELEASE (0x8000). İşlemden sonra sayfalar boş durumdadır. MEM_DECOMMIT (0x4000), sayfaların serbest bırakılması gerekmeden çıkarılması yerine kullanılabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Daha fazla bilgi için bkz. VirtualFree Win32 API.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugDataTarget Arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)