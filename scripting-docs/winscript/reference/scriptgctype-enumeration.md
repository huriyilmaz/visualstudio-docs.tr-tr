---
title: SCRıPTGCTYPE numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fce16c756cf06c8cf01937114402832570a0cd3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574389"
---
# <a name="scriptgctype-enumeration"></a>SCRIPTGCTYPE Numaralandırması
Gerçekleştirilecek çöp toplamanın türü. [Iactivescriptgarbagecollector:: Collectçöp](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) yönteminde kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>Sabit listesi değerleri  
  
|||  
|-|-|  
|SCRIPTGCTYPE_NORMAL|Normal çöp toplama işlemi yapın. Tamsayı değeri 0 ' dır.|  
|SCRIPTGCTYPE_EXHAUSTIVE|Ayrıntılı atık toplama işlemi yapın. Tamsayı değeri 1 ' dir.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Sabitleri, Sabit Listeleri ve Hata Kodları](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)