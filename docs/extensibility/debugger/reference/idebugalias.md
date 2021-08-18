---
description: Bir değişken için sayısal diğer adı temsil eder.
title: IDebugAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 52590d62bb2bc6d9090432efe7e11a343601cfd9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064792"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bir değişken için sayısal diğer adı temsil eder. Diğer ad bir değişken için yalnızca farklı bir addır.

## <a name="syntax"></a>Syntax

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 ifade değerlendirici (EE), değişkenler için sayısal diğer adları desteklemek üzere bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) , belirli bir nesne için bir diğer ad oluşturur. Diğer adları aramak için [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) veya [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)kullanın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki yöntemler `IDebugAlias` arabiriminde tanımlanmıştır.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Bu diğer adın başvurduğu nesneyi alır.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Diğer adı alır.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|`ICorDebugValue`Bu nesneyle ilgili yönetilen kod bilgilerine erişim sağlayan bir arabirim alır (yalnızca yönetilen kod).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Bu diğer adı artık kullanılmıyor olarak işaretler.|

## <a name="remarks"></a>Açıklamalar
 Diğer ad, dize formundaki ondalık bir sayıdır ve # karakteri, örneğin, 1001 # olur.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
