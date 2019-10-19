---
title: SCRIPTTHREADSTATE numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc4ef840310c27ccbadce2ed4f632514b555ef98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575651"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE Numaralandırması
Bir komut dosyası altyapısındaki iş parçacığının durumunu belirtir. Bu numaralandırma, [IActiveScript:: GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) yöntemi tarafından kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Sabit listesi değerleri  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Belirtilen iş parçacığı şu anda betikleştirilmiş bir olaya hizmet vermiyor, hemen yürütülen betik metnini işliyor veya bir betik makrosu çalıştırmıyor.|  
|SCRIPTTHREADSTATE_RUNNING|Belirtilen iş parçacığı, komut dosyalı bir olaya etkin bir şekilde hizmet veriyor, hemen yürütülen betik metnini işliyor veya bir betik makrosu çalıştırmakta.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Sabitleri, Sabit Listeleri ve Hata Kodları](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)