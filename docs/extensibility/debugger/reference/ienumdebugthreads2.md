---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbbe047c08f8e91264163d028c1b40d94cde97fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715097"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Bu arabirim, geçerli hata ayıklama oturumunda çalışan iş parçacıklarını numaralandırır.

## <a name="syntax"></a>Syntax

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bir programdaki iş parçacıklarının listesini göstermek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir işlemde çalışan tüm programlardaki tüm iş parçacıklarının listesini temsil eden bu arabirimi almak için [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) 'i çağırın. Bir programda çalışan iş parçacıklarının listesini temsil eden bu arabirimi edinmek için [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 'i çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugThreads2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Sabit Listesi dizisinde belirtilen sayıda iş parçacığı alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Bir numaralandırma dizisindeki belirtilen sayıda iş parçacığını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Geçerli numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Bir Numaralandırıcı içindeki iş parçacığı sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio genellikle bu arabirimi **Iş parçacıkları** penceresini güncelleştirmek ve [yürütme](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [devam et](../../../extensibility/debugger/reference/idebugprocess3-continue.md)ve [adımla](../../../extensibility/debugger/reference/idebugprocess3-step.md)çağırmak için listenin ilk iş parçacığını almak üzere edinir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Devam et](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Yürütme](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
