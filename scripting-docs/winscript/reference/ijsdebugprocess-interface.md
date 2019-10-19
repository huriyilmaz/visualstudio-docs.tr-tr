---
title: Ijsdebugprocess arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9200515b2c975fb1fa5b2acda7c261cb684d85b4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577340"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess Arabirimi
Hedef işlemi İnceleme ve denetleme yordamlarını sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="public-methods"></a>Ortak Yöntemler  
  
|Name|Açıklama|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint Metodu](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Kesme noktasını belirtilen belge konumunda ayarlar.|  
|[IJsDebugProcess::CreateStackWalker Metodu](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Yığın denetçisi için fabrika yöntemi.|  
|[IJsDebugProcess::PerformAsyncBreak Metodu](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Komut dosyası altyapısını kesme moduna geçirir ve bir sonraki betik yönergesinde kesintiye neden olur.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Betik Arabirimleri Başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)