---
title: BREAKREASON numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f656bdf4e3bc85a014ff8d3011708799aa44bcd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572627"
---
# <a name="breakreason-enumeration"></a>BREAKREASON Listelemesi
Kesilmenin nedenini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|BREAKREASON_STEP|Dil altyapısı atlama modundadır.|  
|BREAKREASON_BREAKPOINT|Dil altyapısı açık bir kesme noktasıyla karşılaştı.|  
|BREAKREASON_DEBUGGER_BLOCK|Dil altyapısı, başka bir iş parçacığında bir hata ayıklayıcı bloğuna rastladı.|  
|BREAKREASON_HOST_INITIATED|Ana bilgisayar bir kesme istedi.|  
|BREAKREASON_LANGUAGE_INITIATED|Dil altyapısı bir kesme istedi.|  
|BREAKREASON_DEBUGGER_HALT|Hata ayıklayıcı IDE bir kesme istedi.|  
|BREAKREASON_ERROR|Bir yürütme hatası, kesintiye neden oldu.|  
|BREAKREASON_JIT|JıT hata ayıklama başlatması neden oldu.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Hata Ayıklayıcı Sabitleri, Sabit Listeleri ve Yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)