---
description: Bu arabirim bir hata ayıklama altyapısını (DE) temsil eder.
title: IDebugEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: bacc450f29e950f5fd2d339244ad3715dead711a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725822"
---
# <a name="idebugengine2"></a>IDebugEngine2
Bu arabirim bir hata ayıklama altyapısını (DE) temsil eder. Kesme noktası oluşturmaktan özel durumları ayarlamaya ve temizlemeye kadar çeşitli hata ayıklama oturumunun çeşitli yönlerini yönetmek için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, programlarda hata ayıklamayı yönetmek için özel bir DE tarafından uygulanır. Bu arabirimin DE tarafından uygulanması gerekir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, özel durumları yönetme, kesme noktaları oluşturma ve DE tarafından gönderilen zaman uyumlu olaylara yanıt verme de dahil olmak üzere hata ayıklama oturumunu yönetmek için oturum hata ayıklama yöneticisi (SDM) tarafından çağrılır.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugEngine2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|DE tarafından hata ayıklaması yapılan tüm programlar için bir numaralayıcı oluşturur.|
|[İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Bir programa DE iliştirer.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|DE'de bekleyen bir kesme noktası oluşturur.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|DE'nin belirli bir özel durumu nasıl işlemesi gerektiğini belirtir.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Belirtilen özel durumu kaldırır, böylece artık hata ayıklama altyapısı tarafından işilmez.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|IDE'nin belirli bir çalışma zamanı mimarisi veya dili için ayarlayş olduğu özel durumların listesini kaldırır.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|DE GUID'lerini alır.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|DE'ye belirtilen programın atipik olarak sonlandırılmalarını ve DE'nin programa yapılan tüm başvuruları temizlemesi ve bir program yok etme olayı göndermesi gerektiğini bilgi verir.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Daha önce DE tarafından SDM'ye gönderilen zaman uyumlu bir hata ayıklama olayı alınarak işlendiğinden belirtmek için SDM tarafından çağrılır.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|DE'nin yerel ayar ayarlar.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|DE tarafından şu anda kullanmakta olan kayıt defteri kökünü ayarlar.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Bir ölçüm ayarlar.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|bu DE tarafından hata ayıklaması yapılan tüm programların, iş parçacıklarının bir sonraki çalıştırma girişiminde yürütmeyi durdurmasını sağlar.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
