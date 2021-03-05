---
description: Özel bir özniteliğin ada göre varolup olmadığını belirler.
title: 'IDebugCustomAttributeQuery2:: IsCustomAttributeDefined | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c25a0357a1b0b8768f02fd7eb903c30943964445
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168302"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Özel bir özniteliğin ada göre varolup olmadığını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>Parametreler
`pszCustomAttributeName`\
'ndaki Bulunacak özel özniteliğin adını içeren bir dize.

## <a name="return-value"></a>Dönüş Değeri
 Özel öznitelik bu alanda tanımlanmışsa S_OK döndürür, aksi takdirde S_FALSE döndürür.

## <a name="remarks"></a>Açıklamalar
 Özel öznitelikle ilişkili öznitelik baytlarını almak için [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) metodunu çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
