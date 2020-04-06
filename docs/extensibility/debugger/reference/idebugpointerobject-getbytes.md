---
title: IDebugPointerObject::GetBytes | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17bc39f65d7c4c42b4f958b559df7c5b7d3bbdf7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725521"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Ardışık baytlar bir dizi olarak işaret değeri alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>Parametreler
`dwStart`\
[içinde] Bir ofset, bayt, nesnenin başından itibaren işaret.

`dwCount`\
[içinde] Alınacak bayt sayısı.

`pBytes`\
[içinde, dışarı] Işaret edilen nesneden verilen ofset ten başlayarak, ardışık bayt lar dizisi olarak değerle doldurulan bir dizi.

`pdwBytes`\
[çıkış] Alınan bayt sayısını verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) tarafından temsil edilen işaretçi ilkel bir türe veya basit bir ilkel tür dizisine (diğer bir şekilde, basit bir bayt dizisiyle temsil edilebilen bir dizi) işaret ederse bu yöntem kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
