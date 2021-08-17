---
description: Bağlantı noktasının adını alır.
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5eceb34e8d82853289663a6b6795a266444d8635e34f33c490fe2a53307c1f2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121339066"
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
[out] Bağlantı noktasının adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) arabirimi, bağlantı noktası bağlantısı elde etmek için genellikle bir hata ayıklama paketinden (istemci) bir bağlantı noktası sağlayıcıya (sunucu) geçir edilir. Hem hata ayıklama paketi hem de bağlantı noktası sağlayıcı, bağlantı noktası için olası seçimlerin farkındadır. Basit bir dize bağlantı noktasını açıklayana kadar, `IDebugPortRequest2::GetPortName` yöntemin bağlantıyı yapmak için yeterli bilgiye sahip olduğunu gösterir. Aksi takdirde, kullanılarak sunucu tarafından alınabilecek ek arabirimler istemci tarafından `IDebugPortRequest2::QueryInterface` sağlanmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
