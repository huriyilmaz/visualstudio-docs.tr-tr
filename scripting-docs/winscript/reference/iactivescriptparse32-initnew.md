---
title: 'IActiveScriptParse32:: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 887e4ce44662cc591fee64f5e0549edcdcbc14af
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835712"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Komut dosyası altyapısını başlatır.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`Başarılı olursa veya `E_FAIL` başlatma sırasında bir hata oluştuysa döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Betik altyapısının kullanılabilmesi için aşağıdaki yöntemlerden biri çağrılmalıdır: `IPersist*::Load` , `IPersist*::InitNew` , veya `IActiveScriptParse32::InitNew` . Bu yöntemin semantiği ile aynıdır `IPersistStreamInit::InitNew` ; Bu yöntem, komut dosyası altyapısının kendisini başlatmasını söyler. Ya da ile çağırmak için geçerli değildir, ya da veya birden `IPersist*::InitNew` `IActiveScriptParse32::InitNew` `IPersist*::Load` çok kez çağırmak için geçerli değildir `IPersist*::InitNew` `IActiveScriptParse32::InitNew` `IPersist*::Load` .  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)