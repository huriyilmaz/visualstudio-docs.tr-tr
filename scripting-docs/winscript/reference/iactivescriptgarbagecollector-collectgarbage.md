---
title: 'Iactivescriptgarbagecollector:: Collectçöp | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0539ed2cb3540cf33ceaaa15827c3ca08c156698
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573592"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
Etkin betik Konağı çöp toplamayı başlatmak için bu yöntemi çağırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `scriptgctype`  
 'ndaki Normal veya ayrıntılı atık toplama yapılıp yapılmayacağını belirten [Scrıptgctype numaralandırması](../../winscript/reference/scriptgctype-enumeration.md) .  
  
## <a name="return-value"></a>Dönüş Değeri  
 HRESULT döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptGarbageCollector Arabirimi](../../winscript/reference/iactivescriptgarbagecollector-interface.md)