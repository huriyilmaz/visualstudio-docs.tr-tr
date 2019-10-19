---
title: 'Idebugbelgethelper:: SetTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetTextAttributes
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetTextAttributes
ms.assetid: 31657738-9e4c-436a-be61-23f4185d452e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cc5e5955652fd8b59d4c502e68d97a729ded141
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569465"
---
# <a name="idebugdocumenthelpersettextattributes"></a>IDebugDocumentHelper::SetTextAttributes
Metin aralığındaki öznitelikleri ayarlar ve bu metindeki diğer öznitelikleri geçersiz kılar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetTextAttributes(  
   ULONG              ulCharOffset,  
   ULONG              cChars,  
   SOURCE_TEXT_ATTR*  pstaTextAttr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ulCharOffset`  
 'ndaki Metin aralığının başlangıç konumu.  
  
 `cChars`  
 'ndaki Aralıktaki karakterlerin sayısı.  
  
 `pstaTextAttr`  
 'ndaki Metin aralığı için kaynak metin öznitelikleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Metin belgeye eklenmeden önce metin aralığında `SetTextAttributes` çağırmak hatadır. Belgeye metin eklemek için `AddDBCSText`, `AddUnicodeText` veya `AddDeferredText` yöntemlerini çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugbelgethelper arabirimini](../../winscript/reference/idebugdocumenthelper-interface.md)    
 [Idebugbelgethelper:: AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)    
 [Idebugbelgethelper:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [Idebugbelgethelper:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [SOURCE_TEXT_ATTR Sabit Listesi](../../winscript/reference/source-text-attr-enumeration.md)