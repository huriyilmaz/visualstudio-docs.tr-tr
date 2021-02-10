---
title: IDebugStackFrame2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7241c697baf7810d961f4cc3aba71d469bad4582
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963568"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Bu arabirim, belirli bir iş parçacığında çağrı yığınında tek bir yığın çerçevesini temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), yığın çerçevesini göstermek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) arabirimi almak Için [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) çağırın. Arabirimini içeren bir [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) yapısını almak için [Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) çağrısı yapın `IDebugStackFrame2` .

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugStackFrame2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Bu yığın çerçevesi için kod bağlamını alır.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Bu yığın çerçevesi için belge bağlamını alır.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Yığın çerçevesinin adını alır.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Yığın çerçevesinin açıklamasını alır.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Yığın çerçevesiyle ilişkili fiziksel adres aralığının makineye bağlı temsilini alır.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Yığın çerçevesinin ve iş parçacığının geçerli bağlamı içinde ifade değerlendirmesi yapmak için bir değerlendirme bağlamı alır.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Yığın çerçevesiyle ilişkili dili alır.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Yığın çerçevesiyle ilişkili özelliklerin açıklamasını alır.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Yığın çerçevesi özellikleri için bir Numaralandırıcı oluşturur.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Yığın çerçevesiyle ilişkili iş parçacığını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim yalnızca hata ayıklamakta olan program bir kesme noktasında durdurulduğunda (bir kullanıcı kümesi kesme noktası veya özel durum nedeniyle) elde edilir. Bu arabirimden, ifadeleri değerlendirmek için bir ifade bağlamı elde edilebilir, yazmaçların listesi döndürülebilir veya çağrı yığını elde edilebilir ve incelenebilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
