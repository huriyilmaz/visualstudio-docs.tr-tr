---
description: Bu arabirim, belirli bir iş parçacığında bir çağrı yığınında tek bir yığın çerçevesini temsil eder.
title: IDebugStackFrame2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 69bb2e2f58393311b0867a7ea684b99a8df51676
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029677"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Bu arabirim, belirli bir iş parçacığında bir çağrı yığınında tek bir yığın çerçevesini temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bir yığın çerçevesini temsil etmek için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IEnumDebugFrameInfo2 arabirimini almak için EnumFrameInfo çağrısı.](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) [](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) Arabirimi [içeren](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) bir [FRAMEINFO yapısını](../../../extensibility/debugger/reference/frameinfo.md) almak için Next `IDebugStackFrame2` çağrısı.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugStackFrame2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Bu yığın çerçevesi için kod bağlamını alır.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Bu yığın çerçevesi için belge bağlamını alır.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Yığın çerçevesinin adını alır.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Yığın çerçevesinin açıklamasını alır.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Bir yığın çerçevesiyle ilişkili fiziksel adres aralığının makineye bağımlı bir gösterimini alır.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Bir yığın çerçevesinin ve iş parçacığının geçerli bağlamında ifade değerlendirmesi yapmak için bir değerlendirme bağlamı alır.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Yığın çerçevesiyle ilişkili dili alır.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Bir yığın çerçevesiyle ilişkili özelliklerin açıklamasını alır.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Yığın çerçevesi özellikleri için bir numaralayıcı oluşturur.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Yığın çerçevesiyle ilişkili iş parçacığını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim yalnızca hata ayıklaması yapılan program bir kesme noktası (kullanıcı tarafından ayarlanmış bir kesme noktası veya özel durumdan kaynaklandı) durdurulursa elde edilir. Bu arabirimden ifadeleri değerlendirmek için bir ifade bağlamı elde etmek, kayıt listesi döndürülerek çağrı yığını elde etmek ve incelemektir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
