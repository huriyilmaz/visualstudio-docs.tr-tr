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
ms.openlocfilehash: 53345ce6c7cc7a261b15367d926a68701a087ef3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089361"
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
