---
description: Bir yığın çerçevesi nesnesi hakkında almak için bilgileri belirtir.
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c51d36ca9900731f816961f4cedf362762d26c5267666bbe5c3135d730dbd85
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403201"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Bir yığın çerçevesi nesnesi hakkında almak için bilgileri belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FRAMEINFO_FLAGS {
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
public enum enum_FRAMEINFO_FLAGS {
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
alanını `m_bstrFuncName` başlat/kullan.

`FIF_RETURNTYPE`\
alanını `m_bstrReturnType` başlat/kullan.

`FIF_ARGS`\
alanını `m_bstrArgs` başlat/kullan.

`FIF_LANGUAGE`\
alanını `m_bstrLanguage` başlat/kullan.

`FIF_MODULE`\
alanını `m_bstrModule` başlat/kullan.

`FIF_STACKRANGE`\
ve `m_addrMin` `m_addrMax` (yığın aralığı) alanlarını başlatma/kullanma.

`FIF_FRAME`\
alanını `m_pFrame` başlat/kullan.

`FIF_DEBUGINFO`\
alanını `m_fHasDebugInfo` başlat/kullan.

`FIF_STALECODE`\
alanını `m_fStaleCode` başlat/kullan.

`FIF_ANNOTATEDFRAME`\
alanını `m_fAnnotatedFrame` başlat/kullan.

`FIF_DEBUG_MODULEP`\
alanını `m_pModule` başlat/kullan.

`FIF_FUNCNAME_FORMAT`\
İşlev adını biçimler. Sonuç alanında döndürülür `m_bstrFunName` ve başka alan doldurulmaz.

`FIF_FUNCNAME_RETURNTYPE`\
Alana dönüş türünü `m_bstrFuncName` ekler.

`FIF_FUNCNAME_ARGS`\
Alana bağımsız değişkenleri `m_bstrFuncName` ekler.

`FIF_FUNCNAME_LANGUAGE`\
Dili alana `m_bstrFuncName` ekler.

`FIF_FUNCNAME_MODULE`\
Modül adını alana `m_bstrFuncName` ekler.

`FIF_FUNCNAME_LINES`\
Alana satır sayısını `m_bstrFuncName` ekler.

`FIF_FUNCNAME_OFFSET`\
`m_bstrFuncName`Belirtilmişse, alana satırın başından bayt cinsinden uzaklığı `FIF_FUNCNAME_LINES` ekler. `FIF_FUNCNAME_LINES`Belirtilmezse veya satır numaraları kullanılamıyorsa, işlevin başındaki uzaklığı bayt cinsinden ekler.

`FIF_FUNCNAME_ARGS_TYPES`\
Alana her işlev bağımsız değişkeninin türünü `m_bstrFuncName` ekler.

`FIF_FUNCNAME_ARGS_NAMES`\
Alana her işlev bağımsız değişkeninin adını `m_bstrFuncName` ekler.

`FIF_FUNCNAME_ARGS_VALUES`\
Alana her işlev bağımsız değişkeninin değerini `m_bstrFuncName` ekler.

`FIF_FUNCNAME_ARGS_ALL`\
Alana tüm bağımsız değişkenlerin türünü, adını ve değerini `m_bstrFuncName` ekler.

`FIF_ARGS_TYPES`\
Bağımsız değişken türleri alınır ve biçimlendirildi.

`FIF_ARGS_NAMES`\
Bağımsız değişken adları alınır ve biçimlendirildi.

`FIF_ARGS_VALUES`\
Bağımsız değişken değerleri alınır ve biçimlendirildi.

`FIF_ARGS_ALL`\
Tüm bağımsız değişkenlerin türünü, adını ve değerini alın ve biçimlendirin.

`FIF_ARGS_NOFORMAT`\
Bağımsız değişkenlerin biçimlendirilenene (örneğin, bağımsız değişken listesinin çevresine açma ve kapatma parantezleri ekleme veya bağımsız değişkenler arasında ayırıcı ekleme) belirtir.

`FIF_ARGS_NO_FUNC_EVAL`\
Bağımsız değişken değerleri alınırken işlev (özellik) değerlendirmesinin kullanılmamesi gerektiğini belirtir.

`FIF_FILTER_NON_USER_CODE`\
Hata ayıklama altyapısı, kullanıcı olmayan kod çerçevelerini dahil edilecek şekilde filtrelemektir.

`FIF_ARGS_NO_TOSTRING`\
İşlev bağımsız değişkenleri `ToString()` döndüren işlev değerlendirmesine veya biçimlendirmesine izin verme.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Çerçeve bilgileri barındırma işlemi yerine barındırılan uygulama-etki alanından al olmalıdır.

## <a name="remarks"></a>Açıklamalar
Bu [bayraklar, FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapısında veya yapılarında hangi alanların başlatıldığına işaret etmek için [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) ve [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) yöntemlerine geçirildi.

Bu bayraklar, yapı döndürülürken [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapısının hangi alanlarının ve geçerli olduğunu belirtmek için de kullanılır. Bu değerler bitwise ile birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
