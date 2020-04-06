---
title: IEnumDebugPortSuppliers2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de0bfc5b387df9b347e4a58d97601a5e1e70f1a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715942"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Bu arayüz liman tedarikçilerini taklit eder.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio, liman tedarikçileri listesini temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Liman tedarikçilerinin listesini almak için [EnumPortSuppliers'i](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugPortSuppliers2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Numaralandırma sırasında belirli sayıda bağlantı noktası tedarikçisi alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Numaralandırma sırasında belirli sayıda bağlantı noktası tedarikçisiatlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Bir numaralandırma da liman tedarikçilerinin sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısının genellikle bu arabirimi elde etmesi gerekmez.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
