---
title: FRAMEINFO_FLAGS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3510726400623c5ddf3e7a4d58a4903763b91245
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736807"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Yığın çerçevesi nesnesi hakkında alınacak bilgileri belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="fields"></a>Alanlar
`FIF_FUNCNAME`\
`m_bstrFuncName` Alanı başlatma/kullanma.

`FIF_RETURNTYPE`\
`m_bstrReturnType` Alanı başlatma/kullanma.

`FIF_ARGS`\
`m_bstrArgs` Alanı başlatma/kullanma.

`FIF_LANGUAGE`\
`m_bstrLanguage` Alanı başlatma/kullanma.

`FIF_MODULE`\
`m_bstrModule` Alanı başlatma/kullanma.

`FIF_STACKRANGE`\
Initialize/use `m_addrMin` the `m_addrMax` ve (stack range) alanları.

`FIF_FRAME`\
`m_pFrame` Alanı başlatma/kullanma.

`FIF_DEBUGINFO`\
`m_fHasDebugInfo` Alanı başlatma/kullanma.

`FIF_STALECODE`\
`m_fStaleCode` Alanı başlatma/kullanma.

`FIF_ANNOTATEDFRAME`\
`m_fAnnotatedFrame` Alanı başlatma/kullanma.

`FIF_DEBUG_MODULEP`\
`m_pModule` Alanı başlatma/kullanma.

`FIF_FUNCNAME_FORMAT`\
Işlev adını biçimlendirin. Sonuç `m_bstrFunName` alanında döndürülür ve başka alan doldurulur.

`FIF_FUNCNAME_RETURNTYPE`\
`m_bstrFuncName` Alana dönüş türünü ekler.

`FIF_FUNCNAME_ARGS`\
Bağımsız değişkenleri `m_bstrFuncName` alana ekler.

`FIF_FUNCNAME_LANGUAGE`\
`m_bstrFuncName` Dili alana ekler.

`FIF_FUNCNAME_MODULE`\
Modül adını alana `m_bstrFuncName` ekler.

`FIF_FUNCNAME_LINES`\
`m_bstrFuncName` Alana satır sayısını ekler.

`FIF_FUNCNAME_OFFSET`\
Belirtilmişse, satırın `m_bstrFuncName` `FIF_FUNCNAME_LINES` başlangıcından itibaren bayt cinsinden mahsup edilen ofset alana ekler. `FIF_FUNCNAME_LINES` Belirtilmemişse veya satır numaraları yoksa, işlevin başlangıcından itibaren mahsup tonlarını baytlara ekler.

`FIF_FUNCNAME_ARGS_TYPES`\
Her işlev bağımsız değişkeninin `m_bstrFuncName` türünü alana ekler.

`FIF_FUNCNAME_ARGS_NAMES`\
Her işlev bağımsız değişkeninin `m_bstrFuncName` adını alana ekler.

`FIF_FUNCNAME_ARGS_VALUES`\
Her işlev bağımsız değişkeninin `m_bstrFuncName` değerini alana ekler.

`FIF_FUNCNAME_ARGS_ALL`\
`m_bstrFuncName` Alana tüm bağımsız değişkenlerin türünü, adını ve değerini ekler.

`FIF_ARGS_TYPES`\
Bağımsız değişken türleri alınır ve biçimlendirilir.

`FIF_ARGS_NAMES`\
Bağımsız değişken adları alınır ve biçimlendirilir.

`FIF_ARGS_VALUES`\
Bağımsız değişken değerleri alınır ve biçimlendirilir.

`FIF_ARGS_ALL`\
Tüm bağımsız değişkenlerin türünü, adını ve değerini alın ve biçimlendirin.

`FIF_ARGS_NOFORMAT`\
Bağımsız değişkenlerin biçimlendirilmediğini belirtir (örneğin, bağımsız değişken listesinin etrafına açılış ve kapatma parantezleri eklemeyin veya bağımsız değişkenler arasında ayırıcı eklemeyin).

`FIF_ARGS_NO_FUNC_EVAL`\
Bağımsız değişken değerlerini alırken işlev (özellik) değerlendirmesinin kullanılmaması gerektiğini belirtir.

`FIF_FILTER_NON_USER_CODE`\
Hata ayıklama altyapısı, kullanıcı olmayan kod çerçevelerine dahil edilmemek için filtreleme yapmaktır.

`FIF_ARGS_NO_TOSTRING`\
İşlev `ToString()` bağımsız değişkenlerini döndürürken işlev değerlendirmesine veya biçimlendirmeye izin vermeyin.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Çerçeve bilgileri barındırma işlemi yerine barındırılan uygulama etki alanından alınmalıdır.

## <a name="remarks"></a>Açıklamalar
Bu bayraklar, [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapısında veya yapılarında hangi alanların başlatılması gerektiğini belirtmek için [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) ve [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) yöntemlerine geçirilir.

Bu bayraklar, [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapısının hangi alanlarının kullanıldığını belirtmek için de kullanılır ve yapı döndürüldüğünde geçerlidir. Bu değerler biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
