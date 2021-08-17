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
ms.openlocfilehash: a2e1b2961911a44e1eb23a3929146ddfe0a09bb1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057609"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Bu arabirim çalışan bir işlemi ve programlarını temsil eder. Bu arabirim, [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimindeki çeşitli yöntemlerin yerini alacak şekilde bulunur. İşlemdeki tüm programlar üzerinde denetim sağlar.

> [!NOTE]
> [Devam etme](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [yürütme](../../../extensibility/debugger/reference/idebugprogram2-execute.md)ve [adım](../../../extensibility/debugger/reference/idebugprogram2-step.md) yöntemleri kullanım dışıdır ve artık kullanılmamalıdır. Bunun yerine arabirim üzerinde ilgili yöntemleri kullanın `IDebugProcess3` .

## <a name="syntax"></a>Syntax

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, programları bir grup olarak yönetmek için özel bir bağlantı noktası sağlayıcısı tarafından uygulanır. Programlar bir grup olarak yönetildiğinde, yürütmesini denetleyebilir ve bir ifade değerlendirici için dil oluşturabilirsiniz. Bu arabirimin bağlantı noktası sağlayıcısı tarafından uygulanması gerekir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim öncelikle bu işlemde tanımlanan bir program grubuyla etkileşim kurmak için oturum hata ayıklama Yöneticisi (SDM) tarafından çağrılır.

 Bu arabirimi almak için bir [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) arabiriminde [QueryInterface](/cpp/atl/queryinterface) 'i çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)öğesinden devralınan yöntemlere ek olarak `IDebugProcess3` aşağıdaki yöntemleri uygular.

|Yöntem|Açıklama|
|------------|-----------------|
|[Devam et](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Bir işlemden yürütmeye devam eder.|
|[Yürütme](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Bir işlemin yürütülmesine başlar.|
|[Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)|İşlemler, işlemde bir yönerge veya ifade iletir.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|İşlemin hata ayıklama için başlatılmasının nedenini alır.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Hata ayıklama altyapısının uygun ifade değerlendiricisi 'nı yükleyebilmesi için barındırma dilini ayarlar.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Bu işlem için şu anda ayarlanmış olan dili alır.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Bu işlem için Düzenle ve devam et (ENC) işlemini devre dışı bırakır.<br /><br /> Özel bir bağlantı noktası sağlayıcısı bu yöntemi uygulamaz (her zaman döndürmelidir `E_NOTIMPL` ).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Bu işlem için ENC durumunu alın.<br /><br /> Özel bir bağlantı noktası sağlayıcısı bu yöntemi uygulamaz (her zaman döndürmelidir `E_NOTIMPL` ).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Kullanılabilir hata ayıklama motorları için benzersiz tanımlayıcıların dizisini alır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
