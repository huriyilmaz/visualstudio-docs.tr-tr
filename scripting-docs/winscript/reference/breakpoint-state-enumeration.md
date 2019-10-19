---
title: BREAKPOINT_STATE numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKPOINT_STATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKPOINT_STATE enumeration
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c56a8b135a0aa9a4f8ddf91e146d4d64367bb2b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572639"
---
# <a name="breakpoint_state-enumeration"></a>BREAKPOINT_STATE Listelemesi
Bir kesme noktasının durumunu gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|BREAKPOINT_DELETED|Kesme noktası artık yok, ancak hala buna başvurular var.|  
|BREAKPOINT_DISABLED|Kesme noktası var, ancak devre dışı bırakıldı.|  
|BREAKPOINT_ENABLED|Kesme noktası var ve etkin.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Hata Ayıklayıcı Sabitleri, Sabit Listeleri ve Yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)