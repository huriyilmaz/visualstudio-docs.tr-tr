---
title: 'Idebugdocumentcontext:: Enumcodecontext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentContext.EnumCodeContexts
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentContext::EnumCodeContexts
ms.assetid: fb0aa64e-c458-4ef1-bcd8-5cebdc972549
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 790fd55493bfb24b32400bc73ae8a1799a279625
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573486"
---
# <a name="idebugdocumentcontextenumcodecontexts"></a>IDebugDocumentContext::EnumCodeContexts
Bu belge içeriğiyle ilişkili kod bağlamlarını numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumCodeContexts(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppescc`  
 dışı Bu belge bağlamı ile ilişkili kod bağlamları.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Belge bir içerme dosyası veya şablon olmadığı takdirde, genellikle yalnızca bir kod bağlamıyla ilişkilendirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugDocumentContext Arabirimi](../../winscript/reference/idebugdocumentcontext-interface.md)