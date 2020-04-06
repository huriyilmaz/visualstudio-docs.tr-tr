---
title: EVALFLAGS90 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01951885541ba4acce33f3e4f06f7106116ccc62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737096"
---
# <a name="evalflags90"></a>EVALFLAGS90
İfade değerlendirmesini denetleyen bayraklar için geçerli değerleri okurum. Bu numaralandırma [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) numaralandırmasını genişletir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>Alanlar
`EVAL90_RETURNVALUE`\
Varsa iade değerinin değerlendirilmesi gerektiğini belirtir.

`EVAL90_NOSIDEEFFECTS`\
Yan etkilere izin verilmemesini belirtir.

`EVAL90_ALLOWBPS`\
Kesme noktalarında durmayı belirtir.

`EVAL90_ALLOWERRORREPORT`\
Bu hatanın ana bilgisayara bildirilmesine izin verilip verilmediğini belirtir. Öncelikle Internet Explorer'da komut dosyasında ifade değerlendirmesi için kullanılır.

`EVAL90_FUNCTION_AS_ADDRESS`\
İşlev çağırmak yerine işlevleri adres olarak değerlendirilmeye zorlar.

`EVAL90_NOFUNCEVAL`\
Fonksiyonun değerlendirilmesini engeller. Örneğin, ifadedeki `int` `myExpression(int) + 10`belirteci göz önünde bulundurun. Bu işlev doğru bir adres olarak değerlendirilebilir, ancak bir değer olarak değil.

`EVAL90_NOEVENTS`\
İfade değerlendirmesi sırasında meydana gelen olayların oturum hata ayıklama yöneticisine (SDM) veya IDE'ye gönderilmemesi gerektiğini belirtmek için işaretle.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Tasarım zamanı ifade değerlendirmesini sağlar.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Örtük değişken oluşturulmasına izin verir.

`EVAL90_FORCE_EVALUATION_NOW`\
Değerlendirmenin hemen gerçekleşmesine zorlar. Bu, kullanıcı isteği gibi bir isteğe hizmet verirken yararlıdır.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: Msdbg90.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
