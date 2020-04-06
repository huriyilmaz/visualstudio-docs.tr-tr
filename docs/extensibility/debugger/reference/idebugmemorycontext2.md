---
title: IDebugMemoryContext2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727432"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Bu arabirim, debugged programı çalıştıran makinenin adres alanında bir konumu temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) bellekteki bir adresi temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) veya [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) için yapılan bir çağrı bu arabirimi döndürür. Ayrıca, uygun aritmetik işlem uygulandıktan sonra [Ekle](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) ve [Çıkarma](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) çağrıları bu arabirimin yeni kopyalarını döndürür.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugMemoryContext2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Bu bağlam için kullanıcı tarafından görüntülenebilir adı alır.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Bu bağlamı açıklayan bilgileri alır.|
|[Ekle](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Yeni bir bağlam oluşturmak için geçerli bağlamın adresine belirli bir değer ekler.|
|[Çıkarmak](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Yeni bir bağlam oluşturmak için geçerli bağlamın adresinden belirli bir değer çıkarır.|
|[Karşılaştır](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|İki bağlamı karşılaştırma bayraklarıyla belirtilen şekilde karşılaştırır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio'nun **Bellek** penceresi, bellek `IDebugMemoryContext2` adresi için kullanılan değerlendirilmiş ifadeyi içeren arabirimi edinmek için [GetMemoryContext'ı](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) çağırır. Bu içerik daha sonra okumak veya yazmak için adresi belirtmek için [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) ve [WriteAt'a](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
