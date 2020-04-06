---
title: IDebugProgram2::WriteDump | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 333535a727d88f66346ba4c94cb08b4917b8acfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722731"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Dosyaya bir döküm yazar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>Parametreler
`DumpType`\
[içinde] [DumpTYPE](../../../extensibility/debugger/reference/dumptype.md) numaralandırmasından, örneğin kısa veya uzun döküm türünü belirten bir değer.

`pszDumpUrl`\
[içinde] Dökümü yazmak için URL. Genellikle, bu `file://c:\path\filename.ext`şeklindedir, ancak geçerli bir URL olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Program dökümü genellikle geçerli yığın çerçevesi, yığın kendisi, programda çalışan iş parçacıklarının bir listesini ve muhtemelen programın sahip olduğu herhangi bir bellek içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
