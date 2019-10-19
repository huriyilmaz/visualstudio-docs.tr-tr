---
title: 'Ijsdebugprocess:: Createstackdenetçisi yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateStackWalker
apilocation:
- jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70f5d4885abba3d891526723d3ca1f174549c348
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573832"
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>IJsDebugProcess::CreateStackWalker Yöntemi
Yığın denetçisi için fabrika yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `threadId`  
 'ndaki İş parçacığı KIMLIĞI.  
  
 `ppStackWalker`  
 dışı Yeni yığın denetçisi nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 İş parçacığında JavaScript yoksa, E_JsDEBUG_UNKNOWN_THREAD döndürür. Bu yöntem yalnızca hedef işlem durdurulduğunda çağrılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugProcess Arabirimi](../../winscript/reference/ijsdebugprocess-interface.md)