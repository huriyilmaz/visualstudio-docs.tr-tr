---
title: IDebugBinder3 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa85872337fdc1f7519d0de98cffe1436ef41c67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735677"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bu arabirim türleri, diğer adlar ve özel görselleştirici hizmetlerine erişim sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı bu arabirimi takma adları, özel görselleştirici hizmetleri ve nesne türü bilgilerine erişimi desteklemek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) arabirimi [QueryInterface](/cpp/atl/queryinterface)kullanarak bu arabirimi elde eder.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) arabirimi tarafından sağlanan yöntemlere ek olarak, bu arabirim aşağıdakileri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Bu nesnenin bağlı olduğu belleği temsil eden bir bellek nesnesi alır.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Bu nesneyle ilişkili özel durumu alır (varsa),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Adı verilen bir takma adı alır,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Bu nesne için tüm diğer adlardan oluşan bir dizi alır,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Bu nesneyle ilişkili bağımsız değişken türlerinin sayısını alır,|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Bu nesneyle ilişkili bağımsız değişken türlerinin listesini alır,|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Görselleştirici hizmetine arayüz alır,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Nesne konumunu veya 64 bit bellek adresini bellek bağlamına dönüştürür.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [İfade Değerlendirme Arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
