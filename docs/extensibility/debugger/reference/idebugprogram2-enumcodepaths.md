---
description: Kaynak dosyada verilen bir konum için kod yollarının listesini alın.
title: IDebugProgram2::EnumCodePaths | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d5f04a988b7afae1b4b86c38e6fedba4c5d6d896
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057479"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Kaynak dosyada verilen bir konum için kod yollarının listesini alın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>Parametreler
`pszHint`\
[in] IDE'de Kaynak **veya** **Disassembly görünümünde** imlecin altındaki sözcük.

`pStart`\
[in] Geçerli [kod bağlamını temsil eden bir IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi.

`pFrame`\
[in] Geçerli kesme noktasıyla ilişkili yığın çerçevesini temsil eden [bir IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) nesnesi.

`fSource`\
[in] Kaynak görünümünde sıfır olmayan ( `TRUE` ) **veya** `FALSE` **Disassembly** görünümünde ise sıfır ( ).

`ppEnum`\
[out] Kod [yollarının listesini içeren bir IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) nesnesi döndürür.

`ppSafety`\
[out] Seçilen kod yolunun atlanmış olması durumunda kesme noktası olarak ayarlanacak ek bir kod bağlamını temsil eden [bir IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi döndürür. Bu, örneğin, kısa devreli boole ifadesinde ortaya olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kod yolu, programın yürütülmesinde geçerli noktaya almak için çağrılan bir yöntemin veya işlevin adını açıklar. Kod yollarının listesi çağrı yığınını temsil eder.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
