---
title: 'IDebugApplicationNode100:: SetFilterForEventSink | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f85241bee7b35d40bf193a613a6fefda4265be6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574731"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Belirli bir [ıdebugapplicationnodeevents arabirim](../../winscript/reference/idebugapplicationnodeevents-interface.md) uygulamasındaki filtreyi ayarlar. Betik hata ayıklayıcıların derleyici tarafından oluşturulan alt uygulama düğümlerini filtrelemesine olanak tanır; böylece PDM, bunlar oluşturulduğunda veya kaldırıldığında olayları artık gönderemeyecektir. Varsayılan olarak, tüm düğümler gönderilir.  
  
> [!IMPORTANT]
> [IDebugApplicationNode100 ARABIRIMI](../../winscript/reference/idebugapplicationnode100-interface.md) PDM v 10.0 ve üzeri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwCookie`  
 Filtrenin tanımlama bilgisi.  
  
 `filter`  
 Filtre.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplicationNode100 Arabirimi](../../winscript/reference/idebugapplicationnode100-interface.md)