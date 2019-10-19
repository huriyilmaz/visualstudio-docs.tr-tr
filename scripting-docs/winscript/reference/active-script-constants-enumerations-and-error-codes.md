---
title: Etkin komut dosyası sabitleri, numaralandırmalar ve hata kodları | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e03bef99c2297d517aa5234db49820a2b9600ce7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572716"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Etkin Komut Dosyası Sabitleri, Numaralandırmaları ve Hata Kodları
Bu bölümde, Windows komut dosyası altyapılarında kullanılan numaralandırmalar ve hata kodları açıklanmaktadır.  
  
## <a name="constants"></a>Sabitler  
  
|Sabit|Açıklama|  
|--------------|-----------------|  
|[SCRIPTTHREADID Sabitleri](../../winscript/reference/scriptthreadid-constants.md)|İş parçacığı türünü belirtir.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE Özelliği](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Bekleyen başvurular varsa, betik altyapısının tam olarak işlevsel tutulması gerekip gerekmediğini belirtmek için kullanılır.|  
  
## <a name="enumerations"></a>Numaralandırmalar  
  
|Sabit Listesi|Açıklama|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE Sabit Listesi](../../winscript/reference/scriptgctype-enumeration.md)|Gerçekleştirilecek çöp toplamanın türü.|  
|[SCRIPTLANGUAGEVERSION Sabit Listesi](../../winscript/reference/scriptlanguageversion-enumeration.md)|Olası betik sürümlerini belirtir.|  
|[SCRIPTSTATE Sabit Listesi](../../winscript/reference/scriptstate-enumeration.md)|Bir betik altyapısının durumunu belirtir.|  
|||  
|[SCRIPTTHREADSTATE Sabit Listesi](../../winscript/reference/scriptthreadstate-enumeration.md)|Bir komut dosyası altyapısındaki iş parçacığının durumunu belirtir.|  
|[SCRIPTTRACEINFO Sabit Listesi](../../winscript/reference/scripttraceinfo-enumeration.md)|İzlenen betik olayını temsil eder. [IActiveScriptSiteTraceInfo:: SendScriptTraceInfo yönteminde](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)kullanılır.|  
|[SCRIPTUICHANDLING Sabit Listesi](../../winscript/reference/scriptuichandling-enumeration.md)|UI denetiminin işlenme şeklini temsil eder.|  
|[SCRIPTUICITEM Sabit Listesi](../../winscript/reference/scriptuicitem-enumeration.md)|UI öğesinin türünü temsil eder. [IActiveScriptSiteUIControl:: GetUIBehavior yönteminde](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)kullanılır.|  
  
## <a name="error-codes"></a>Hata Kodları  
  
|Hata Kodu|Açıklama|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE Hata Kodu](../../winscript/reference/script-e-propagate-error-code.md)|Bir betik hatası, arayana yayılmakta ve bu, farklı bir iş parçacığında olabilir.|  
|[SCRIPT_E_RECORDED Hata Kodu](../../winscript/reference/script-e-recorded-error-code.md)|Betik altyapısı ve konak arasında bir hata geçirildi.|  
|[SCRIPT_E_REPORTED Hata Kodu](../../winscript/reference/script-e-reported-error-code.md)|Betik altyapısı, konağa işlenmeyen bir özel durum bildirdi.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Arabirimleri](../../winscript/reference/active-script-interfaces.md)