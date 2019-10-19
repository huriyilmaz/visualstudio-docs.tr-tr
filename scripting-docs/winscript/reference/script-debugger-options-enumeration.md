---
title: SCRIPT_DEBUGGER_OPTIONS numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69d419732786442cda275bf85c74ab2b9d3e870
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574561"
---
# <a name="script_debugger_options-enumeration"></a>SCRIPT_DEBUGGER_OPTIONS Listelemesi
Ekli hata ayıklayıcı için uygulanan bir dizi seçenek ve/veya özelliği gösterir. [IDebugApplicationNode100:: GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) ve [IDebugApplicationNode100:: SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md) içinde kullanılır  
  
> [!IMPORTANT]
> Bu sabitler, PDM v 10.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Değer|Açıklama|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Hiçbir seçenek ayarlanmadı.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Bir özel durum oluştuğunda betik çalışma zamanının BREAKREASON_ERROR olaylarını oluşturması gerektiğini gösterir. Bu seçenek, hata ayıklayıcı tarafından ayarlanabilir veya `Debug.enableFirstChanceExceptions(<true&#124;false>)` aracılığıyla Kullanıcı kodu tarafından ayarlanabilir.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Ekli hata ayıklayıcının Web çalışanlarını desteklediğini gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Hata Ayıklayıcı Sabitleri, Sabit Listeleri ve Yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)