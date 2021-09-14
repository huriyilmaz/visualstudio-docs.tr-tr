---
description: Bu arabirim bir sınıfı tür olarak temsil eder.
title: IDebugClassField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: aa6691a4606b6724eacd6386a569af02ceb2cddd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627464"
---
# <a name="idebugclassfield"></a>IDebugClassField
Bu arabirim bir sınıfı tür olarak temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Sembol sağlayıcısı bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimini uygulayan aynı nesne üzerinde kullanır. Bu arabirim, bir sınıf türünü temsil eden bir uzmanlıktır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir dizi arabirim [IDebugSymbolProvider,](../../../extensibility/debugger/reference/idebugsymbolprovider.md) [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)ve [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)dahil olmak üzere bu arabirimi getirebilirsiniz yöntemlerine sahiptir. Ayrıca, [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) yöntemi bayrağını döndürürse [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabiriminden bu arabirimi almak için [QueryInterface](/cpp/atl/queryinterface) kullanabilirsiniz. `FIELD_TYPE_CLASS`

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 [Bu arabirim, IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ve [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimleri üzerinde yöntemlere ek olarak şunları da kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Bu sınıfın temel sınıfları için bir numaralayıcı oluşturur.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|sınıfında belirli bir arabirimin tanımlanmamış olup olmadığını belirler.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Bu sınıfın iç içe geçmiş sınıfları için bir numaralayıcı oluşturur.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Bu sınıfı kapsayan sınıfı alır.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Bu sınıf tarafından uygulanan arabirimler için bir numaralayıcı oluşturur.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Bu sınıfın oluşturucuları için bir numaralayıcı oluşturur.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Varsayılan dizin oluşturmanın adını alır.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Bu sınıfın iç içe geçmiş numaralayıcıları için bir numaralayıcı oluşturur.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
