---
title: IDebugEngine2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e00751db052adeefee828829ec89309a3adba4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730857"
---
# <a name="idebugengine2"></a>IDebugEngine2
Bu arabirim hata ayıklama altyapıyı (DE) temsil eder. Hata ayıklama oturumunun çeşitli yönlerini yönetmek için, kesme noktaları oluşturmaktan özel durumları ayarlamaya ve temizlemeye kadar kullanılır.

## <a name="syntax"></a>Sözdizimi

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, programların hata ayıklama yönetmek için özel bir DE tarafından uygulanır. Bu arabirim DE tarafından uygulanmalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, özel durumları yönetme, kesme noktaları oluşturma ve DE tarafından gönderilen eşzamanlı olaylara yanıt verme de dahil olmak üzere hata ayıklama oturumunu yönetmek için oturum hata ayıklama yöneticisi (SDM) tarafından çağrılır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugEngine2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Bir DE tarafından debugged olan tüm programlar için bir sayısallaştırıcı oluşturur.|
|[İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Programa DE bağlar.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|DE'de bekleyen bir kesme noktası oluşturur.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|DE'nin belirli bir özel durumu nasıl ele alması gerektiğini belirtir.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Hata ayıklama altyapısı tarafından artık işlenmeyecek şekilde belirtilen özel durumu kaldırır.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|IDE'nin belirli bir çalışma zamanı mimarisi veya dili için belirlediği özel durumlar listesini kaldırır.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|DE'nin GUID'ini alır.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Bir DE'ye, belirtilen programın genellikle sonlandırıldığını ve DE'nin programa yapılan tüm başvuruları temizlemesi ve bir program yok etme olayı göndermesi gerektiğini bildirir.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|SDM tarafından, daha önce DE tarafından SDM'ye gönderilen eşzamanlı hata ayıklama olayının alındığını ve işlenmediğini belirtmek için çağrılır.|
|[Setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|DE'nin yerel kümesini ayarlar.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|DE tarafından kullanılmakta olan kayıt defteri kökünü ayarlar.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Bir metrik ayarlar.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Bu DE tarafından debubgged tüm programların bir sonraki iş parçacığı çalıştırmak için çalıştığında yürütme yi durdurmasını talep eder.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
