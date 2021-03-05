---
description: Bu yöntem, ad verilen bir diğer ad bulur.
title: 'IDebugBinder3:: FindAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db4d5cad6d0c2990141e0dd3a824425b8b53145b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167730"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Bu yöntem, ad verilen bir diğer ad bulur. Bu, programdaki tüm diğer adları arar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametreler
`pcstrName`\
'ndaki Bulunacak diğer ad adı.

`ppAlias`\
dışı [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) arabirimi tarafından temsil edilen diğer ad (varsa) bulundu.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` (diğer ad bulunamazsa) veya bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, çağrılmadan önce hedef nesneyi null olarak başlatır; daha sonra bir null değeri sınar, daha sonra diğer adın bulunup bulunmadığını belirleyebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
