---
description: Bağlantı noktasının adını alır.
title: 'IDebugPortRequest2:: GetPortName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee0d0199a87dff6f29e82b691ed0a396f6d0162a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169255"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Bağlantı noktasının adını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPortName( 
   BSTR* pbstrPortName
);
```

```csharp
int GetPortName( 
   out string pbstrPortName
);
```

## <a name="parameters"></a>Parametreler
`pbstrPortName`\
dışı Bağlantı noktasının adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) arabirimi genellikle bir bağlantı noktasına bağlantı almak için bir hata ayıklama paketinden (istemci) bir bağlantı noktası sağlayıcısına (sunucu) geçirilir. Hem hata ayıklama paketi hem de bağlantı noktası sağlayıcısı, bağlantı noktası için olası seçimleri algılar. Basit bir dize bağlantı noktasını tanımlıyorsa, `IDebugPortRequest2::GetPortName` yöntemi bağlantı kurmak için yeterli bilgiye sahip olabilir. Aksi takdirde, kullanarak sunucu tarafından elde edilebilir istemci tarafından Ek arabirimler temin edilebilir `IDebugPortRequest2::QueryInterface` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
