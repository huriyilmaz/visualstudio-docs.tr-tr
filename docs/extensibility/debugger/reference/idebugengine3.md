---
title: IDebugEngine3 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7026156eac7f60e7435e32244c3cc03ae5f08e1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730648"
---
# <a name="idebugengine3"></a>IDebugEngine3
Bir veya daha fazla modülün hata ayıklamasını kontrol eden tek bir hata ayıklama motorını (DE) temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, JustMyCode durumunu etkinleştirmek için özel bir DE (sembolleri destekliyorsa) tarafından uygulanır. Bu arabirim, sembolleri ve JustMyCode'u destekliyorsa DE tarafından uygulanmalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, oturum hata ayıklama yöneticisi (SDM) tarafından, simgeleri yükleyecek konumlar için kullanıcı seçeneklerini aktarmak üzere çağrılır. Ayrıca, anında olduğunda motorun GUID'ini ayarlamak için de denir (bu GUID, motor kaydı sırasındaki ölçümlere dayanır). SDM ayrıca JustMyCode durumunu ayarlamak ve hata ayıklayıcı tarafından bilinen tüm özel durumları belirli bir duruma ayarlamak için bu arabirimi çağırır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugEngine2'den](../../../extensibility/debugger/reference/idebugengine2.md)devralınan yöntemlere ek `IDebugEngine3` olarak, arabirim aşağıdaki yöntemleri ortaya çıkarır.

|Yöntem|Açıklama|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|De'nin hata ayıklama sembollerini aramak için kullanacağı yolu veya yolları ayarlar.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Henüz sembollerini yüklememiş tüm modüllerin sembollerini yükler.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|De'ye JustMyCode bilgilerini anlatır.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|DE GUID'i ölçümlerden ayarlar.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Şu anda bekleyen tüm özel durumları belirli bir duruma ayarlayın.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
