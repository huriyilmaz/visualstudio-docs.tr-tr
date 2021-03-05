---
description: Bu yöntem, bir alanla ilgili genişletilmiş bilgileri alır.
title: 'IDebugField:: Geiddeınfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 98d522222d57a0828ebcefe446262033d2d8dfc1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151968"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Bu yöntem, bir alanla ilgili genişletilmiş bilgileri alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>Parametreler
`guidExtendedInfo`\
'ndaki Döndürülecek bilgileri seçer. Geçerli değerler:

|Değer|Açıklama|
|-----------|-----------------|
|`guidConstantValue`|Değer bir bayt dizisi olarak.|
|`guidConstantType`|Tür imzası olarak yazın.|

`prgBuffer`\
dışı Genişletilmiş bilgileri döndürür.

`pdwLen`\
[in, out] Genişletilmiş bilgilerin boyutunu bayt cinsinden döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Şu anda, bu yöntem yalnızca bir sabitin türünü veya değerini döndürür. Çağıran, `prgBuffer` com `CoTaskMemFree` Işlevi (C++) veya <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#) çağırarak ' de döndürülen arabelleği boşaltmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
