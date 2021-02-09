---
title: IDebugManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b90540aaf5f7e409c8fc7fa44126f195230317f8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929816"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bu arabirim, ifade değerlendiricisi 'nin (EE) değer sınıfı örneklerinde özellikleri veya yöntemleri (örneğin, `System.Decimal` ) çağırmasını ve hata ayıklamakta olan programda [değerlendirilmesi](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) çağrılmadan değerlerini ayarlayabilmesini sağlar.

## <a name="syntax"></a>Syntax

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir ifade değerlendirici bu arabirimi bir değişken gibi bir yönetilen kod nesnesini temsil etmek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi edinmek için, bir değer sınıfının bir örneğini temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) üzerinde [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) öğesini çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugObject nesnesinden](../../../extensibility/debugger/reference/idebugobject.md)devralınan yöntemlere ek olarak, `IDebugManagedObject` arabirim aşağıdaki yöntemleri sunar.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Yönetilen kod nesnesini temsil eden ve uygun yönetilen kod arabiriminin alındığı bir arabirim döndürür.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Bu nesnenin değerini belirtilen bir yönetilen kod nesnesinin değerine ayarlar.|

## <a name="remarks"></a>Açıklamalar
 Bir ifade değerlendirici bir ayrıştırma ağacında yönetilen kod nesnesini depolamak için bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Değerlendirmesini](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
