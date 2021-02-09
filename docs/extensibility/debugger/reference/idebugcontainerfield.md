---
title: IDebugContainerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2e7ed9e573236f0bdeff9c9a8433af322a5a5f79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928503"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Bu arabirim, diğer semboller veya türler için kapsayıcı olan bir simgeyi veya türü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir sembol sağlayıcısı, bu arabirimi [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimini uygulayan aynı nesne üzerinde uygular. Bu arabirim Ayrıca kapsayıcıları temsil eden tüm arabirimler için temel sınıftır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Birçok arabirimde birçok yöntem bu arabirimi döndürür. Bu, tüm kapsayıcılar için bir temel sınıf olduğundan, bu arabirimden [QueryInterface](/cpp/atl/queryinterface)kullanarak daha özelleştirilmiş arabirimler elde edilebilir. Bu tür arabirimler [ıdebuggarrayfield](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)ve [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)içerir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Bu arabirim, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimindeki yöntemlere ek olarak aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Kapsayıcının alanları için bir Numaralandırıcı oluşturur.|

## <a name="remarks"></a>Açıklamalar
 Diziler (değişkenler için kapsayıcılar), sınıflar (yöntemlere ve değişkenlere yönelik kapsayıcılar) ve yöntemleri (parametreler ve yerel değişkenler için kapsayıcılar), kapsayıcılara örnektir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
