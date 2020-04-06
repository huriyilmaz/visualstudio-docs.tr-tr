---
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2346bb76fe604265a309a51f48b734fc6f2ab8d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733025"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Sunucuda hata ayıklama altyapısı örneği oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
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
[içinde] Parametrede belirtilen CLSID'yi uygulayan dll'ye `clsidObject` giden yol. Bu ise, `NULL`com `CoCreateInstance` işlevi çağrılır.

`wLangId`\
[içinde] Hata ayıklama motorunun yerel alanı. [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) yöntemi çağrılmaması gerekiyorsa, bu 0 olabilir.

`clsidObject`\
[içinde] CLSID hata ayıklama motoru oluşturmak için.

`riid`\
[içinde] Sınıf nesnesinden alınacak belirli arabirimin arabirim kimliği.

`ppvObject`\
[çıkış] `IUnknown` anında nesneden arayüz. Bu nesneyi istenilen arabirime döküm veya mareşal.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [Setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
