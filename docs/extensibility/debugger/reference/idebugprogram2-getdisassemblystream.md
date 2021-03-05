---
description: Bu program veya bu programın bir parçası için ayrıştırma akışını alır.
title: 'IDebugProgram2:: GetDisassemblyStream | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e000ada618c21af865743bfb2bd9fd6b60a80a4b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159932"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Bu program veya bu programın bir parçası için ayrıştırma akışını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDisassemblyStream( 
   DISASSEMBLY_STREAM_SCOPE   dwScope,
   IDebugCodeContext2*        pCodeContext,
   IDebugDisassemblyStream2** ppDisassemblyStream
);
```

```csharp
int GetDisassemblyStream( 
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,
   IDebugCodeContext2             pCodeContext,
   out IDebugDisassemblyStream2   ppDisassemblyStream
);
```

## <a name="parameters"></a>Parametreler
`dwScope`\
'ndaki Ayrıştırılmış akışın kapsamını tanımlayan [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) numaralandırmasından bir değer belirtir.

`pCodeContext`\
'ndaki Ayrıştırılmış birleştirme akışının başlayacağı konumu temsil eden bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi.

`ppDisassemblyStream`\
dışı Ayrıştırılmış derlemeyi temsil eden bir [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. `E_DISASM_NOTSUPPORTED`Bu belirli mimari için ayrıştırılmış derleme desteklenmiyorsa döndürür.

## <a name="remarks"></a>Açıklamalar
 `dwScopes`Parametre `DSS_HUGE` [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) numaralandırma kümesi bayrağıyla ayarlandıysa, ayrıştırılmış bir dosyanın veya modülün tamamı için, örneğin, çok sayıda ayrıştırma yönergesi döndürmesi beklenir. `DSS_HUGE`Bayrak ayarlanmamışsa, ayrıştırılmış derlemenin küçük bir bölgeye göre sınırlandırılan genellikle tek bir işlevde olması beklenir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
