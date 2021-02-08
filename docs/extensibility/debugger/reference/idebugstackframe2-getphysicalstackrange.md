---
title: 'IDebugStackFrame2:: GetPhysicalStackRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c4c4bbc468403aaf94aca1b5133a732e0c050b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837482"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Yığın çerçevesiyle ilişkili fiziksel adres aralığının makineye bağlı temsilini alır.

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
dışı Bu yığın çerçevesiyle ilişkili en düşük fiziksel adresi döndürür.

`paddrMax`\
dışı Bu yığın çerçevesiyle ilişkili en yüksek fiziksel adresi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemin döndürdüğü bilgiler, yığın çerçevelerini sıralamak için oturum hata ayıklama Yöneticisi (SDM) tarafından kullanılır.

 Çağrı yığınının arttığına, yani yeni yığın çerçevelerinin artan bellek adreslerinde daha düşük bir şekilde ekleneceğini kabul edilir. Çalışma zamanı mimarisi, bu varsayım ile eşleşen fiziksel yığın aralıkları sağlamalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
