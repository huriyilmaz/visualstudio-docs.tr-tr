---
description: Bu arabirim, bağlantı noktası sağlayıcılarını numaralar.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725127"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Bu arabirim, bağlantı noktası sağlayıcılarını numaralar.

## <a name="syntax"></a>Syntax

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio, bağlantı noktası sağlayıcıları listesini temsil etmek için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bağlantı [noktası sağlayıcılarının listesini almak için EnumPortSuppliers'ı](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) arayın.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IEnumDebugPortSuppliers2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Bir numaralama dizisinde belirtilen sayıda bağlantı noktası sağlayıcıyı alan.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Bir numaralama dizisinde belirtilen sayıda bağlantı noktası sağlayıcıyı atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Numaralayıcıda bağlantı noktası sağlayıcılarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısının genellikle bu arabirimi elde etmek zorunda değildir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
