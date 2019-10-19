---
title: 'IActiveScriptParse:: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4817e103d7408124f35eb7dbaa16e955dd18f17
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573506"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Komut dosyası altyapısını başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa `S_OK` döndürür veya başlatma sırasında bir hata oluştuysa `E_FAIL`.  
  
## <a name="remarks"></a>Açıklamalar  
 Betik altyapısının kullanılabilmesi için aşağıdaki yöntemlerden biri çağrılmalıdır: `IPersist*::Load`, `IPersist*::InitNew` veya `IActiveScriptParse::InitNew`. Bu yöntemin semantiği `IPersistStreamInit::InitNew` aynıdır, bu yöntem komut dosyası altyapısından kendisini başlatmasını söyler. @No__t_0 veya `IActiveScriptParse::InitNew` ve `IPersist*::Load` çağırmak için geçerli değildir, ne de `IPersist*::InitNew`, `IActiveScriptParse::InitNew` veya `IPersist*::Load` birden çok kez çağırmak için geçerli değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)