---
title: 'IJsDebugFrame:: GetStackRange Yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1ac3cbee9d16296632477f4128ec36370ab0d4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574035"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange Yöntemi
Mantıksal JavaScript yığın çerçevesinin mutlak adres aralığını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pStart`  
 dışı Çerçevenin en alt yığın işaretçisi.  
  
 `pEnd`  
 dışı Çerçevenin en üstteki yığın işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, birden fazla çalışma alanından toplanan araya eklemeli yığın izlemeleri piecing için faydalıdır. Başlangıç, bitiş yığını işaretçileri birden fazla fiziksel makine yığın çerçevesini kapsayabilir (yorumlanan JavaScript çalışma zamanı çerçeveleri için). yığın yüksek veya düşük adrese büyüdükçe > bitiş ' i başlatın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugFrame Arabirimi](../../winscript/reference/ijsdebugframe-interface.md)