---
description: Bir veya daha fazla modülün hata ayıklamasını kontrol eden tek bir hata ayıklama altyapısını (DE) temsil eder.
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f997a177164c66ac116db407db6e3edfcc571b0a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725805"
---
# <a name="idebugengine3"></a>IDebugEngine3
Bir veya daha fazla modülün hata ayıklamasını kontrol eden tek bir hata ayıklama altyapısını (DE) temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, JustMyCode durumunu etkinleştirmek için özel bir DE (sembolleri destekliyorsa) tarafından uygulanır. Sembolleri ve JustMyCode'ları destekliyorsa, bu arabirim DE tarafından uygulanarak gerçekleştirilmeli.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, sembollerin yük devredeceği konumlar için kullanıcı seçeneklerinin geçişi için oturum hata ayıklama yöneticisi (SDM) tarafından çağrılır. Ayrıca, örneği 2019'da altyapının GUID'lerini ayarlamak için de çağrılır (bu GUID, altyapı kaydı sırasındaki ölçümleri temel alır). SDM ayrıca JustMyCode durumunu ayarlamak ve hata ayıklayıcı tarafından bilinen tüm özel durumları belirtilen bir durum olarak ayarlamak için bu arabirimi de çağırtır.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 [Arabirimi, IDebugEngine2'den devralınan](../../../extensibility/debugger/reference/idebugengine2.md)yöntemlere ek `IDebugEngine3` olarak aşağıdaki yöntemleri gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|DE'nin hata ayıklama sembollerini aramak için kullanabileceği yolu veya yolları ayarlar.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Henüz sembolleri yüklenmemiş tüm modüller için sembolleri yükler.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|DE'ye JustMyCode bilgilerini söyler.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Ölçümlerden DE GUID'lerini ayarlar.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Şu anda bekleyen tüm özel durumları belirtilen bir durum olarak ayarlayın.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
