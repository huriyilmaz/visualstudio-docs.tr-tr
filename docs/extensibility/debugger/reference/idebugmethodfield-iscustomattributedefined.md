---
description: Belirli bir özel özniteliğin tanımlanıp tanımlanmadığını belirler.
title: 'IDebugMethodField:: IsCustomAttributeDefined | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afecc77ef3b38c9c6e7b106ce0f76fb5c167719f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035052"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Belirli bir özel özniteliğin tanımlanıp tanımlanmadığını belirler.

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
 Özel öznitelik bu yöntemde tanımlanmışsa S_OK döndürür, aksi takdirde S_FALSE döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
