---
title: 'IJsDebugFrame:: GetDocumentPositionWithName yöntemi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithName
apilocation:
- jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b818ca4dc1ec4402973026668972507861c86f22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575119"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName Yöntemi
Bu yığın çerçevesinin Kullanıcı düzeyi belge içindeki geçerli konumunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pDocumentName`  
 dışı Statik betikler için, belge URL 'SI. Dinamik betikler için, betik türünü (örneğin, eval kodu, işlev kodu vs.) içeren bir ad döndürülür.  
  
 `pLine`  
 [out] belge içinde 1 tabanlı satır konumu.  
  
 `pColumn`  
 [out] belge içinde 1 tabanlı satır konumu.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IJsDebugFrame Arabirimi](../../winscript/reference/ijsdebugframe-interface.md)