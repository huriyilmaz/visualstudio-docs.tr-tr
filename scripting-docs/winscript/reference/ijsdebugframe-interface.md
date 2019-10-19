---
title: IJsDebugFrame arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91fe8cdf91b0c2121f4a1a7f111794b0fbe36669
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575111"
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame Arabirimi
Bir yığın çerçevesini temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="public-methods"></a>Ortak Yöntemler  
  
|Name|Açıklama|  
|----------|-----------------|  
|[IJsDebugFrame::Evaluate Metodu](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Bu yığın çerçevesinin bağlamında bir ifadeyi değerlendirin.|  
|[IJsDebugFrame::GetDebugProperty Metodu](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Bu yığın çerçevesi için bir özellik tarayıcısı döndürür.|  
|[IJsDebugFrame::GetDocumentPositionWithId Metodu](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Bu yığın çerçevesinin Kullanıcı düzeyi belge içindeki geçerli konumunu döndürür.|  
|[IJsDebugFrame::GetDocumentPositionWithName Metodu](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Bu yığın çerçevesinin Kullanıcı düzeyi belge içindeki geçerli konumunu döndürür.|  
|[IJsDebugFrame::GetName Metodu](../../winscript/reference/ijsdebugframe-getname-method.md)|Yığın çerçevesinin Kullanıcı dostu adını alır.|  
|[IJsDebugFrame::GetReturnAddress Metodu](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Çerçevenin ' Start ' (bkz. GetStackRange) adresine gönderilen dönüş adresini alır.|  
|[IJsDebugFrame::GetStackRange Metodu](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Mantıksal JavaScript yığın çerçevesinin mutlak adres aralığını döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Betik Arabirimleri Başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)