---
title: IDebugClassField | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b0e4cd7c851e65edf299f45ec97273804c25d8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734294"
---
# <a name="idebugclassfield"></a>IDebugClassField
Bu arabirim bir sınıfı tür olarak temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir sembol sağlayıcısı bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimini uygulayan nesne üzerinde uygular. Bu arabirim, sınıf türünü temsil eden bir uzmanlık alanıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Arabirimler bir dizi [IDebugSymbolProvider,](../../../extensibility/debugger/reference/idebugsymbolprovider.md) [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)ve [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)dahil bu arabirimi döndürebilir yöntemleri vardır. Ayrıca, [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) yöntemi bayrağı `FIELD_TYPE_CLASS`döndürürse, Bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabiriminden elde etmek için [QueryInterface'i](/cpp/atl/queryinterface) kullanabilirsiniz.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugField ve IDebugContainerField](../../../extensibility/debugger/reference/idebugfield.md) arabirimlerindeki yöntemlere ek olarak, bu arabirim aşağıdakileri uygular: [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Bu sınıfın temel sınıfları için bir sayısallaştırıcı oluşturur.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Sınıfta belirli bir arabirim tanımlı olup olmadığını belirler.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Bu sınıfın iç içe geçen sınıfları için bir sayısallaştırıcı oluşturur.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Bu sınıfı içine alan sınıfı alır.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Bu sınıf tarafından uygulanan arabirimler için bir sayısallaştırıcı oluşturur.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Bu sınıfın oluşturucuları için bir sayısallaştırıcı oluşturur.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Varsayılan dizinleyicinin adını alır.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Bu sınıfın iç içe geçen sayısalatörleri için bir sayısallaştırıcı oluşturur.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
