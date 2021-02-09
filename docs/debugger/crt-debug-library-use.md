---
title: CRT hata ayıklama kitaplığı kullanımı | Microsoft Docs
description: C çalışma zamanı (CRT) kitaplığının hata ayıklama çabalarınızı nasıl desteklediğini ve CRT hata ayıklama kitaplıklarını kullanmak için ne yapmanız gerektiğini öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: fe50082f8ff62c4a19b7725facc18f43d672e353
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865715"
---
# <a name="crt-debug-library-use"></a>CRT Hata Ayıklama Kitaplığı Kullanımı
C çalışma zamanı kitaplığı kapsamlı hata ayıklama desteği sağlar. CRT hata ayıklama kitaplıklarından birini kullanmak için [/Debug](/cpp/build/reference/debug-generate-debug-info) ile bağlantı oluşturmanız ve **/MDD**, **/MTD** veya **/LDD** ile derlemeniz gerekir.

## <a name="remarks"></a>Açıklamalar
 CRT hata ayıklama için ana tanımları ve makroları CRTDBG. h üstbilgi dosyasında bulabilirsiniz.

 CRT hata ayıklama kitaplıklarının işlevleri hata ayıklama bilgileri ([/Z7,/ZD,/Zi,/ZI (hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format)) ve iyileştirme olmadan derlenir. Bazı işlevler, bunlara geçirilen parametreleri doğrulamak için onay onayları içerir ve kaynak kodu sağlanır. Bu kaynak kodla, işlevlerin beklenen şekilde çalıştığını doğrulamak ve hatalı parametreleri ya da bellek durumlarını denetlemek için CRT işlevlere ilerleyebiliriz. (Bazı CRT teknolojileri özeldir ve özel durum işleme, kayan nokta ve diğer birkaç yordam için kaynak kodu sağlamaz.)

 Kullanabileceğiniz çeşitli çalışma zamanı kitaplıkları hakkında daha fazla bilgi için bkz. [C Run-Time kitaplıkları](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>Ayrıca bkz.

- [CRT hata ayıklama teknikleri](../debugger/crt-debugging-techniques.md)
- [/MD,/MT,/LD (Run-Time kitaplığı kullanın)](/cpp/build/reference/md-mt-ld-use-run-time-library)