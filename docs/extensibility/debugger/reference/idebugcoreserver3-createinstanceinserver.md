---
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
ms.openlocfilehash: b76c37d767ae38a33d537a96f9ad8f7087503ed2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909958"
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
