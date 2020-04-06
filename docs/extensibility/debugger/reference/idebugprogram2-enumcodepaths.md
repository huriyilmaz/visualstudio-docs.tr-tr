---
title: IDebugProgram2::EnumCodePaths | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b99651811cedbdb8ec0eca5b766e6d75651dd5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723038"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Kaynak dosyadaki belirli bir konumun kod yollarının listesini alır.

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
[içinde] IDE'deki **Kaynak** veya **Sökme** görünümünde imlecin altındaki sözcük.

`pStart`\
[içinde] Geçerli kod bağlamını temsil eden bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi.

`pFrame`\
[içinde] Geçerli kesme noktasıyla ilişkili yığın çerçevesini temsil eden bir [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) nesnesi.

`fSource`\
[içinde] **Kaynak** görünümünde sıfır olmayan (`FALSE``TRUE`) veya () ise **Sökme** görünümünde.

`ppEnum`\
[çıkış] Kod yollarının listesini içeren bir [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) nesnesi döndürür.

`ppSafety`\
[çıkış] Seçilen kod yolunun atlanması durumunda kesme noktası olarak ayarlanacak ek bir kod bağlamını temsil eden bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi döndürür. Bu, örneğin kısa devreboolean ifadesinde gerçekleşebilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kod yolu, programın yürütülmesinde geçerli noktaya ulaşmak için çağrılan bir yöntem veya işlevin adını açıklar. Kod yollarının listesi çağrı yığınını temsil eder.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
