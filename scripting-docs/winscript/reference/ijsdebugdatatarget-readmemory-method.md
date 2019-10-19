---
title: 'IJsDebugDataTarget:: ReadMemory yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84da36433cf3546b34d3e044bb113916c9798117
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572424"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory Yöntemi
Hedef işlemin belleğini okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki Hedef işlemin belleğinin okunacağı temel adres.  
  
 `flags`  
 'ndaki ReadMemory davranışını denetleyen bayraklar.  
  
 `pBuffer`  
 dışı Hedef işlemin adres alanından içeriği alan bir arabellek. Hatada Bu arabelleğin içeriği belirtilmemiş olur.  
  
 `size`  
 'ndaki İşlemden okunacak bayt sayısı.  
  
 `pBytesRead`  
 dışı Hedef işlemden okunan bayt sayısını gösterir. JsDebugAllowPartialRead açık ise, başarı durumunda bu değer her zaman giriş boyutuna eşit olur. JsDebugAllowPartialRead belirtilirse, başarı durumunda bu değer sıfırdan büyük olur.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Başarılı durumunda S_OK döndürür ve hata kodları herhangi bir hata için kullanılır. Adres geçerli değilse, E_JsDEBUG_INVALID_MEMORY_ADDRESS döndürür. Daha fazla bilgi için bkz. JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugDataTarget Arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)