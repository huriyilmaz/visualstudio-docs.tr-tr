---
title: IDebugStackFrame2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37acb9f2984c36130de494108ef4b76a59cc74e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719507"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Bu arabirim, belirli bir iş parçacığındaki çağrı yığınındaki tek bir yığın çerçeveyi temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) bir yığın çerçeveyi temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [Bir IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) arabirimini almak için [EnumFrameInfo'yı](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) arayın. Arabirimi içeren bir [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapısını `IDebugStackFrame2` almak için [Next'i](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugStackFrame2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Bu yığın çerçevesi için kod bağlamını alır.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Bu yığın çerçevesi için belge bağlamını alır.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Yığın çerçevesinin adını alır.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Yığın çerçevesinin açıklamasını alır.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Yığın çerçevesiyle ilişkili fiziksel adres aralığının makineye bağımlı bir temsilini alır.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Yığın çerçevesi ve iş parçacığının geçerli bağlamında ifade değerlendirmesi yapmak için bir değerlendirme bağlamı alır.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Yığın çerçevesiile ilişkili dili alır.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Yığın çerçevesiyle ilişkili özelliklerin açıklamasını alır.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Yığın çerçeve özellikleri için bir sayısallaştırıcı oluşturur.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Yığın çerçevesi ile ilişkili iş parçacığı alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim yalnızca hata ayıklanan program bir kesme noktasında durdurulduğunda (kullanıcı kümesi kesme noktası veya özel bir özel durum nedeniyle) elde edilir. Bu arabirimden, ifadeleri değerlendirmek için bir ifade bağlamı elde edilebilir, kayıt listesi döndürülebilir veya çağrı yığını elde edilip incelenebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
