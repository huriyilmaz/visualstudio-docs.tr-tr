---
title: SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8eb089efbf608b488465809f997ffc82fc2c2e3c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574404"
---
# <a name="script_error_debug_exception_thrown_kind-enumeration"></a>SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND Listelemesi
Oluşan özel durumun türünü gösterir. Bu numaralandırma, [IActiveScriptErrorDebug110:: GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) yöntemi tarafından kullanılır.  
  
> [!IMPORTANT]
> Bu sabitler PDM sürüm 11.0 ve daha sonraki sürümleri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Değer|Açıklama|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|Özel durum bir ilk şans özel durumudur.|  
|ETK_USER_UNHANDLED|0x00000001|Özel durum kullanıcı kodunda işlenmez.|  
|ETK_UNHANDLED|0x00000002|Özel durum kodda işlenmez.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptErrorDebug110 Arabirimi](../../winscript/reference/iactivescripterrordebug110-interface.md)