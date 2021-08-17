---
description: Bu arabirim, kod yollarının bir listesini temsil eder.
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
Bu arabirim, kod yollarının bir listesini temsil eder.

## <a name="syntax"></a>Syntax

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bu arabirimi kod yollarının listesini temsil etmek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi edinmek için [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) çağrısı yapın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumCodePaths2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Sabit Listesi dizisinde belirtilen sayıda kod yolunu alır.|
|[Atla](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Sabit Listesi dizisinde belirtilen sayıda kod yolunu atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Bir Numaralandırıcı içindeki kod yollarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Bir kod yolu, bir programdaki bir dal noktasını veya işlev çağrısını temsil eder. Kod yollarının listesi, kod yürütmenin alındığı yolu temsil eder.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
