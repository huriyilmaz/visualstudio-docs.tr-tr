---
title: 'Iapplicationdebuggeruı:: BringDocumentContextToTop | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentContextToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8648a4377e901908df20cdb5f413ee73ede5c1a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577805"
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Verilen belge bağlamını içeren pencereyi hata ayıklayıcı Kullanıcı arabirimindeki en üstüne getirir ve pencereyi bağlama göre kaydırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pddc`  
 'ndaki Hata ayıklayıcı Kullanıcı arabirimindeki en üste getirmek için belge bağlamı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_INVALIDARG`|@No__t_0 tarafından belirtilen bağlam bilinmiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belirtilen belge bağlamını içeren pencereyi hata ayıklayıcı Kullanıcı arabirimindeki üst öğesine getirir ve pencereyi bağlama göre kaydırır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IApplicationDebuggerUI Arabirimi](../../winscript/reference/iapplicationdebuggerui-interface.md)