---
description: Bu arabirim özel bir özniteliği temsil eder ve özniteliğin adını, üst ve sınıf türünü sağlar.
title: IDebugCustomAttribute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: cb62849f82b2fdbbcc6e2942fbeebcb7c1dd60d3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079525"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Bu arabirim özel bir özniteliği temsil eder ve özniteliğin adını, üst ve sınıf türünü sağlar.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Sembol sağlayıcısı, bir sembolle ilişkili özel öznitelikleri desteklemek için bu arabirimi kullanır. Genellikle kendi nesnesine uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Next çağrısı bu [arabirimi](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) döndürür. [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) yöntemine yapılan bir [çağrı, IEnumDebugCustomAttributes arabirimini](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) döndürür.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugCustomAttribute` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Geçerli özniteliğin ekli olduğu alanı alır.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Özel öznitelik sınıf türünü alır.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Özel özniteliğin adını alır.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Öznitelik bilgilerini bayt blobu olarak alır.|

## <a name="remarks"></a>Açıklamalar
 Özel öznitelik, belirli bir sınıf veya yöntem ile ilişkili özel meta veriler sağlar C# için bir yapıdır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
