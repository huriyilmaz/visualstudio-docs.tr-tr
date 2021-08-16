---
description: Bu arabirim, modüllerin listesini numaralar.
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ef8e7e041ae63370ec285d02a720efada35aa4877b63319b4071527c2b2f94f0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377476"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Bu arabirim, modüllerin listesini numaralar.

## <a name="syntax"></a>Syntax

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bir program için yüklenen modüllerin listesini temsil etmek için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio [arabirimi almak için EnumModules'u](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) çağırıyor.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IEnumDebugModules2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Bir numaralama dizisinde belirtilen sayıda modülü alan.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Bir numaralama dizisinde belirtilen sayıda modülü atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Modül sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio modüller penceresini güncelleştirmek için öncelikle **bu arabirimi** kullanır.

 Visual Studio'da hata ayıklama amacıyla program, modül sınırlarını aşabilir ve bu nedenle tek [bir IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimi için modüllerin listesi gerekir. Listenin ilk modülü genellikle ilişkili programın ilk giriş noktasını içerir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
