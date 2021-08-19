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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089192"
---
# <a name="idebugengine2"></a>IDebugEngine2
Bu arabirim bir hata ayıklama altyapısını (DE) temsil eder. Bir hata ayıklama oturumunun çeşitli yönlerini yönetmek için kullanılır, özel durumları ayarlamak ve temizlemek için kesme noktaları oluşturma.

## <a name="syntax"></a>Syntax

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, programlarda hata ayıklamayı yönetmek için özel bir DE ile uygulanır. Bu arabirim, DE tarafından uygulanmalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, hata ayıklama oturumunu yönetmek için, özel durumları yönetme, kesme noktaları oluşturma ve DE tarafından gönderilen zaman uyumlu olaylara yanıt verme dahil olmak üzere oturum hata ayıklama Yöneticisi (SDM) tarafından çağrılır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugEngine2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|' DE hata ayıklamakta olan tüm programlar için bir Numaralandırıcı oluşturur.|
|[İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Bir programa DE ekler.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|De bekleyen bir kesme noktası oluşturur.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Bunun belirli bir özel durumu nasıl işleyeceğini belirtir.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Belirtilen özel durumu, artık hata ayıklama altyapısı tarafından işlenmemesi için kaldırır.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|IDE 'nin belirli bir çalışma zamanı mimarisi veya dili için ayarlamış olduğu özel durumların listesini kaldırır.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Aynı GUID değerini alır.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|, Belirtilen programın genellikle sonlandırıldığı ve aynı programın tüm başvurularını temizlemesini ve program yok etme olayı göndermesini DE bildirir.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Daha önce DE ' ın SDM 'ye gönderdiği zaman uyumlu bir hata ayıklama olayının alındığını ve işlendiğini göstermek için SDM tarafından çağırılır.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|DE yerel ayarını ayarlar.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Şu anda tarafından kullanılan kayıt defteri kökünü ayarlar.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Bir ölçüm ayarlar.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Bütün programlarının bu şekilde hata ayıklamakta olduğu tüm programlar, iş parçacıklarından birinin bir sonraki çalıştırılışında yürütmeyi durdurur.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
