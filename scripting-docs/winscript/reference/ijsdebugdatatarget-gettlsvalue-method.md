---
title: 'IJsDebugDataTarget:: GetTlsValue yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eecf9acf370656d5310a03d68ed74e10671a0bc2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577599"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue Metodu
Hata ayıklanan iş parçacığı için, belirtilen TLS dizini için iş parçacığı yerel depolaması (TLS) yuvasındaki değeri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `threadId`  
 'ndaki Okunacak hedef işlemde çalışan iş parçacığı.  
  
 `tlsIndex`  
 'ndaki Hedef işlem TlsAlloc işlevi olarak çağrıldığında ayrılan TLS dizini.  
  
 `pValue`  
 dışı İş parçacığının TLS yuvasında saklanan işaretçi boyutu değeri. Hedef iş parçacığı 32 bit ise, bu değerin üst 32-bit değeri sıfır olur.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Bir işlemin her iş parçacığının her TLS dizini için kendi yuvası vardır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugDataTarget Arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)