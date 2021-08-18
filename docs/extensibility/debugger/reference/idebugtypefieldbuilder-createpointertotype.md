---
description: Belirtilen türe bir işaretçi oluşturur.
title: 'Idebugtypefieldbuilder:: CreatePointerToType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreatePointerToType
- IDebugTypeFieldBuilder::CreatePointerToType
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50270c122c2be9daf99089c129e9e97b7684cc49
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126030"
---
# <a name="idebugtypefieldbuildercreatepointertotype"></a>IDebugTypeFieldBuilder::CreatePointerToType
Belirtilen türe bir işaretçi oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreatePointerToType(
   IDebugField*  pTypeField,
   IDebugField** pPtrToTypeField
);
```

```csharp
int CreatePointerToType(
   IDebugField     pTypeField,
   out IDebugField pPtrToTypeField
);
```

## <a name="parameters"></a>Parametreler
`pTypeField`\
'ndaki İşaret etmek için yazın. [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimi tarafından temsil edilir.

`pPtrToTypeField`\
dışı Yeni bir **IDebugField** nesnesi tarafından temsil edilen işaretçiyi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)
