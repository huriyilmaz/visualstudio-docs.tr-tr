---
title: CV_CFL_LANG | Microsoft Docs
description: Hata ayıklama arabirimi CV_CFL_LANG SDK'sı içinde uygulamanın veya bağlı modülün kod dilini belirten enumeration türü hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8bb3192316bf3dbdda7ee06f9bfa9a159ab8d982
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630681"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
Uygulamanın veya bağlı modülün kaynak kod dilini belirtir.

## <a name="syntax"></a>Syntax

```C++
typedef enum CV_CFL_LANG {
    CV_CFL_C       = 0x00,
    CV_CFL_CXX     = 0x01,
    CV_CFL_FORTRAN = 0x02,
    CV_CFL_MASM    = 0x03,
    CV_CFL_PASCAL  = 0x04,
    CV_CFL_BASIC   = 0x05,
    CV_CFL_COBOL   = 0x06,
    CV_CFL_LINK    = 0x07,
    CV_CFL_CVTRES  = 0x08,
    CV_CFL_CVTPGD  = 0x09,
    CV_CFL_CSHARP  = 0x0A,
    CV_CFL_VB      = 0x0B,
    CV_CFL_ILASM   = 0x0C,
    CV_CFL_JAVA    = 0x0D,
    CV_CFL_JSCRIPT = 0x0E,
    CV_CFL_MSIL    = 0x0F,
    CV_CFL_HLSL    = 0x10
} CV_CFL_LANG;
```

## <a name="elements"></a>Öğeler
CV_CFL_C dili C'dir.

CV_CFL_CXX dili C++ dilidir.

CV_CFL_FORTRAN dili FORTRAN'dır.

CV_CFL_MASM dili Microsoft Macro Assembler'dır.

CV_CFL_PASCAL dili Pascal'dır.

CV_CFL_BASIC dili BASIC'tir.

CV_CFL_COBOL dili COBOL'dır.

CV_CFL_LINK Application, bir linker tarafından oluşturulan modüldür.

CV_CFL_CVTRES Uygulaması, CVTRES aracıyla dönüştürülen bir kaynak modülüdür.

CV_CFL_CVTPGD Uygulaması, CVTPGD aracıyla oluşturulan POGO için iyileştirilmiş bir modüldür.

CV_CFL_CSHARP dili C# şeklindedir.

CV_CFL_VB dili Visual Basic.

CV_CFL_ILASM dili ara dil derlemesidir (diğer bir ifade, Ortak Dil Çalışma Zamanı (CLR) derlemesi).

CV_CFL_JAVA dili Java'dır.

CV_CFL_JSCRIPT dili Jscript'tir.

CV_CFL_MSIL dili bilinmeyen bir Microsoft Ara Dilidir (MSIL), [/LTCG (Bağlantı](/cpp/build/reference/ltcg-link-time-code-generation) Zamanı Kod Oluşturma) anahtarının kullanımı sonucu olabilir.

CV_CFL_HLSL dili Üst Düzey Gölgelendirici Dili'dir.

## <a name="remarks"></a>Açıklamalar
Bu numaralamada yer alan değerler [IDiaSymbol::get_language yöntemine yapılan bir çağrıyla](../../debugger/debug-interface-access/idiasymbol-get-language.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst.h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
