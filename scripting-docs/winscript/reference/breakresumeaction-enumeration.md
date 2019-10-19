---
title: BREAKRESUMEACTION numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2db56b66a544a31df3ac3a622568ecd29a33d12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572615"
---
# <a name="breakresumeaction-enumeration"></a>BREAKRESUMEACTION Listelemesi
Kesme noktasından devam etmenin yollarını açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|Uygulamayı iptal eder.|  
|BREAKRESUMEACTION_CONTINUE|Çalışmaya devam eder.|  
|BREAKRESUMEACTION_STEP_INTO|Bir yordamın adımları.|  
|BREAKRESUMEACTION_STEP_OVER|Yordam üzerindeki adımlar.|  
|BREAKRESUMEACTION_STEP_OUT|Geçerli yordamın adımları.|  
|BREAKRESUMEACTION_IGNORE|Durumla çalışmaya devam eder.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Sonraki belgeye adımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Hata Ayıklayıcı Sabitleri, Sabit Listeleri ve Yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)