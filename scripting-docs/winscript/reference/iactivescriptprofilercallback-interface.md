---
title: Iactivescriptprofilercallback arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ae520dcb36e00dfaba8702db6294a5a47484b0a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571720"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback Arabirimi
Olaylar gerçekleştiğinde bir profil oluşturucu nesnesine bildirimde bulunan betik altyapısı tarafından kullanılan yöntemleri sağlar. Bu arabirim, profil oluşturucu nesnesi tarafından uygulanır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Bir betik altyapısında profil oluşturma her başlatıldığında profil oluşturucu nesnesini başlatmak için çağırılır.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Bir betik altyapısında profil oluşturma durdurulduğunda profil oluşturucu nesnesini serbest bırakmak ve serbest bırakmak için çağırılır.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Betik altyapısının betiği derlediğini profil oluşturucu nesnesine bildirir.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Profil Oluşturucu nesnesine betik derlenirken komut dosyası altyapısının bir işlevle karşılaştığı bildirir.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Betik altyapısının Belge Nesne Modeli (DOM) çağrısı olmayan bir işlev çağrısını yürütmek üzere olduğunu profil oluşturucu nesnesine bildirir.|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Profil Oluşturucu nesnesine, betik altyapısının DOM 'a çağrı olmayan bir işlev çağrısını yürütmeyi bitirmekte olduğunu bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Belge Nesne Modeli (DOM) içindeki işlev çağrılarının bildirimi [ıactivescriptprofilercallback2 arabirimi](../../winscript/reference/iactivescriptprofilercallback2-interface.md)tarafından sağlanmaktadır.  
  
> [!NOTE]
> Bir betik çalışırken profil oluşturmayı başlatma ve durdurma özelliğini eklemek için aşağıdaki yöntemleri çağırın. Bu yöntemleri kullanarak, profil oluşturmayı başlattığınızda veya durdurduğunuzda [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] çalışıyorsa, tüm çağrı yığınını elde edebilirsiniz.  
> 
> - Profil oluşturmayı başlattığınız profil oluşturucuyu bildirmek için [ıactivescriptprofilercontrol2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) çağırın.  
>   - Profil oluşturucuyu yakında durdurulacağı profil oluşturucuya bildirmek için [ıactivescriptprofilercontrol2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Profil Oluşturucu Arabirimleri](../../winscript/reference/active-script-profiler-interfaces.md)