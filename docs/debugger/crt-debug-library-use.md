---
title: CRT Hata Ayıklama Kitaplığı | Microsoft Docs
description: C çalışma zamanı (CRT) kitaplığının hata ayıklama çalışmalarınızı nasıl desteklediğini ve CRT hata ayıklama kitaplıklarını kullanmak için neleri gerektiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/03/2019
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 09f4805785983818b1475f3435b2c26feb17604e0275c9c25ce8faff27ccd34c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345835"
---
# <a name="crt-debug-library-use"></a>CRT Hata Ayıklama Kitaplığı Kullanımı
C çalışma zamanı kitaplığı kapsamlı hata ayıklama desteği sağlar. CRT hata ayıklama kitaplıklarından birini kullanmak için [/DEBUG](/cpp/build/reference/debug-generate-debug-info) ile bağlantı kurarak **/MDd , /MTd** veya **/LDd ile derlemeniz gerekir.** 

## <a name="remarks"></a>Açıklamalar
 CRT hata ayıklama için ana tanımlar ve makrolar CRTDBG.h üst bilgi dosyasında bulunabilir.

 CRT hata ayıklama kitaplıklarında işlevler hata ayıklama bilgileriyle ([/Z7, /Zd, /Zi, /ZI (Hata](/cpp/build/reference/z7-zi-zi-debug-information-format)Ayıklama Bilgileri Biçimi) ) ve iyileştirme olmadan derlenmiş. Bazı işlevler, geçirilen parametreleri doğrulamak için onaylar içerir ve kaynak kodu sağlanır. Bu kaynak koduyla, işlevlerin beklediğiniz gibi çalıştığını onaylamak için CRT işlevlerine adımlayabilir ve hatalı parametreleri veya bellek durumlarını kontrol edin. (Bazı CRT teknolojileri özeldir ve özel durum işleme, kayan nokta ve diğer birkaç yordam için kaynak kodu sağlamaz.)

 Kullanabileceğiniz çeşitli çalışma zamanı kitaplıkları hakkında daha fazla bilgi için bkz. [C Run-Time Kitaplıkları.](/cpp/c-runtime-library/crt-library-features)

## <a name="see-also"></a>Ayrıca bkz.

- [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md)
- [/MD, /MT, /LD (Run-Time Kitaplığını Kullan)](/cpp/build/reference/md-mt-ld-use-run-time-library)