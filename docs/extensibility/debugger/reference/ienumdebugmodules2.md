---
title: IEnumDebugModules2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 612285aa4d5a249c0f922ccae88d98a7df83187b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716437"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Bu arabirim, modüllerin listesini listeler.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bir program için yüklenen modüllerin listesini temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio bu arayüzü elde etmek için [EnumModules'i](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) arar.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugModules2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Numaralandırma sırasında belirli sayıda modül alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Numaralandırma sırasında belirli sayıda modülü atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Modül sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio öncelikle **Modüller** penceresini güncelleştirmek için bu arabirimi kullanır.

 Visual Studio'da hata ayıklama amacıyla, bir program modül sınırlarını geçebilecek kod yönergelerinin mantıksal bir sırasıdır, bu nedenle tek bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimi için modül lerin listesine ihtiyaç vardır. Listedeki ilk modül genellikle ilişkili programın ilk giriş noktasını içerir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
