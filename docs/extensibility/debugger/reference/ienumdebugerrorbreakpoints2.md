---
description: Bu arabirim, bekleyen bir kesme noktasıyla ilişkili hata kesme noktalarını numaralandırır.
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: dfbd8a47aaf7fa62d4e72842645d1acb709c43f2b11c90893a2867577fb8d459
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121415512"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Bu arabirim, bekleyen bir kesme noktasıyla ilişkili hata kesme noktalarını numaralandırır.

## <a name="syntax"></a>Syntax

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bu arabirimi kesme noktaları desteğinin bir parçası olarak uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio, bağlanmayan kesme noktaları listesini temsil eden bu arabirimi elde etmek için [canbind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) çağırır veya bağlanmamış kesme noktaları listesini temsil eden bu arabirimi elde etmek için [enumerrorkesmenoktaları](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) .

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugErrorBreakpoints2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Bir numaralandırma dizisinde belirtilen sayıda hata kesme noktası alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Sabit Listesi dizisinde belirtilen sayıda hata kesme noktası atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Bir Numaralandırıcı içindeki hata kesme noktası sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, her biri, bağlanamamayan ve neden bağlanamadığına ilişkin bir kesme noktası tanımlayan [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) arabirimlerinin bir listesini tutar. Visual Studio `IEnumDebugErrorBreakpoint2` ıde 'de gösterilen kesme noktalarını güncelleştirmek için arabirimini kullanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
