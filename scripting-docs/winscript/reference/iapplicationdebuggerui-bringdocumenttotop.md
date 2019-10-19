---
title: 'Iapplicationdebuggeruı:: BringDocumentToTop | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b51e7b588750fc72e61840c4748c006eea732c22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577803"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Belirtilen hata ayıklama belgesini içeren pencereyi hata ayıklayıcı Kullanıcı arabirimindeki en üst tarafına taşır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pddt`  
 'ndaki Hata ayıklayıcı Kullanıcı arabirimindeki en üste getirmek için belgede hata ayıklayın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_INVALIDARG`|Belge bilinmiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belirtilen hata ayıklama belgesini içeren pencereyi hata ayıklayıcı Kullanıcı arabirimindeki en üst tarafına taşır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IApplicationDebuggerUI Arabirimi](../../winscript/reference/iapplicationdebuggerui-interface.md)