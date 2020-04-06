---
title: IDebugField::GetSize | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9f19a914de2e74613e987753c8062215fd0d0403
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728802"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
Bu yöntem baytlar halinde bir alan boyutunu alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSize( 
   DWORD* pdwSize
);
```

```csharp
int GetSize(
   out uint pdwSize
);
```

## <a name="parameters"></a>Parametreler
`pdwSize`\
[çıkış] Boyutu döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Tüm alanların bir türü vardır ve tüm türler bir boyuta sahiptir. Örneğin, bayt türüne sahip bir alanın boyutu 1 baytdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
