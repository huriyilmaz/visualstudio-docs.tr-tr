---
title: 'IDebugMethodField:: GetThis | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1893ffac03aba345589274475f81abd44b5b7b5f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936840"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
`this` `Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] Yöntemi içeren nesnenin (ın) işaretçisini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parametreler
`ppClass`\
dışı "This" işaretçisini temsil eden bir [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Nesne yönelimli dillerde, genellikle bir sınıfın geçerli örneklemesi için örtülü bir işaretçi vardır. Bu, `this` C#/c + + ve içinde olduğu gibi bilinir `Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
