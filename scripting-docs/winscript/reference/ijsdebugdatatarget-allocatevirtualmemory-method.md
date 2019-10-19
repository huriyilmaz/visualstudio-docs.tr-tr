---
title: 'IJsDebugDataTarget:: AllocateVirtualMemory yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30ad8a3eb277823271fbfb4c2e10364b8602775c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577637"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory Yöntemi
Hedef işlemin sanal adres alanı içindeki bir bellek bölgesini ayırır ve/veya kaydeder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki Belleğin yürütülmesi veya ayrılması gereken hedef işlem içindeki adres. Bu değer genellikle sıfırdır ve bu durumda sistem bir adres seçer.  
  
 `size`  
 'ndaki Ayrılacak bellek bölgesinin bayt cinsinden boyutu. Sistem otomatik olarak sonraki sayfa sınırına yuvarlar.  
  
 `allocationType`  
 'ndaki Gerçekleştirilecek ayırma türünü gösterir. Bu genellikle bir adımda &#124; ayırmayı ayrılmış ve KAYDEDEN bir MEM_COMMIT MEM_RESERVE (0x3000).  
  
 `pageProtection`  
 'ndaki Ayrılacak sayfa bölgesi için bellek koruması. Sayfalar yürütüliyorsa, bellek koruma sabitlerinden birini belirtebilirsiniz (örneğin, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 dışı Sayfaların ayrılmış bölgesinin temel adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 İşlevi, MEM_RESET kullanılmadığı takdirde sıfıra ayrılan belleği başlatır. Daha fazla bilgi için bkz. VirtualAlloc Win32 API.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugDataTarget Arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)