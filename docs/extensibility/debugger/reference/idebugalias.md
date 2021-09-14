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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627626"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR İfade Değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Bir değişken için sayısal diğer adı temsil eder. Diğer ad, bir değişken için farklı bir addır.

## <a name="syntax"></a>Syntax

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 İfade değerlendiricisi (EE), değişkenler için sayısal diğer adları desteklemek için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) belirli bir nesne için bir diğer ad oluşturur. Diğer adları aramak için [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) veya [GetAllAliases kullanın.](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki yöntemler arabiriminde `IDebugAlias` tanımlanmıştır.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Bu diğer adın başvurduğu nesneyi alır.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Diğer ad alır.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Bu `ICorDebugValue` nesneyle ilgili yönetilen kod bilgilerine erişim sağlayan bir arabirim alır (yalnızca yönetilen kod).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Bu diğer adı artık kullanılmadı olarak işaretler.|

## <a name="remarks"></a>Açıklamalar
 Diğer ad, dize biçimindeki bir ondalık sayıdır ve ardından # karakteri (örneğin, 1001#).

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: ee.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
