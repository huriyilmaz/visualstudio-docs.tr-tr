---
title: 'IActiveScriptParse32:: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 8b5304d60aed8145e7a68d89b2c6d4386db0d745
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561654"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32:: InitNew
Komut dosyası altyapısını başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa `S_OK` döndürür veya başlatma sırasında bir hata oluştuysa `E_FAIL`.  
  
## <a name="remarks"></a>Açıklamalar  
 Betik altyapısının kullanılabilmesi için aşağıdaki yöntemlerden biri çağrılmalıdır: `IPersist*::Load`, `IPersist*::InitNew` veya `IActiveScriptParse32::InitNew`. Bu yöntemin semantiği `IPersistStreamInit::InitNew` aynıdır, bu yöntem komut dosyası altyapısından kendisini başlatmasını söyler. @No__t_0 veya `IActiveScriptParse32::InitNew` ve `IPersist*::Load` çağırmak için geçerli değildir, ne de `IPersist*::InitNew`, `IActiveScriptParse32::InitNew` veya `IPersist*::Load` birden çok kez çağırmak için geçerli değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)