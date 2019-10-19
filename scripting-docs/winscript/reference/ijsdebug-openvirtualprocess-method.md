---
title: 'Ijsdebug:: OpenVirtualProcess yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3de39beb28a68ec3b8e0d76b17a7e914a464ecfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577740"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess Yöntemi
Yeni bir sanal işlem nesnesi oluşturmak için kullanılan Factory yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `processId`  
 'ndaki Hata ayıklayıcıyı iliştirilecek işlem kimliği.  
  
 `runtimeJsBaseAddress`  
 'ndaki JavaScript çalışma zamanının hedef işleme yüklendiği temel adres.  
  
 `pDataTarget`  
 'ndaki Hata ayıklayıcı işlemin durumunu sorgulamak için arabirim sağlandı.  
  
 `ppProcess`  
 dışı Yeni hata ayıklama işlemi nesnesi  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Jscript9diag ve JScript9 eşleşmezse E_JsDEBUG_MISMATCHED_RUNTIME döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebug Arabirimi](../../winscript/reference/ijsdebug-interface.md)