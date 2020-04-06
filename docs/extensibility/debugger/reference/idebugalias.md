---
title: IDebugAlias | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2ceb87277460f65e52c35f02e7fbbd01da1101a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736522"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bir değişken için sayısal bir diğer adı temsil eder. Takma ad, bir değişken için farklı bir addır.

## <a name="syntax"></a>Sözdizimi

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 İfade değerlendiricisi (EE), değişkenler için sayısal diğer adları desteklemek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) belirli bir nesne için bir takma ad oluşturur. Takma adları aramak için [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) veya [GetAllAliases'i](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)kullanın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki yöntemler `IDebugAlias` arabirimde tanımlanır.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Bu diğer adın başvurulması gereken nesneyi alır.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Takma adı alır.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Bu nesne `ICorDebugValue` (yalnızca yönetilen kod) hakkında yönetilen kod bilgilerine erişim sağlayan bir arabirim alır.|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Bu takma adı artık kullanılmamış olarak işaretler.|

## <a name="remarks"></a>Açıklamalar
 Takma ad, dize formunda ondalık sayıdır ve ardından # karakteri, örneğin, 1001#.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [İfade Değerlendirme Arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
