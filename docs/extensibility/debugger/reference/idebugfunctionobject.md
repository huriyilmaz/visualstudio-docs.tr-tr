---
title: IDebugFunctionObject | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6433c1f2c540b040a3b3beccc264377e69592387
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728493"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bu arabirim bir işlevi temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir ifade değerlendiricisi, bir işlevi temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabiriminin bir uzmanlık ve `IDebugObject` arayüz üzerinde [QueryInterface](/cpp/atl/queryinterface) kullanılarak elde edilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugObject'den](../../../extensibility/debugger/reference/idebugobject.md)devralınan yöntemlere ek `IDebugFunctionObject` olarak, arabirim aşağıdaki yöntemleri ortaya çıkarır.

|Yöntem|Açıklama|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|İlkel bir veri nesnesi oluşturur.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Bir oluşturucu kullanarak bir nesne oluşturur.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Oluşturucusu olmayan bir nesne oluşturur.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Bir dizi nesnesi oluşturur.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Bir dize nesnesi oluşturur.|
|[Değerlendirmek](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|İşlevi çağırır ve ortaya çıkan değeri nesne olarak döndürür.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, ifade değerlendiricinin ayrışdırıcı bir ağaçtaki işlevleri temsil etmesini sağlar. Bu `Create` arabirimdeki yöntemler, yönteme giriş parametrelerini temsil eden nesneleri oluşturmak için kullanılır. İşlev daha sonra, işlevin geri dönüş değerini temsil eden bir nesneyi döndüren [Değerlendir](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) yöntemini çağırarak çalıştırılabilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [İfade Değerlendirme Arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
