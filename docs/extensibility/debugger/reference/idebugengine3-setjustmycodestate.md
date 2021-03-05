---
description: Bu yöntem, hata ayıklama altyapısına, Adatmycode durum bilgilerini söyler.
title: 'IDebugEngine3:: Setadatmycodestate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a81fa4bda506cf1be27f658b071910e7c8ccd8a7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153709"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Bu yöntem, hata ayıklama altyapısına, Adatmycode durum bilgilerini söyler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Parametreler
`fUpdate`\
'ndaki `TRUE`Geçerli bilgileri güncelleştirmek için sıfır olmayan () ( `FALSE` daha önce ayarlanmış herhangi bir şey yok sayılıyor).

`dwModules`\
'ndaki İçindeki bilgi yapılarının sayısı `rgJMCSpec.`

`rgJMCSpec`\
'ndaki Kullanılacak [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) yapıları dizisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Adammycode, bu sistem kodu için kaynak kodu kullanılabilir olsa bile, yalnızca bir kullanıcıya ait kodu ve sistem kodu gibi tüm ara kodları yok saymanın hata ayıklaması kavramıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
