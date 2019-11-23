---
title: IDebugApplication::D ebugOutput | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.DebugOutput
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::DebugOutput
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d52acf0e4b32f0ced63b53a6b37ffe62f1d948e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575013"
---
# <a name="idebugapplicationdebugoutput"></a>IDebugApplication::DebugOutput
Belirtilen dizenin hata ayıklayıcı tümleşik geliştirme ortamı (IDE) tarafından görüntülenmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT DebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstr`  
 'ndaki Hata ayıklayıcıda görüntülenecek dize.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, dil altyapısının dile özgü hata ayıklama çıkışı desteğini uygulamasına olanak tanır. Dize genellikle hata ayıklayıcının çıkış penceresinde görüntülenir.  
  
 Bu yöntem `IApplicationDebugger::onDebugOutput` çağırmasına neden olur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication arabirimi](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)