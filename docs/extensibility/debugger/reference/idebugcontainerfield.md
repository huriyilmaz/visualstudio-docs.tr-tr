---
title: IDebugContainerField | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72296517a64c6dcfcb8e347fb00588504aa75a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733210"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Bu arabirim, diğer semboller veya türler için bir kapsayıcı olan bir sembolü veya türü temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir sembol sağlayıcısı bu arabirimi [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimini uygulayan nesne üzerinde uygular. Bu arabirim aynı zamanda kapsayıcıları temsil eden tüm arabirimler için taban sınıftır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Birçok arabirimdeki birçok yöntem bu arabirimi döndürer. Bu tüm kapsayıcılar için bir taban sınıf olduğundan, [queryInterface](/cpp/atl/queryinterface)kullanarak bu arabirimden daha özel arabirimler elde edebilirsiniz. Bu tür arabirimler [IDebugArrayField,](../../../extensibility/debugger/reference/idebugarrayfield.md) [IDebugClassField,](../../../extensibility/debugger/reference/idebugclassfield.md) [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)ve [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)içerir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Kapsayıcının alanları için bir sayısallaştırıcı oluşturur.|

## <a name="remarks"></a>Açıklamalar
 Diziler (değişkenler için kapsayıcılar), sınıflar (yöntem ve değişkenler için kapsayıcılar) ve yöntemler (parametreler ve yerel değişkenler için kapsayıcılar) kapsayıcıların tüm örnekleridir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
