---
description: Özel özniteliğin adını alır.
title: 'IDebugCustomAttribute:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 807922628249a38400c86001a27498f3c26fafd30c2b2907e8faa2cb09fd2454
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307966"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Özel özniteliğin adını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Parametreler
`bstrName`\
dışı Özel özniteliğin adını içeren bir dize döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem tarafından döndürülen adlandırılmış öznitelik, özniteliği bildirmek için kullanılan sınıfın adına karşılık gelir. Bu, C# ' ın bir bildirimde kullanıldığında özel öznitelik adından "öznitelik" sonekinin bırakılmasına izin veren bir özel öznitelik sınıfının adına tam olarak karşılık gelmeyebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
