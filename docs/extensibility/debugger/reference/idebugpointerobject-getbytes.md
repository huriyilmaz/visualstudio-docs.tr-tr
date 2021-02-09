---
title: 'Ihata ayıklama Gpoınterobject:: GetBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1961aaf45478f25ed8eb55d8eda91a5c4eafc4dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852953"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Ardışık bayt dizisi olarak işaret edilen değeri alır.

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
'ndaki İşaret edilen nesnenin başından itibaren bayt cinsinden bir konum.

`dwCount`\
'ndaki Alınacak bayt sayısı.

`pBytes`\
[in, out] Değerin işaret ettiği nesnenin verilen uzaklığında başlayarak ardışık bayt dizisi olarak değer ile doldurulmuş bir dizi.

`pdwBytes`\
dışı Gerçekten alınan bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, bu [Ihata ayıklama Gpoınterobject](../../../extensibility/debugger/reference/idebugpointerobject.md) tarafından temsil edilen işaretçi temel bir türe veya basit türlerin basit bir dizisine (yani basit bir bayt dizisiyle temsil edilebilir bir dizi) işaret ediyorsa kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
