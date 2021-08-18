---
description: Bu arabirim, hata ayıklaması yapılan programı çalıştıran makinenin adres alanı konumundaki bir konumu temsil eder.
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 9cf9d57eefbe69be131a5aa041606ba99dbce973
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153361"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Bu arabirim, hata ayıklaması yapılan programı çalıştıran makinenin adres alanı konumundaki bir konumu temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bellekte bir adresi temsil etmek için bu arabirimi kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetMemoryContext veya](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) [GetMemoryContext çağrısı bu](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) arabirimi döndürür. Ayrıca, Ekle ve [Çıkar'a yapılan](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) çağrılar, uygun aritmetik işlem uygulandıktan sonra bu arabirimin yeni kopyalarını da geri döner. [](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugMemoryContext2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Bu bağlam için kullanıcı tarafından görüntülenebilir adı alır.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Bu bağlamı açıklayan bilgileri alır.|
|[Ekle](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Yeni bir bağlam oluşturmak için geçerli bağlamın adresine belirtilen bir değer ekler.|
|[Çıkar](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Yeni bir bağlam oluşturmak için geçerli bağlamın adreslerinden belirtilen bir değeri çıkarır.|
|[Karşılaştır](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|İki bağlamı, karşılaştırma bayrakları tarafından belirtilen şekilde karşılar.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio penceresinde, **bellek** adresi için kullanılan değerlendirilen ifadeyi içeren arabirimi almak için [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) `IDebugMemoryContext2` çağrısında bulunabilirsiniz. Bu bağlam daha sonra okunacak veya yazacak adresi belirtmek için [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) ve [WriteAt'e](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) geçirebilirsiniz.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
