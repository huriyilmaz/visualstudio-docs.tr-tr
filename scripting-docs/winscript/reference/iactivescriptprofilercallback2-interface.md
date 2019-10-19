---
title: Iactivescriptprofilercallback2 arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f9616497192659df67feedfe16bd9ea0c5e3b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577308"
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2 Arabirimi
Belge Nesne Modeli (DOM) olayları gerçekleştiğinde bir profil oluşturucu nesnesine bildirimde bulunan komut dosyası altyapısı tarafından kullanılan yöntemleri sağlar. Bu arabirim, profil oluşturucu nesnesi tarafından uygulanır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Profil Oluşturucu nesnesine betik altyapısının bir DOM işlev çağrısı çalıştıracağınızı bildirir.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Profil Oluşturucu nesnesine betik altyapısının bir DOM işlev çağrısını çalıştırmayı tamamladığını bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 arabirimi ilk olarak Internet Explorer 9 ' da kullanıma sunuldu.  
  
 DOM 'a çağrı olmayan işlev çağrılarının bildirimi [ıactivescriptprofilercallback arabirimi](../../winscript/reference/iactivescriptprofilercallback-interface.md)tarafından sağlanır.  
  
> [!NOTE]
> Bir betik çalışırken profil oluşturmayı başlatma ve durdurma özelliğini eklemek için aşağıdaki yöntemleri çağırın. Bu yöntemleri kullanarak, profil oluşturmayı başlattığınızda veya durdurduğunuzda [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] çalışıyorsa, tüm çağrı yığınını elde edebilirsiniz.  
> 
> - Profil oluşturmayı başlattığınız profil oluşturucuyu bildirmek için [ıactivescriptprofilercontrol2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) çağırın.  
>   - Profil oluşturucuyu yakında durdurulacağı profil oluşturucuya bildirmek için [ıactivescriptprofilercontrol2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Profil Oluşturucu Arabirimleri](../../winscript/reference/active-script-profiler-interfaces.md)