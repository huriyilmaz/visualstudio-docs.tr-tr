---
description: Bu arabirim türlere, diğer adlara ve özel görselleştirici hizmetlerine erişim sağlar.
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 423bfa11073e2ed29474056098ad2a189e346113
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104358"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR İfade Değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Bu arabirim türlere, diğer adlara ve özel görselleştirici hizmetlerine erişim sağlar.

## <a name="syntax"></a>Syntax

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı diğer adları, özel görselleştirici hizmetlerini ve nesne türü bilgilerine erişimi desteklemek için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDebugBinder arabirimi,](../../../extensibility/debugger/reference/idebugbinder.md) [QueryInterface](/cpp/atl/queryinterface)kullanarak bu arabirimi elde ediyor.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 [Bu arabirim, IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) arabirimi tarafından sağlanan yöntemlere ek olarak şunları da sunar:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Bu nesnenin bağlı olduğu belleği temsil eden bir bellek nesnesi alınır.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Bu nesneyle ilişkili özel durumu (varsa) alın,|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Adına göre bir diğer ad alan,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Bu nesne için tüm diğer adların bir dizisini,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Bu nesneyle ilişkili bağımsız değişken türlerinin sayısını alır,|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Bu nesneyle ilişkili bağımsız değişken türlerinin listesini alın,|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Görselleştirici hizmetine arabirim alır,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Nesne konumunu veya 64 bit bellek adresini bir bellek bağlamına dönüştürür.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: ee.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
