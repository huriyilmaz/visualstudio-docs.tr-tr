---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3df924c6c8a4373082d61575e4ad8a7ec3f161d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719663"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Yığın çerçevesiyle ilişkili fiziksel adres aralığının makineye bağımlı bir temsilini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>Parametreler
`paddrMin`\
[çıkış] Bu yığın çerçevesiyle ilişkili en düşük fiziksel adresi döndürür.

`paddrMax`\
[çıkış] Bu yığın çerçevesiyle ilişkili en yüksek fiziksel adresi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemle döndürülen bilgiler, yığın çerçevelerini sıralamak için oturum hata ayıklama yöneticisi (SDM) tarafından kullanılır.

 Çağrı yığınının küçültüldüğü, yani yeni yığın karelerinin giderek daha alttaki bellek adreslerine eklendiği varsayılıyor. Çalışma zamanı mimarisi, bu varsayımla eşleşen fiziksel yığın aralıkları sağlamalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
