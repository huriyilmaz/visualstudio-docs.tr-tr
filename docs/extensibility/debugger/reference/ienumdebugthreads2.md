---
description: Bu arabirim, geçerli hata ayıklama oturumunda çalışan iş parçacıklarını numaralar.
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d37c20a1b78f33b05b73bbae4e2a91c3ae53c82c3fde975354738ebea083e221
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121261430"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Bu arabirim, geçerli hata ayıklama oturumunda çalışan iş parçacıklarını numaralar.

## <a name="syntax"></a>Syntax

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bir programda iş parçacıkları listesini temsil etmek için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir işlemde çalışan tüm programlarda tüm iş parçacıklarının listesini temsil eden bu arabirimi elde etmek için [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) çağrısı. Bir programda çalışan iş parçacıkları listesini temsil eden bu arabirimi elde etmek için [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) çağrısı.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IEnumDebugThreads2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Numaralama dizisinde belirtilen sayıda iş parçacığını alan.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Bir numaralama dizisinde belirtilen sayıda iş parçacığını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Geçerli numarayla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Numaralayıcıda iş parçacığı sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio genellikle Yürüt, Devam ve Adım  çağrısı yapmak için İş Parçacıkları penceresini güncelleştirmek ve listenin [](../../../extensibility/debugger/reference/idebugprocess3-execute.md)ilk [](../../../extensibility/debugger/reference/idebugprocess3-continue.md)iş parçacığını almak için bu arabirimi [elde eder.](../../../extensibility/debugger/reference/idebugprocess3-step.md)

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Devam et](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Yürütme](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
