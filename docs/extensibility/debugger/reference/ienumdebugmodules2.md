---
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dfcd594ab8764cedb8cbe2ea312675f884ae2338
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957159"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Bu arabirim bir modül listesini numaralandırır.

## <a name="syntax"></a>Syntax

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bir program için yüklenen modüllerin listesini göstermek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio bu arabirimi edinmek için [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugModules2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Bir numaralandırma dizisinde belirtilen sayıda modülü alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Sabit Listesi dizisinde belirtilen sayıda modülü atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Oluşturulacak](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Modül sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio bu arabirimi öncelikle **modüller** penceresini güncelleştirmek için kullanır.

 Visual Studio 'da hata ayıklama amacıyla, bir program, modül sınırlarını çapraz bir şekilde, bu nedenle tek bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimine yönelik modüllerin bir listesi için ihtiyacı olan mantıksal bir kod yönergeleri dizisidir. Listedeki ilk modül genellikle ilişkili programın ilk giriş noktasını içerir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
