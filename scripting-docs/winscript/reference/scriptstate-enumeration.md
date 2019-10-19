---
title: SCRIPTSTATE numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10dd6366e2d0783ec2e9d6bdadc001e9f999901e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575676"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE Numaralandırması
Bir betik altyapısının durumunu belirtir. Bu numaralandırma, [IActiveScript:: GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) ve [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) yöntemleri tarafından kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>Sabit listesi değerleri  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|Betik yeni oluşturuldu, ancak henüz bir `IPersist*` Interface ve [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) kullanılarak başlatılmamış.|  
|SCRIPTSTATE_INITIALIZED|Betik başlatılmış, ancak çalışmıyor (diğer nesnelere bağlanma veya olayları başlatma) veya herhangi bir kod yürütme. Kod, [IActiveScriptParse::P arseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) yöntemi çağırarak yürütme için sorgulanabilir.|  
|SCRIPTSTATE_STARTED|Betik kodu yürütebilir, ancak [IActiveScript:: Addnamedidıtem](../../winscript/reference/iactivescript-addnameditem.md) yöntemi tarafından eklenen nesnelerin olaylarını henüz bir daha etkilemez.|  
|SCRIPTSTATE_CONNECTED|Komut dosyası yüklendi ve olaylar için bağlandı.|  
|SCRIPTSTATE_DISCONNECTED|Betik yüklendi ve çalışma zamanı yürütme durumuna sahip, ancak bu olaylar için geçici olarak bağlantısı kesildi.|  
|SCRIPTSTATE_CLOSED|Betik kapatıldı. Betik altyapısı artık çalışmaz ve çoğu Yöntem için hataları döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Sabitleri, Sabit Listeleri ve Hata Kodları](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)