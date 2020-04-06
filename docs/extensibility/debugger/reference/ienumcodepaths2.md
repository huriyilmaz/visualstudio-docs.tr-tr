---
title: IEnumCodePaths2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89c8cac9a7c2baa020002fe852330639d7081982
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717723"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Bu arabirim kod yollarının listesini temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) kod yollarının listesini temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi elde etmek için [EnumCodePaths'i](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumCodePaths2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Numaralandırma sırasında belirli sayıda kod yolu alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Numaralandırma sırasında belirli sayıda kod yolunu atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Bir numaralandırmada kod yollarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Kod yolu, programdaki bir dal noktasını veya işlev çağrısını temsil eder. Kod yollarının listesi, kod yürütmenin geçtiği yolu temsil eder.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
