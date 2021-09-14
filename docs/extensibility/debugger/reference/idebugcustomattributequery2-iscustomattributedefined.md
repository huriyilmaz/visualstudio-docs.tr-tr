---
description: Özel bir özniteliğin adıyla var olup olmadığını belirler.
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d4e3fe35577c37d70413b0b4ad8a3bd17d76451c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627441"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Özel bir özniteliğin adıyla var olup olmadığını belirler.

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
[in] Buluna özel özniteliğin adını içeren bir dize.

## <a name="return-value"></a>Dönüş Değeri
 Özel S_OK bu alanda tanımlanmışsa, aksi takdirde bu değeri S_FALSE.

## <a name="remarks"></a>Açıklamalar
 Özel öznitelikle ilişkili öznitelik baytlarını almak için [GetCustomAttributeByName yöntemini](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
