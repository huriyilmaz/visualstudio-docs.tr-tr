---
description: Bu yöntem, işlemin altında barındırılacak dili ayarlar.
title: 'IDebugProcess3:: SetHostingProcessLanguage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d2a95a5f8181b7b58198a8a56b7fb0037ef0bc1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150126"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
Bu yöntem, işlemin altında barındırılacak dili ayarlar. Bu dil, uygun ifade değerlendiricisi 'ni yüklemek için hata ayıklama altyapısı (DE) tarafından kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetHostingProcessLanguage(
   REFGUID guidLang
);
```

```csharp
int SetHostingProcessLanguage(
   ref Guid guidLang
);
```

## <a name="parameters"></a>Parametreler
`guidLang`\
[in] `GUID` öğesinin kullanması gereken dil. `GUID_NULL` `Guid.Empty` Varsayılan dili de kullanması için (C++) veya (C#) belirtin.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
- Geçerli dil ayarını almak için [Gethostingprocesslanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)
