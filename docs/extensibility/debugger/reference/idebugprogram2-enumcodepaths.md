---
title: 'IDebugProgram2:: EnumCodePaths | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723038"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Kaynak dosyadaki belirli bir konum için kod yollarının listesini alır.

## <a name="syntax"></a>Söz dizimi

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
'ndaki IDE 'deki **kaynak** veya **ayrıştırma** görünümünde imlecin altında bulunan sözcük.

`pStart`\
'ndaki Geçerli kod bağlamını temsil eden bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi.

`pFrame`\
'ndaki Geçerli kesme noktasıyla ilişkili yığın çerçevesini temsil eden bir [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) nesnesi.

`fSource`\
'ndaki Kaynak görünümünde sıfır olmayan ( `TRUE` ) **Source** veya `FALSE` **ayrıştırma** görünümünde sıfır ().

`ppEnum`\
dışı Kod yollarının bir listesini içeren bir [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) nesnesi döndürür.

`ppSafety`\
dışı Seçilen kod yolunun atlanması durumunda kesme noktası olarak ayarlanacak ek kod bağlamını temsil eden bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi döndürür. Örneğin, kısa devre dışı olarak kabul edilen bir Boole ifadesi söz konusu olduğunda bu durum oluşabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kod yolu, programın yürütüldüğü geçerli noktaya ulaşmak için çağrılan bir yöntemin veya işlevin adını tanımlar. Kod yollarının listesi çağrı yığınını temsil eder.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
