---
description: Bir değişken için sayısal diğer adı temsil eder ve bir ifade değerlendiricinin (EE) diğer ad için uygulama etki alanını elde ettiğine olanak sağlar.
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ae66d69153a539c42000914c9df1c275aa3a431c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627614"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR İfade Değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Bir değişken için sayısal diğer adı temsil eder ve bir ifade değerlendiricinin (EE) diğer ad için uygulama etki alanını elde ettiğine olanak sağlar.

## <a name="syntax"></a>Syntax

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, yönetilen hata ayıklama altyapısı (DE) tarafından uygulanır.

## <a name="methods"></a>Yöntemler
 [Bu arabirim, IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) arabiriminde yöntemlere ek olarak aşağıdaki yöntemi de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Uygulama etki alanının tanımlayıcısını alın.|

## <a name="remarks"></a>Açıklamalar
 Diğer ad, dize biçimindeki bir ondalık sayıdır ve ardından # karakteri (örneğin, 1001#).

## <a name="requirements"></a>Gereksinimler
 Üst Bilgi: Ee.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll
