---
title: 'IDebugBreakpointChecksumRequest2:: ıschecksumenabled | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2::IsChecksumEnabled
ms.assetid: 8b1853b5-745c-4cd6-88a9-ce0673971bb0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c30dbdbc3c75f22331c61f42dbe9aa829020725
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735113"
---
# <a name="idebugbreakpointchecksumrequest2ischecksumenabled"></a>IDebugBreakpointChecksumRequest2::IsChecksumEnabled
Bu belge için sağlama toplamı etkinleştirilip etkinleştirilmediğini belirler.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT IsChecksumEnabled(
   BOOL *pfChecksumEnabled
);
```

```csharp
public int IsChecksumEnabled(
   out int pfChecksumEnabled
);
```

## <a name="parameters"></a>Parametreler
`pfChecksumEnabled`\
dışı Sağlama toplamı etkinse doğru döndürür; Aksi takdirde, FALSE döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)
