---
description: Bu arabirim, bağlantı noktası tedarikçilerini numaralandırır.
title: IEnumDebugPortSuppliers2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 7620b528b90bf2a34894618ad186c4fdb8aa1c2e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034831"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Bu arabirim, bağlantı noktası tedarikçilerini numaralandırır.

## <a name="syntax"></a>Syntax

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Visual Studio, bağlantı noktası sağlayıcılarının listesini temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bağlantı noktası sağlayıcılarının bir listesini almak için [Trmportsuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) ' i çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugPortSuppliers2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Bir numaralandırma dizisinde belirtilen sayıda bağlantı noktası tedarikçilerini alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Bir numaralandırma dizisinde belirtilen sayıda bağlantı noktası tedarikçilerini atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Bir Numaralandırıcı içindeki bağlantı noktası sağlayıcılarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısının genellikle bu arabirimi alması gerekmez.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
