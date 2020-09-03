---
title: 'IDebugCustomAttribute:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15d435d043d0e3863358628fa12016431a417918
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732766"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Özel özniteliğin adını alır.

## <a name="syntax"></a>Söz dizimi

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
