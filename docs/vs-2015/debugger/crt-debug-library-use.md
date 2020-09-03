---
title: CRT hata ayıklama kitaplığı kullanımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7e14a181b432dede3f00a4465d40154fdb393bb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697854"
---
# <a name="crt-debug-library-use"></a>CRT Hata Ayıklama Kitaplığı Kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C çalışma zamanı kitaplığı kapsamlı hata ayıklama desteği sağlar. CRT hata ayıklama kitaplıklarından birini kullanmak için [/Debug](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103) ile bağlantı oluşturmanız ve **/MDD**, **/MTD**veya **/LDD**ile derlemeniz gerekir.  
  
## <a name="remarks"></a>Açıklamalar  
 CRT hata ayıklama için ana tanımları ve makroları CRTDBG. h üstbilgi dosyasında bulabilirsiniz.  
  
 CRT hata ayıklama kitaplıklarının işlevleri hata ayıklama bilgileri ([/Z7,/ZD,/Zi,/ZI (hata ayıklama bilgileri biçimi)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)) ve iyileştirme olmadan derlenir. Bazı işlevler, bunlara geçirilen parametreleri doğrulamak için onay onayları içerir ve kaynak kodu sağlanır. Bu kaynak kodla, işlevlerin beklenen şekilde çalıştığını doğrulamak ve hatalı parametreleri ya da bellek durumlarını denetlemek için CRT işlevlere ilerleyebiliriz. (Bazı CRT teknolojileri özeldir ve özel durum işleme, kayan nokta ve diğer birkaç yordam için kaynak kodu sağlamaz.)  
  
 Visual C++ yüklediğinizde, sabit diskinizde C çalışma zamanı kitaplığı kaynak kodu yükleme seçeneğiniz vardır. Kaynak kodu yüklemezseniz, CD-ROM ' u CRT işlevlere adım adım açmanız gerekir.  
  
 Kullanabileceğiniz çeşitli çalışma zamanı kitaplıkları hakkında daha fazla bilgi için bkz. [C çalışma zamanı kitaplıkları](https://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CRT hata ayıklama teknikleri](../debugger/crt-debugging-techniques.md)   
 [/MD,/MT,/LD (çalışma zamanı kitaplığını kullan)](https://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)
