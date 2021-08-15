---
description: Sunucuda bir hata ayıklama altyapısı örneği oluşturur.
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3708d56f9eaeaa6f11124107056f67e10c33a7135ccc3998a11095c4a53acef1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121238989"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Sunucuda bir hata ayıklama altyapısı örneği oluşturur.

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
[in] parametresinde belirtilen CLSID'i uygulayan dll'nin `clsidObject` yolu. Bu ise `NULL` COM'un `CoCreateInstance` işlevi çağrılır.

`wLangId`\
[in] Hata ayıklama altyapısının yerel olarak yereli. [SetLocale yöntemi çağrılmasa](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) bu 0 olabilir.

`clsidObject`\
[in] Oluşturularak hata ayıklama altyapısının CLSID'i.

`riid`\
[in] Sınıf nesnesinden almak için belirli arabirimin arabirim kimliği.

`ppvObject`\
[out] `IUnknown` arabirimini seçin. Bu nesneyi istenen arabirime atarak veya sırala.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
