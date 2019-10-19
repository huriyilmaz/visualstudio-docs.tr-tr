---
title: Iactivescriptprofilercontrol arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef127e3a4463d112b9ea424702fb2650c80cce7d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571592"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl Arabirimi
Profil oluşturmayı destekleyen betik altyapısı tarafından uygulanır. Genellikle, `IActiveScriptProfilerControl` uygulayan bir nesne [IActiveScript](../../winscript/reference/iactivescript.md) arabirimini de uygular. Bu durumda, nesne üzerinde `IUnknown::QueryInterface` metodunu çağırarak `IActiveScriptProfilerControl` arabirimine bir tanıtıcı elde edebilirsiniz. Arabirim, komut dosyası altyapısında profil oluşturmayı durdurmak ve başlatmak için gerekli yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Komut dosyası altyapısında profil oluşturmayı başlatır.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Betik altyapısında profil oluşturucu olay maskesini ayarlar.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Komut dosyası altyapısında profil oluşturmayı durduruyor.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Profil Oluşturucu Arabirimleri](../../winscript/reference/active-script-profiler-interfaces.md)