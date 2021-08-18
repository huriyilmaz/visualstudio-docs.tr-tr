---
description: Bu arabirim bir nesne hakkında ek bilgi sağlar.
title: IDebugObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d3d18068b5ad9ef74a84a31366d7c90bdefc365c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153296"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bu arabirim bir nesne hakkında ek bilgi sağlar.

## <a name="syntax"></a>Syntax

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 İfade değerlendirici bu arabirimi, diğer adlar için destek sunmak ve nesneyle ilgili bilgilere erişmek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimi, bu arabirimi [QueryInterface](/cpp/atl/queryinterface)kullanarak alabilir. Ayrıca, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimindeki yöntemlere ek olarak, `IDebugObject2` arabirim şunları uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Bu nesne tarafından temsil edilen özelliği yedeklebilecek alanı veya değişkeni (varsa) alır.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Bu nesnenin değerini temsil eden yönetilen kod nesnesini alır.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Bu nesne için benzersiz bir KIMLIK oluşturur veya var olan bir diğer adı döndürür.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Varsa, bu nesneyle ilişkili diğer adı alır.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Bu nesnenin türünü alır.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Bu nesnenin Kullanıcı verilerini temsil edip etmediğini belirler.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Düzenle ve devam et durumunun artık geçerli olup olmadığını belirler.<br /><br /> Özel bir ifade değerlendirici bu yöntemi uygulamaz (her zaman döndürmelidir `E_NOTIMPL` ).|

## <a name="remarks"></a>Açıklamalar
 Diğer adlarla ilgili bir tartışma için [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) bölümüne bakın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
