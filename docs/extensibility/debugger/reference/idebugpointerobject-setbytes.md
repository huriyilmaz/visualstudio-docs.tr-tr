---
title: IDebugPointerObject::SetBytes | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dede3ee5291afbfbeab4d6e60dcbd56e205e4526
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725507"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Ardışık bayt lar dizisinin işaret ettiği değeri ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>Parametreler
`dwStart`\
[içinde] Bir ofset, bayt, nesnenin başından itibaren işaret.

`dwCount`\
[içinde] Ayarlanan bayt sayısı.

`pBytes`\
[içinde] Yeni değeri temsil eden bir dizi bayt. Bu değer, verilen ofset başlayarak nesneye depolanır.

`pdwBytes`\
[çıkış] Ayarlanan bayt sayısını verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) tarafından temsil edilen işaretçi ilkel bir türe veya basit bir ilkel tür dizisine (diğer bir şekilde, basit bir bayt dizisiyle temsil edilebilen bir dizi) işaret ederse bu yöntem kullanılır. Bu `IDebugPointerObject` nesne null bir başvuru olamaz (bellekte bir adrese işaret etmelidir).

## <a name="see-also"></a>Ayrıca bkz.
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
