---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 333535a727d88f66346ba4c94cb08b4917b8acfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722731"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Bir dosyaya döküm yazar.

## <a name="syntax"></a>Söz dizimi

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
