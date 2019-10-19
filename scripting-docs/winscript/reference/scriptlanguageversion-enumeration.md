---
title: SCRIPTLANGUAGEVERSION numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 802a9f31cc7e3497c5e5fc54395d988552f75e84
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574370"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION Numaralandırması
Olası betik sürümlerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Sabit listesi değerleri  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Varsayılan sürüm. Tamsayı değeri 0 ' dır.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows Scripting sürüm 5,7. Tamsayı değeri 1 ' dir.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows Scripting sürüm 5,8. Tamsayı değeri 2 ' dir.|  
|SCRIPTLANGUAGEVERSION_MAX|En yüksek sürüm. Tamsayı değeri 255 ' dir.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Sabitleri, Sabit Listeleri ve Hata Kodları](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)