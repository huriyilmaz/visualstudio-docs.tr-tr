---
title: IEnumDebugThreads2 | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715097"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Bu arabirim, geçerli hata ayıklama oturumunda çalışan iş parçacıklarını ayıklar.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) bu arabirimi bir programdaki iş parçacıkları listesini temsil etmek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir işlemde çalışan tüm programlardaki tüm iş parçacıklarının listesini temsil eden bu arabirimi elde etmek için [EnumThreads'i](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) arayın. Bir programda çalışan iş parçacıklarının listesini temsil eden bu arabirimi elde etmek için [EnumThreads'i](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugThreads2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Numaralandırma dizisinde belirtilen sayıda iş parçacığı alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Numaralandırma sırasında belirli sayıda iş parçacığı atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Bir numaralandırmadaki iş parçacığı sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio genellikle **Threads** penceresini güncellemek için yanı sıra listenin ilk iş parçacığı elde [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)etmek için bu arayüzü elde, [çağırın,](../../../extensibility/debugger/reference/idebugprocess3-execute.md)Devam , ve [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Devam](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Yürütmek](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
