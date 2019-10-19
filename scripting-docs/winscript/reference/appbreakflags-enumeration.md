---
title: APPBREAKFLAGS numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de6efbc20843fcaa73965334c18cf0e5c2a0abab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572667"
---
# <a name="appbreakflags-enumeration"></a>APPBREAKFLAGS Numaralandırması
Uygulamalar ve iş parçacıkları için geçerli hata ayıklama durumunu gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Değer|Açıklama|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Dil altyapısı, BREAKREASON_DEBUGGER_BLOCK ile tüm iş parçacıkları üzerinde hemen kesintiye uğramalıdır.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Dil altyapısının doğrudan BREAKREASON_DEBUGGER_HALT ile kesintiye uğramalıdır.|  
|APPBREAKFLAG_STEP|0x00010000|Dil altyapısının, BREAKREASON_STEP ile Adımlama iş parçacığında hemen kesintiye uğramalıdır.|  
|APPBREAKFLAG_NESTED|0x00020000|Uygulama, bir kesme noktasında iç içe Yürütmeyle yapılır.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Hata ayıklayıcı kaynak düzeyinde adımlanıyor.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Hata ayıklayıcı, bayt kodu düzeyinde adımlanıyor.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Hata ayıklayıcı makine düzeyinde adımlanıyor.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Adım türlerini düzenleme için maske.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Bir kesme noktası devam ediyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı bayraklar, dil altyapılarının bir sonraki fırsatta kesilmesini gerektiğini belirtir, ancak diğer bayraklar hata ayıklayıcının atlama modunu belirtir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin betik hata ayıklayıcısı sabitleri, numaralandırmalar ve yapılar](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)    
 [BREAKREASON Sabit Listesi](../../winscript/reference/breakreason-enumeration.md)