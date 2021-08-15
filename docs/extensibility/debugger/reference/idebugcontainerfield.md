---
description: Bu arabirim, diğer semboller veya türler için kapsayıcı olan bir simgeyi veya türü temsil eder.
title: IDebugContainerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d0345582e0429af045f085833be8b41158ca7ac12e3a5b1dda1721ed5b72d270
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239054"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Bu arabirim, diğer semboller veya türler için kapsayıcı olan bir simgeyi veya türü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Sembol sağlayıcısı bu arabirimi [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimini uygulayan aynı nesnede kullanır. Bu arabirim ayrıca kapsayıcıları temsil eden tüm arabirimler için temel sınıftır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Birçok arabirimde birçok yöntem bu arabirimi geri döner. Bu tüm kapsayıcılar için temel bir sınıf olduğundan, QueryInterface kullanılarak bu arabirimden daha özel [arabirimler elde edilir.](/cpp/atl/queryinterface) Bu arabirimler [IDebugArrayField,](../../../extensibility/debugger/reference/idebugarrayfield.md) [IDebugClassField,](../../../extensibility/debugger/reference/idebugclassfield.md) [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)ve [IDebugPropertyField arabirimlerini içerir.](../../../extensibility/debugger/reference/idebugpropertyfield.md)

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 [Bu arabirim, IDebugField arabiriminde](../../../extensibility/debugger/reference/idebugfield.md) yöntemlerine ek olarak aşağıdaki yöntemi de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Kapsayıcının alanları için bir numaralayıcı oluşturur.|

## <a name="remarks"></a>Açıklamalar
 Diziler (değişkenler için kapsayıcılar), sınıflar (yöntemler ve değişkenler için kapsayıcılar) ve yöntemler (parametreler ve yerel değişkenler için kapsayıcılar) kapsayıcılara örnek olarak verilmiştir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
