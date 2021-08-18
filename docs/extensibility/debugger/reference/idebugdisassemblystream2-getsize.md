---
description: Bu ayırt derleme akışının yönergelerindeki boyutu alır.
title: 'IDebugDisassemblyStream2:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2702b092102cc0a918a1604c79b27885d1e002a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111274"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Bu ayırt derleme akışının yönergelerindeki boyutu alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSize( 
   UINT64* pnSize
);
```

```csharp
int GetSize( 
   out ulong pnSize
);
```

## <a name="parameters"></a>Parametreler
`pnSize`\
dışı Yönergelerde, boyutunu döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemden döndürülen değer, daha sonra [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) yöntemine geçirilen bir [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapıları dizisi ayırmak için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Okuyamaz](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
