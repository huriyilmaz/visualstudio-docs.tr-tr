---
title: 'Icriptnode:: GetCookie | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetCookie
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetCookie
ms.assetid: 007339c6-a73a-4147-b3c0-cc041e467ecd
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91428ca617c5c9e7b2bf88fc9c405f1d1610de1a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572225"
---
# <a name="iscriptnodegetcookie"></a>IScriptNode::GetCookie
Bir kod oluşturma yöntemi konak nesnesiyle ilişkilendirmek için kullanılan uygulama tanımlı bir değer döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetCookie(  
   DWORD              *pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdwCookie`  
 dışı @No__t_0 nesnesi için uygulama tanımlı tanımlama bilgisi değerini döndürür.  
  
 Bir Web sayfasını temsil eden bir `IScriptNode` nesnesi için 0 döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IScriptNode Arabirimi](../../winscript/reference/iscriptnode-interface.md)