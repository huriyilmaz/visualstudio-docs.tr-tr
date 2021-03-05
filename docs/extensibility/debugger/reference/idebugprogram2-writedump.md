---
description: Bir dosyaya döküm yazar.
title: 'IDebugProgram2:: WriteDump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0e4c90034d19635993196a0cd00ffcb06f26433
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171933"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Bir dosyaya döküm yazar.

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
'ndaki Döküm türünü belirten [DumpType](../../../extensibility/debugger/reference/dumptype.md) numaralandırmasındaki bir değer (örneğin, kısa veya uzun).

`pszDumpUrl`\
'ndaki Döküm yazılacak URL. Genellikle, bu biçimindedir `file://c:\path\filename.ext` , ancak geçerli BIR URL olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Program dökümü genellikle geçerli yığın çerçevesini, yığının kendisini, programda çalışan iş parçacıklarının bir listesini ve programın sahip olduğu tüm belleği içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
