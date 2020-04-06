---
title: IEnumDebugObjects::GetCount | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::GetCount
helpviewer_keywords:
- IEnumDebugObjects::GetCount method
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1475652e340ff793dc900ab11563c0c1ad82c9b1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716357"
---
# <a name="ienumdebugobjectsgetcount"></a>IEnumDebugObjects::GetCount
Bu yöntem numaralandırmadaki öğe sayısını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parametreler
`pcelt`\
[çıkış] Numaralandırmadaki eleman sayısını verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, yalnızca Sonraki, Klonlama, Atlama ve Sıfırlama'nın uygulanması gerektiğini belirten alışılmış COM numaralandırma arabiriminin bir parçası değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
