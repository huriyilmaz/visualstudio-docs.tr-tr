---
description: Bu arabirim, kod yollarının listesini temsil eder.
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 952df4bec381fdce0850d2f74f0bc81329f14c2c10a7f6dc2ad3de019761c355
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448669"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Bu arabirim, kod yollarının listesini temsil eder.

## <a name="syntax"></a>Syntax

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), kod yollarının listesini temsil etmek için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu [arabirimi almak için EnumCodePaths'i](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IEnumCodePaths2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Bir numaralama dizisinde belirtilen sayıda kod yolu alma.|
|[Atla](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Bir numaralama dizisinde belirtilen sayıda kod yolunu atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Numaralayıcıda kod yollarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Kod yolu, programda bir dal noktasını veya işlev çağrısını temsil eder. Kod yolları listesi, kod yürütmenin üzerinden geçen yolu temsil eder.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
