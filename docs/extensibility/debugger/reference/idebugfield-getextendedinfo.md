---
description: Bu yöntem, bir alan hakkında genişletilmiş bilgiler alır.
title: IDebugField::GetExtendedInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54cdd5b8c57e6aaf9e28832b21dd82430ed98d38
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088828"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Bu yöntem, bir alan hakkında genişletilmiş bilgiler alır.

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
[in] Döndürülen bilgileri seçer. Geçerli değerler:

|Değer|Açıklama|
|-----------|-----------------|
|`guidConstantValue`|Bayt dizisi olarak değer.|
|`guidConstantType`|Tür imzası olarak türü.|

`prgBuffer`\
[out] Genişletilmiş bilgileri döndürür.

`pdwLen`\
[in, out] Genişletilmiş bilgilerin boyutunu bayt cinsinden döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Şu anda bu yöntem yalnızca bir sabitin türünü veya değerini döndürür. Çağıranın COM'un işlevini (C++) veya (C#) çağırarak içinde döndürülen `prgBuffer` `CoTaskMemFree` arabelleği <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> serbest bırakacağı gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
