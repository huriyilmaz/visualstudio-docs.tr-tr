---
title: 'IDebugApplication:: AddStackFrameSniffer | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.AddStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddStackFrameSniffer
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a461c24b6f62f1e0ece88915e097faf0c59f15e7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575027"
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
Bu uygulamaya bir yığın çerçeve Numaralandırıcı sağlayıcısı ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdsfs`  
 'ndaki Bu uygulamaya eklenecek yığın çerçevesi Numaralandırıcı sağlayıcısı.  
  
 `pdwCookie`  
 dışı Uygulamadan bu yığın çerçeve Numaralandırıcı sağlayıcısını kaldırmak için kullanılan tanımlama bilgisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Dil motorları, yığın çerçevelerini hata ayıklayıcıya göstermek için genellikle bu yöntemi çağırmakla birlikte, diğer varlıkların yığın çerçevelerini kullanıma sunmasına olanak tanır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication arabirimi](../../winscript/reference/idebugapplication-interface.md)    
 [IDebugApplication:: RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)    
 [IDebugStackFrameSniffer Arabirimi](../../winscript/reference/idebugstackframesniffer-interface.md)