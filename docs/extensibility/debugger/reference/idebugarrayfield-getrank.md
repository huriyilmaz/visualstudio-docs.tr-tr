---
title: 'Ihata ayıklama Garrayfield:: GetRank | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10f42ca10496d89955032bd531651186d0aecf37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926355"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Dizinin boyutunu veya boyut sayısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parametreler
`pdwRank`\
dışı Dereceyi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir dizinin sıralaması, boyut sayısına karşılık gelir. C++ ve C# ' de, çok boyutlu diziler gerçekten dizi dizilerdir ve bu nedenle yalnızca bir boyutlu dizi olarak kabul edilebilir (ve `GetRank` yöntemi her zaman 1 ' i döndürür). ' De, [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] diğer yandan çok boyutlu diziler farklı şekilde işlenir ve böyle bir dizinin sıralaması boyut sayısını yansıtır (ve `GetRank` Yöntem her zaman boyut sayısını döndürür).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
