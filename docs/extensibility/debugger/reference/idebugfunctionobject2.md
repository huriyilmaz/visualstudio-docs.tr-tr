---
title: IDebugFunctionObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 304269ba2a4f556cfe931157c445d7b4fc86f489
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929946"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bir işlevi temsil eder ve [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimini geliştirir.

## <a name="syntax"></a>Syntax

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir ifade değerlendirici (EE), bir işlevi temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimin yöntemleri **IDebugFunctionObject** türlerini aşağıdaki yollarla erteler:

- **Ihata ayıklama Gevaluate** yöntemi bayraklar alır.

- **CreateObject** yöntemi bayraklar ve bir zaman aşımı alır.

- **CreateStringObjectWithLength** yöntemi bir uzunluk alır.

## <a name="methods"></a>Yöntemler
 Bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Değerlendirme bayrağı ayarları ve zaman aşımı değeri verilen bir Oluşturucu kullanan bir nesne oluşturur.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Belirtilen uzunluğa sahip bir dize nesnesi oluşturur.|
|[Değerlendirmesini](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|İşlevini çağırır ve sonuç değerini bir nesne olarak döndürür.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
