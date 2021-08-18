---
description: Ayrık akışta geçerli konumdan başlayarak yönergeleri okur.
title: IDebugDisassemblyStream2::Read | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d39c8db44d4f59d9eeb7ef93877bcb64e029e23
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064467"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Ayrık akışta geçerli konumdan başlayarak yönergeleri okur.

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
[in] Parçalara ayırabilecek yönergelerin sayısı. Bu değer aynı zamanda dizinin maksimum uzunluğu `prgDisassembly` dadır.

`dwFields`\
[in] Hangi alanların doldurulması [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) bayrakların bir birleşimi. `prgDisassembly`

`pdwInstructionsRead`\
[out] Aslında biriktirildi yönergelerin sayısını döndürür.

`prgDisassembly`\
[out] Bir dizi [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısı, her bir ayrık yönerge için bir yapı olan, bir kod olarak doldurulan bir kod. Bu dizinin uzunluğu parametresi tarafından `dwInstructions` dikte edildi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Geçerli kapsamda kullanılabilen en fazla yönergelerin sayısı [GetSize yöntemi çağrılarak elde](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) edilir.

 Sonraki yönergenin okunma [konumu, Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) yöntemi çağrılarak değiştirilebilir.

 Yönergelerin biriktirirken sembol adlarının kullan gerektiğini belirtmek için parametresinde `DSF_OPERANDS_SYMBOLS` `DSF_OPERANDS` `dwFields` bayrağına bayrağı eklenebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
