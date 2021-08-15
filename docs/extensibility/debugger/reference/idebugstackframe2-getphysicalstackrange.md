---
description: Bir yığın çerçevesiyle ilişkili fiziksel adres aralığının makineye bağımlı bir gösterimini alır.
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75bba9bd57f544b82dd459ca7e001de8657cbd79a05c3bdc01a6a5d1d72705bd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321603"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Bir yığın çerçevesiyle ilişkili fiziksel adres aralığının makineye bağımlı bir gösterimini alır.

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
[out] Bu yığın çerçevesiyle ilişkili en düşük fiziksel adresi döndürür.

`paddrMax`\
[out] Bu yığın çerçevesiyle ilişkili en yüksek fiziksel adresi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem tarafından döndürülen bilgiler, yığın çerçevelerini sıralamak için oturum hata ayıklama yöneticisi (SDM) tarafından kullanılır.

 Çağrı yığınının aşağı doğru artarak yeni yığın çerçevelerinin giderek daha düşük bellek adreslerinde ekli olduğu varsayılır. Bir çalışma zamanı mimarisi, bu varsayımla eşan fiziksel yığın aralıkları sağlamaktadır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
