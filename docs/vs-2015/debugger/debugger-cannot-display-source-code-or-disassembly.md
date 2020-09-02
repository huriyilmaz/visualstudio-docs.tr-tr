---
title: Hata ayıklayıcı kaynak kodu veya ayrıştırılmış kod görüntüleyemiyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ce4460aecb634523de02f2e3f6929b206b415e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186501"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Hata Ayıklayıcı Kaynak Kodu veya Ayrıştırılmış Kodu Görüntüleyemez
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hata şunu okur:  
  
 Hata ayıklayıcı, yürütmenin durdurulduğu geçerli konum için kaynak kodu veya ayrıştırılmış kod görüntüleyemiyor.  
  
 Bu hata iletisi, birkaç nedenden dolayı oluşabilir:  
  
- Kaynak kodu olmayan bir konumda bir kesme noktasına isabet ediyor, ancak ayrıştırılmış derlemeyi desteklemeyen bir dilde hata ayıklaması yapmış olabilirsiniz. **Kesme noktaları** penceresini açın, kesme noktasını bulun ve silin.  
  
- Betikte hata ayıklaması yapıyorsanız, programınızda iş parçacığı olmadığı sürece bir kesme noktasına ulaşırsınız. Hata ayıklamayı sürdürmek için **Hata Ayıkla** menüsünden **adımla** veya **devam et** ' i seçin.  
  
- Güvenlik konuları hata ayıklayıcının yığın, iş parçacığı, kayıt ve diğer bağlam bilgilerini hata ayıklamakta olduğunuz programdan okumasını engellemiş olabilir. Bir Web uygulamasında hata ayıklaması yapıyorsanız ve sanal dizine erişmek için doğru izinlere sahip değilseniz bu durum büyük olasılıkla gerçekleşir. Sanal dizin için güvenliği anonim olarak ayarlayıp yeniden deneyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı temelleri](../debugger/debugger-basics.md)   
 [Visual Studio 'da hata ayıklama](../debugger/debugging-in-visual-studio.md)   
 [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)
