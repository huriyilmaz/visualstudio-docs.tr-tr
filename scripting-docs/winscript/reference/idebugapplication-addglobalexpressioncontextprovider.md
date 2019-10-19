---
title: 'IDebugApplication:: AddGlobalExpressionContextProvider | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.AddGlobalExpressionContextProvider
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddGlobalExpressionContextProvider
ms.assetid: 35db7124-6970-4e45-8f00-ecdf21e9f5cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 429e87def1e17a6abac92ce2d3538960659cfaeb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573469"
---
# <a name="idebugapplicationaddglobalexpressioncontextprovider"></a>IDebugApplication::AddGlobalExpressionContextProvider
Bu uygulamaya bir genel ifade bağlam sağlayıcısı ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT AddGlobalExpressionContextProvider(  
   IProvideExpressionContexts*  pdsfs,  
   DWORD_PTR*                   pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdsfs`  
 'ndaki Bu uygulamaya eklenecek genel bağlam sağlayıcısı.  
  
 `pdwCookie`  
 dışı Uygulamadan bu genel ifade bağlamı sağlayıcısını kaldırmak için kullanılan tanımlama bilgisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bu uygulamaya bir genel ifade bağlam sağlayıcısı ekler.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication arabirimi](../../winscript/reference/idebugapplication-interface.md)    
 [IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)