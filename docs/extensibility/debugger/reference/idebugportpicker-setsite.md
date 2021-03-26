---
description: Hizmet sağlayıcıyı ayarlar.
title: 'Idebugportpicker:: SetSite | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a442c438f233187265c90e724f57e8681b95556
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072266"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Hizmet sağlayıcıyı ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

## <a name="parameters"></a>Parametreler
`pSP`\
'ndaki Hizmet sağlayıcısının arabirimine başvuru.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem diğer yöntemler çağrılmadan önce çağrılacaktır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
