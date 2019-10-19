---
title: 'IJsDebugDataTarget:: WriteMemory yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cd23ad784e222f770dfd5c0e7c2d775aa55e42
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572418"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory Yöntemi
Hedef işlemin belleğini okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki Hedef işlemin belleğinin yazılacağı temel adres.  
  
 `pMemory`  
 'ndaki Belirtilen işlemin adres alanına yazılacak veriler.  
  
 `size`  
 'ndaki İşleme yazılacak bayt sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Veri aktarımı gerçekleşmeden önce, sistem, temel adresteki tüm verilere ve belirtilen boyuttaki belleğe yazma erişimi için erişilebildiğini doğrular ve erişilebilir değilse, işlev bir E_JsDEBUG_INVALID_MEMORY_ADDRESS hatası oluşturur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugDataTarget Arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)