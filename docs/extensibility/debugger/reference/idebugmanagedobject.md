---
title: IDebugManagedObject | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fbd270aa1b65f05f308d41d22f154fb53b8833d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727683"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bu arabirim, ifade değerlendiricisinin (EE) değer sınıfı örneklerindeki özellikleri `System.Decimal`veya yöntemleri aramasını (örneğin,) ve debugged olan programda [Değerlendir'i](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) aramadan değerlerini ayarlamasını sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir ifade değerlendiricisi, değişken gibi yönetilen bir kod nesnesini temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi elde etmek için, değer sınıfının bir örneğini temsil eden bir [IDebugObject'te](../../../extensibility/debugger/reference/idebugobject.md) [GetManagedDebugObject'i](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugObject'den](../../../extensibility/debugger/reference/idebugobject.md)devralınan yöntemlere ek `IDebugManagedObject` olarak, arabirim aşağıdaki yöntemleri ortaya çıkarır.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Yönetilen kod nesnesini temsil eden ve uygun yönetilen kod arabiriminin alınabileceği bir arabirim verir.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Bu nesnenin değerini belirtilen yönetilen kod nesnesinin değerine ayarlar.|

## <a name="remarks"></a>Açıklamalar
 Bir ifade değerlendiricisi, yönetilen bir kod nesnesini ayrıştırma ağacında depolamak için bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [İfade Değerlendirme Arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Değerlendirmek](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
