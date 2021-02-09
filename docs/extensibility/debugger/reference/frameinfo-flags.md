---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcdb555e4355d6f22c8218f98899c01b3b3e2e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904778"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Yığın çerçeve nesnesi hakkında alınacak bilgileri belirtir.

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
Alanı başlatın/kullanın `m_bstrFuncName` .

`FIF_RETURNTYPE`\
Alanı başlatın/kullanın `m_bstrReturnType` .

`FIF_ARGS`\
Alanı başlatın/kullanın `m_bstrArgs` .

`FIF_LANGUAGE`\
Alanı başlatın/kullanın `m_bstrLanguage` .

`FIF_MODULE`\
Alanı başlatın/kullanın `m_bstrModule` .

`FIF_STACKRANGE`\
`m_addrMin`Ve `m_addrMax` (yığın aralığı) alanlarını başlatın/kullanın.

`FIF_FRAME`\
Alanı başlatın/kullanın `m_pFrame` .

`FIF_DEBUGINFO`\
Alanı başlatın/kullanın `m_fHasDebugInfo` .

`FIF_STALECODE`\
Alanı başlatın/kullanın `m_fStaleCode` .

`FIF_ANNOTATEDFRAME`\
Alanı başlatın/kullanın `m_fAnnotatedFrame` .

`FIF_DEBUG_MODULEP`\
Alanı başlatın/kullanın `m_pModule` .

`FIF_FUNCNAME_FORMAT`\
İşlev adını biçimlendirir. Sonuç `m_bstrFunName` alanda döndürülür ve başka hiçbir alan doldurulmaz.

`FIF_FUNCNAME_RETURNTYPE`\
Alana dönüş türünü ekler `m_bstrFuncName` .

`FIF_FUNCNAME_ARGS`\
Bağımsız değişkenleri `m_bstrFuncName` alana ekler.

`FIF_FUNCNAME_LANGUAGE`\
Alana dili ekler `m_bstrFuncName` .

`FIF_FUNCNAME_MODULE`\
Alana modül adını ekler `m_bstrFuncName` .

`FIF_FUNCNAME_LINES`\
Alana satır sayısını ekler `m_bstrFuncName` .

`FIF_FUNCNAME_OFFSET`\
`m_bstrFuncName`Belirtilirse, satırın başından itibaren bayt cinsinden değeri ekler `FIF_FUNCNAME_LINES` . `FIF_FUNCNAME_LINES`Belirtilmezse veya satır numaraları yoksa, işlevin başından itibaren bayt cinsinden sapmayı ekler.

`FIF_FUNCNAME_ARGS_TYPES`\
Her işlev bağımsız değişkeninin türünü `m_bstrFuncName` alana ekler.

`FIF_FUNCNAME_ARGS_NAMES`\
Her işlev bağımsız değişkeninin adını `m_bstrFuncName` alana ekler.

`FIF_FUNCNAME_ARGS_VALUES`\
Her işlev bağımsız değişkeninin değerini `m_bstrFuncName` alana ekler.

`FIF_FUNCNAME_ARGS_ALL`\
Tüm bağımsız değişkenlerin türünü, adını ve değerini `m_bstrFuncName` alana ekler.

`FIF_ARGS_TYPES`\
Bağımsız değişken türleri alınır ve biçimlendirilir.

`FIF_ARGS_NAMES`\
Bağımsız değişken adları alınır ve biçimlendirilir.

`FIF_ARGS_VALUES`\
Bağımsız değişken değerleri alınır ve biçimlendirilir.

`FIF_ARGS_ALL`\
Tüm bağımsız değişkenlerin türünü, adını ve değerini alın ve biçimlendirin.

`FIF_ARGS_NOFORMAT`\
Bağımsız değişkenlerin biçimlendirilmediğini belirtir (örneğin, bağımsız değişken listesi etrafına açılış ve kapanış parantezleri eklemeyin ve bağımsız değişkenler arasında bir ayırıcı ekleyin).

`FIF_ARGS_NO_FUNC_EVAL`\
Bağımsız değişken değerleri alınırken işlev (özellik) değerlendirmesinin kullanılmayacağını belirtir.

`FIF_FILTER_NON_USER_CODE`\
Hata ayıklama altyapısı Kullanıcı olmayan kod çerçevelerini filtreleyerek dahil edilmez.

`FIF_ARGS_NO_TOSTRING`\
`ToString()`İşlev bağımsız değişkenlerini döndürürken işlev değerlendirmesine veya biçimlendirmeye izin vermeyin.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Çerçeve bilgileri barındırma işlemi yerine barındırılan uygulama etki alanından alınmalıdır.

## <a name="remarks"></a>Açıklamalar
Bu bayraklar, [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) yapısında veya yapılarında hangi alanların başlatıldığını göstermek Için [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) ve [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) yöntemlerine geçirilir.

Bu bayraklar Ayrıca, [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) yapısının hangi alanlarının kullanıldığını ve yapı döndürüldüğünde geçerli olduğunu göstermek için de kullanılır. Bu değerler, bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
