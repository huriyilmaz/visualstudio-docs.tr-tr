---
title: JsDebugReadMemoryFlags numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1757678f20a01221ae46e1535d3190cd463d724
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571703"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>JsDebugReadMemoryFlags Listelemesi
Bellek okunduğu sıradaki davranışı belirten bayraklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="values"></a>Değerler  
  
|Name|Açıklama|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Yalnızca bellek okuma işleminin başarılı olması durumunda çağıranın okuma işleminin başarılı olmasını istediğini belirtir. Bu ayarlandıysa, yalnızca ' Address ' geçersizse bir E_JsDEBUG_INVALID_MEMORY_ADDRESS hatası çıkarılır. Bu bayrak açık ise, istenen belleğin herhangi bir bölümü okunamaz olursa bir E_JsDEBUG_INVALID_MEMORY_ADDRESS hatası oluşur.|  
|`None`|Çağıranın ReadMemory için varsayılan davranışı istediğini belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Betik Arabirimleri Başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)