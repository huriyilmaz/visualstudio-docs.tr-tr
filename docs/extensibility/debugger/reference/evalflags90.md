---
description: İfade değerlendirmesini kontrol eden bayraklar için geçerli değerleri numaralar.
title: EVALFLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7d4916f5070792b7169303060b078acca422ef2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153400"
---
# <a name="evalflags90"></a>EVALFLAGS90
İfade değerlendirmesini kontrol eden bayraklar için geçerli değerleri numaralar. Bu numaralama [EVALFLAGS numaralama](../../../extensibility/debugger/reference/evalflags.md) süresini genişleter.

## <a name="syntax"></a>Syntax

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
Varsa dönüş değerinin değerlendirilecek olduğunu belirtir.

`EVAL90_NOSIDEEFFECTS`\
Yan etkilere izin verilmiyor olduğunu belirtir.

`EVAL90_ALLOWBPS`\
Kesme noktalarında durdurmayı belirtir.

`EVAL90_ALLOWERRORREPORT`\
İzin verilen ana bilgisayar hata raporlamasını belirtir. Birincil olarak betikte ifade değerlendirmesi için kullanılır Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
İşlevleri adres olarak değerlendirilmeye, işlevin değerlendirilmesine neden olur.

`EVAL90_NOFUNCEVAL`\
İşlevin değerlendirilmesini önler. Örneğin, ifadesinde `int` belirteci göz önünde `myExpression(int) + 10` bulundurarak. Bu işlev bir adres olarak doğru şekilde değerlendirebilirsiniz ancak değer olarak değerlendirilmez.

`EVAL90_NOEVENTS`\
İfade değerlendirmesi sırasında meydana gelen olayların oturum hata ayıklama yöneticisine (SDM) veya IDE'ye gönderilmez olduğunu belirten bayrak.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Tasarım zamanı ifadesi değerlendirmesini sağlar.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Örtülü değişken oluşturma işlemine izin verir.

`EVAL90_FORCE_EVALUATION_NOW`\
Değerlendirmeyi hemen gerçekleşmesini güçler. Bu, kullanıcı isteği gibi bir itene hizmet vermede yararlıdır.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: Msdbg90.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
