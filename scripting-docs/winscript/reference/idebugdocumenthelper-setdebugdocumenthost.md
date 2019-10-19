---
title: 'Idebugbelgethelper:: Setdebugbelgethost | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDebugDocumentHost
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDebugDocumentHost
ms.assetid: b26a03c3-8a3f-47b0-b916-4c65d5500f10
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b32d14f3a7d65bee7bdb587a35dfe05bb06f5e1e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574651"
---
# <a name="idebugdocumenthelpersetdebugdocumenthost"></a>IDebugDocumentHelper::SetDebugDocumentHost
Bu belge için `IDebugDocumentHost` ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetDebugDocumentHost(  
   IDebugDocumentHost*  pddh  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pddh`  
 'ndaki Hata ayıklama belgesi Konağı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 arabirimi akıllı ana bilgisayar söz dizimi renklendirme, ertelenmiş metin getirme ve yeni oluşturulan belge bağlamları için nesneleri denetlemeye döndürme için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugbelgethelper arabirimini](../../winscript/reference/idebugdocumenthelper-interface.md)    
 [IDebugDocumentHost Arabirimi](../../winscript/reference/idebugdocumenthost-interface.md)