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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 99d015fa327992f22fbab95513102ed9e376a96a29a6ae037ac8f33acb2ea30b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403019"
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
