---
title: IJsDebugStackWalker arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b06b8c1f9282c42599c798030440c30450ef6dd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574011"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker Arabirimi
Belirtilen iş parçacığı için bir yığın denetçisi temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="public-methods"></a>Ortak Yöntemler  
  
|Name|Açıklama|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext Metodu](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Sonraki kareyi alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Stack walseçiciler yalnızca hedef durdurulduğunda oluşturulabilir ve hedef işlem yeniden çalışmaya devam edildikten sonra geçersiz olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Betik Arabirimleri Başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)