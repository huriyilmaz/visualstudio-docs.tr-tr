---
description: Sunucuda hata ayıklama altyapısının bir örneğini oluşturur.
title: 'IDebugCoreServer3:: Createınstanceınserver | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc3a24e28c378bda34034822aedf4d35e5a6313e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154684"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Sunucuda hata ayıklama altyapısının bir örneğini oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parametreler
`szDll`\
'ndaki Parametresinde belirtilen CLSID 'yi uygulayan dll 'nin yolu `clsidObject` . Bu durumda `NULL` , com `CoCreateInstance` işlevi çağrılır.

`wLangId`\
'ndaki Hata ayıklama altyapısının yerel ayarı. [Setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) yönteminin çağrılmaması gerekiyorsa bu 0 olabilir.

`clsidObject`\
'ndaki Oluşturulacak hata ayıklama altyapısının CLSID değeri.

`riid`\
'ndaki Sınıf nesnesinden alınacak olan belirli bir arabirimin arabirim KIMLIĞI.

`ppvObject`\
[out] `IUnknown` oluşturulan nesneden arabirim. Bu nesneyi istenen arabirime atayın veya sıralayamaz.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
