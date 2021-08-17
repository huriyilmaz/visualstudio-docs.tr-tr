---
description: Bu arabirim çalışan bir işlemi ve programlarını temsil eder.
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 16292416d3d915bb5093de292a491ba91a172d42522fdd78a02f9377182480b9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338949"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Bu arabirim çalışan bir işlemi ve programlarını temsil eder. Bu [arabirim, IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabiriminde çeşitli yöntemlerin yerini almaktadır. Süreçteki tüm programlar üzerinde denetim sağlar.

> [!NOTE]
> [Devam](../../../extensibility/debugger/reference/idebugprogram2-continue.md) [edin,](../../../extensibility/debugger/reference/idebugprogram2-execute.md)Yürüt [ve](../../../extensibility/debugger/reference/idebugprogram2-step.md) Adım yöntemleri kullanım dışıdır ve artık kullanılmamalı. Bunun yerine arabirimde karşılık gelen `IDebugProcess3` yöntemleri kullanın.

## <a name="syntax"></a>Syntax

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, programları grup olarak yönetmek için özel bir bağlantı noktası sağlayıcı tarafından uygulanır. Programlar bir grup olarak yönetiliyorsa, bunların yürütülmesini kontrol etmek ve bir ifade değerlendiricisi için bir dil kurmak. Bu arabirimin bağlantı noktası sağlayıcı tarafından uygulanması gerekir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, bu işlemde tanımlanan bir program grubuyla etkileşim kurmak için öncelikle oturum hata ayıklama yöneticisi (SDM) tarafından çağrılır.

 Bu arabirimi elde etmek için [IDebugProcess2 arabiriminde](../../../extensibility/debugger/reference/idebugprocess2.md) [QueryInterface](/cpp/atl/queryinterface) çağrısında bulundunuz.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 [IDebugProcess2'den](../../../extensibility/debugger/reference/idebugprocess2.md)devralınan yöntemlere ek `IDebugProcess3` olarak aşağıdaki yöntemleri de kullanır.

|Yöntem|Açıklama|
|------------|-----------------|
|[Devam et](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Bir işlem yürütmeye veya adım adım işlemeye devam eder.|
|[Yürütme](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Bir sürecin yürütülmesini başlar.|
|[Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Süreç içinde bir yönerge veya deyimi iletme adımları.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Hata ayıklama için sürecin başlat nedenini alır.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Hata ayıklama altyapısının uygun ifade değerlendiriciyi yükleyemediklerinden barındırma dilini ayarlar.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Bu işlem için ayarlanmış olan dili alın.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Bu işlem için Düzenle ve Devam 'ı (ENC) devre dışı eder.<br /><br /> Özel bir bağlantı noktası sağlayıcı bu yöntemi uygulamaz (her zaman geri `E_NOTIMPL` dönmeli).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Bu işlem için ENC durumunu al.<br /><br /> Özel bir bağlantı noktası sağlayıcı bu yöntemi uygulamaz (her zaman geri `E_NOTIMPL` dönmeli).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Kullanılabilir hata ayıklama altyapıları için bir dizi benzersiz tanımlayıcıyı döndürür.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
