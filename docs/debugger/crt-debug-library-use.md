---
title: CRT hata ayıklama kitaplığı kullanımı | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7e58f65f174c549f6992e9218d7ad692634e20d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72435875"
---
# <a name="crt-debug-library-use"></a>CRT Hata Ayıklama Kitaplığı Kullanımı
C çalışma zamanı kitaplığı kapsamlı hata ayıklama desteği sağlar. CRT hata ayıklama kitaplıklarından birini kullanmak için [/Debug](/cpp/build/reference/debug-generate-debug-info) ile bağlantı oluşturmanız ve **/MDD**, **/MTD**veya **/LDD**ile derlemeniz gerekir.

## <a name="remarks"></a>Açıklamalar
 CRT hata ayıklama için ana tanımları ve makroları CRTDBG. h üstbilgi dosyasında bulabilirsiniz.

 CRT hata ayıklama kitaplıklarının işlevleri hata ayıklama bilgileri ([/Z7,/ZD,/Zi,/ZI (hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format)) ve iyileştirme olmadan derlenir. Bazı işlevler, bunlara geçirilen parametreleri doğrulamak için onay onayları içerir ve kaynak kodu sağlanır. Bu kaynak kodla, işlevlerin beklenen şekilde çalıştığını doğrulamak ve hatalı parametreleri ya da bellek durumlarını denetlemek için CRT işlevlere ilerleyebiliriz. (Bazı CRT teknolojileri özeldir ve özel durum işleme, kayan nokta ve diğer birkaç yordam için kaynak kodu sağlamaz.)

 Kullanabileceğiniz çeşitli çalışma zamanı kitaplıkları hakkında daha fazla bilgi için bkz. [C çalışma zamanı kitaplıkları](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>Ayrıca Bkz.

- [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md)
- [/MD, /MT, /LD (Çalışma Zamanı Kitaplığını Kullan)](/cpp/build/reference/md-mt-ld-use-run-time-library)