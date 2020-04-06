---
title: IDebugField::GetExtendedInfo | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc414dd57e86149e38d7c85d11252eb93efced51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728867"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Bu yöntem, bir alan hakkında genişletilmiş bilgi alır.

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
[içinde] Döndürülecek bilgileri seçer. Geçerli değerler:

|Değer|Açıklama|
|-----------|-----------------|
|`guidConstantValue`|Bayt dizisi olarak değer.|
|`guidConstantType`|Tür imzası olarak türü.|

`prgBuffer`\
[çıkış] Uzatılmış bilgileri verir.

`pdwLen`\
[içinde, dışarı] Uzatılan bilgilerin boyutunu baytlarla döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Şu anda, bu yöntem yalnızca bir sabitin türünü veya değerini döndürür. Arayan, COM'un `prgBuffer` `CoTaskMemFree` işlevini (C++) veya <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#) arayarak döndürülen arabelleği serbest etmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
