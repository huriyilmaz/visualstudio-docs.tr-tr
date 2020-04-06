---
title: IDebugPointerObject | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b28189b3f0a07a27f5e4478f64963a63d634db5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725495"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bu arabirim bir işaretçi nesnesini temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 İfade değerlendiricisi, işaretçi nesnesini temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimi, bir işaretçiyi `IDebugObject` temsil ediyorsa [QueryInterface'i](/cpp/atl/queryinterface) kullanarak bu arabirimi elde edebilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugObject'den](../../../extensibility/debugger/reference/idebugobject.md)devralınan yöntemlere ek `IDebugPointerObject` olarak, arabirim aşağıdaki yöntemleri ortaya çıkarır.

|Yöntem|Açıklama|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Arabirimin işaret ettiği nesneyi alır.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Arabirimin ardışık bayt lar dizisi olarak işaret ettiği değeri alır.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Arabirimin ardışık bayt lar serisinden geldiği değeri ayarlar.|

## <a name="remarks"></a>Açıklamalar
 Bir ifade değerlendiricisi, ayrışma ağacındaki bir işaretçiyi temsil etmek için bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [İfade Değerlendirme Arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
