---
title: IDebugAlias2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00e13da257c5477b3834ebb85bf6d481fe699362
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736361"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bir değişken için sayısal bir diğer adı temsil eder ve bir ifade değerlendiricinin (EE) diğer ad için uygulama etki alanını elde etmesini sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim yönetilen hata ayıklama altyapısı (DE) tarafından uygulanır.

## <a name="methods"></a>Yöntemler
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) arabirimindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Uygulama etki alanı için tanımlayıcıyı alır.|

## <a name="remarks"></a>Açıklamalar
 Takma ad, dize formunda ondalık sayıdır ve ardından # karakteri, örneğin, 1001#.

## <a name="requirements"></a>Gereksinimler
 Başlık: Ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
