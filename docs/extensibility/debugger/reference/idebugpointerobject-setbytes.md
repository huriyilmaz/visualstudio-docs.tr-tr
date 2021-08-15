---
description: Ardışık bayt dizilerinden işaret eden değeri ayarlar.
title: IDebugPointerObject::SetBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 61152240fe28fbf2b5329bfc5aebd1fbf06dca4a235c3595379b3604621b8bc5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121277198"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Ardışık bayt dizilerinden işaret eden değeri ayarlar.

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
[in] Nesnenin başlangıcına işaret eden bayt cinsinden uzaklık.

`dwCount`\
[in] Ayar için bayt sayısı.

`pBytes`\
[in] Yeni değeri temsil eden bayt dizisi. Bu değer, verilen uzaklık ile başlayarak nesnede depolanır.

`pdwBytes`\
[out] Gerçekte ayarlanmış bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, [işaretçi bu IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) tarafından temsil edilen ilkel bir türü veya basit bir ilkel tür dizisini (basit bir bayt dizisiyle temsil edilen bir dizi) işaret ediyorsa kullanılır. Bu `IDebugPointerObject` nesne null başvuru olamaz (bellekte bir adrese işaret ediyor olmalıdır).

## <a name="see-also"></a>Ayrıca bkz.
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
