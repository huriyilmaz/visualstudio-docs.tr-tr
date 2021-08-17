---
description: Ardışık bayt dizisi olarak işaret eden değeri alır.
title: IDebugPointerObject::GetBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34b81b01d04ea895b93153a57686a4d784d57b20
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088308"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Ardışık bayt dizisi olarak işaret eden değeri alır.

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
[in] Nesnenin başlangıcına işaret eden bayt cinsinden uzaklık.

`dwCount`\
[in] Alınan bayt sayısı.

`pBytes`\
[in, out] Değeri ardışık bayt dizisi olarak doldurulan bir dizi, işaret ettiği nesneden verilen uzaklığından başlayarak.

`pdwBytes`\
[out] Gerçekte alınan bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, [işaretçi bu IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) tarafından temsil edilen ilkel bir türü veya basit bir temel tür dizisini (basit bir bayt dizisiyle temsil edilen bir dizi) işaret ediyorsa kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
