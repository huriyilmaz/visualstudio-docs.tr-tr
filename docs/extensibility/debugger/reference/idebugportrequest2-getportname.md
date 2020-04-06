---
title: IDebugPortRequest2::GetPortName | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67121e98f2d506aa16c2b4dc3fff2ad5128fb93b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724818"
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
[çıkış] Bağlantı noktasının adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) arabirimi genellikle bir bağlantı noktasına bağlantı elde etmek için hata ayıklama paketinden (istemci) bir bağlantı noktası tedarikçisine (sunucu) geçirilir. Hem hata ayıklama paketi hem de bağlantı noktası tedarikçisi bağlantı noktası için olası seçeneklerin farkındadır. Basit bir dize bağlantı noktasını `IDebugPortRequest2::GetPortName` açıklayabilirse, yöntem bağlantıyı yapmak için yeterli bilgiye sahiptir. Aksi takdirde, ek arabirimler kullanarak sunucu tarafından elde edilebilir `IDebugPortRequest2::QueryInterface`istemci tarafından sağlanabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
