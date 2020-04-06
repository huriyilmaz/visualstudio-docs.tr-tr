---
title: IDebugProcess3 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b423ee2cb95ad55296c452cfdc4b891ee4cd26a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723538"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Bu arabirim çalışan bir işlemi ve programlarını temsil eder. Bu [arabirim, IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimindeki çeşitli yöntemlerin yerine bulunur. Bu işlemdeki tüm programlar üzerinde denetim sağlar.

> [!NOTE]
> [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)ve [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) yöntemleri amortismana alınır ve artık kullanılmamalıdır. Bunun yerine `IDebugProcess3` arabirimde karşılık gelen yöntemleri kullanın.

## <a name="syntax"></a>Sözdizimi

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, programları grup olarak yönetmek için özel bir bağlantı noktası tedarikçisi tarafından uygulanır. Programlar bir grup olarak yönetildiğinde, bunların yürütülmesini denetleyebilir ve bir ifade değerlendiricisi için bir dil oluşturabilirsiniz. Bu arabirim bağlantı noktası tedarikçisi tarafından uygulanmalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, bu işlemde tanımlanan bir program grubuyla etkileşim kurmak için öncelikle oturum hata ayıklama yöneticisi (SDM) tarafından çağrılır.

 Bu arabirimi elde etmek için [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) arabiriminde [QueryInterface'i](/cpp/atl/queryinterface) arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugProcess2'den](../../../extensibility/debugger/reference/idebugprocess2.md)devralınan yöntemlere `IDebugProcess3` ek olarak aşağıdaki yöntemleri uygular.

|Yöntem|Açıklama|
|------------|-----------------|
|[Devam](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Bir işlemin yürütülmesini veya adımını atmaya devam ediyor.|
|[Yürütmek](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Bir işlemin yürütülmesibaşlar.|
|[Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)|İşlemde bir yönerge veya deyim ilerletilir.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|İşlemin hata ayıklama için başlatılmasının nedenini alır.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Hata ayıklama altyapısının uygun ifade değerlendiricisini yükleyebileceği şekilde barındırma dilini ayarlar.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Bu işlem için şu anda ayarlanmış dili alır.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Bu işlem için Edit ve Continue (ENC) devre dışı kılabilir.<br /><br /> Özel bir bağlantı noktası tedarikçisi bu yöntemi `E_NOTIMPL`uygulamaz (her zaman geri dönmelidir).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Bu işlem için ENC durumunu alın.<br /><br /> Özel bir bağlantı noktası tedarikçisi bu yöntemi `E_NOTIMPL`uygulamaz (her zaman geri dönmelidir).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Kullanılabilir hata ayıklama motorları için bir dizi benzersiz tanımlayıcı alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
