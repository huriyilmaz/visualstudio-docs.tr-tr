---
title: IDebugDisassemblyStream2::Oku | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a4f5c0250405c2e2a0314b52c4cbc64d749fc0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732100"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Sökme akışındaki geçerli konumdan başlayarak yönergeleri okur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Read( 
   DWORD                     dwInstructions,
   DISASSEMBLY_STREAM_FIELDS dwFields,
   DWORD*                    pdwInstructionsRead,
   DisassemblyData*          prgDisassembly
);
```

```csharp
int Read( 
   uint                           dwInstructions,
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,
   out uint                       pdwInstructionsRead,
   DisassemblyData[]              prgDisassembly
);
```

## <a name="parameters"></a>Parametreler
`dwInstructions`\
[içinde] Sökülecek talimatların sayısı. Bu değer aynı zamanda `prgDisassembly` dizinin maksimum uzunluğudur.

`dwFields`\
[içinde] [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) numaralandırmadan hangi alanların doldurululeceğini gösteren `prgDisassembly` bayrakların birleşimi.

`pdwInstructionsRead`\
[çıkış] Fiilen sökülen yönergelerin sayısını verir.

`prgDisassembly`\
[çıkış] Sökülen kodla doldurulan bir dizi [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapıları, sökülen yönerge başına bir yapı. Bu dizinin uzunluğu `dwInstructions` parametre tarafından dikte edilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Geçerli kapsamda kullanılabilen maksimum yönerge sayısı [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) yöntemini arayarak elde edilebilir.

 Bir sonraki talimatın okunduğu geçerli [konum, Arama](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) yöntemini arayarak değiştirilebilir.

 Yönergeleri `DSF_OPERANDS_SYMBOLS` sökerken sembol `DSF_OPERANDS` adlarının `dwFields` kullanılması gerektiğini belirtmek için parametredeki bayrağa bayrak eklenebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
