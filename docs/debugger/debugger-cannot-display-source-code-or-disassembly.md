---
title: Hata ayıklayıcı kaynak kodu veya ayrıştırılmış kod görüntüleyemiyor
description: "\"Hata ayıklayıcı, yürütmenin durdurulduğu geçerli konum için kaynak kodu veya ayrıştırılmış kod görüntülenemiyor\" iletisinin nedenlerini inceleyin."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: dbff97b4967b7fd614e52418316f5ea2ab06320814f1f961cb1515052e444e95
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404589"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Hata Ayıklayıcı Kaynak Kodu veya Ayrıştırılmış Kodu Görüntüleyemez
Bu hata şunu okur:

 Hata ayıklayıcı, yürütmenin durdurulduğu geçerli konum için kaynak kodu veya ayrıştırılmış kod görüntüleyemiyor.

 Bu hata iletisi, birkaç nedenden dolayı oluşabilir:

- Kaynak kodu olmayan bir konumda bir kesme noktasına isabet ediyor, ancak ayrıştırılmış derlemeyi desteklemeyen bir dilde hata ayıklaması yapmış olabilirsiniz. **Kesme noktaları** penceresini açın, kesme noktasını bulun ve silin.

- Betikte hata ayıklaması yapıyorsanız, programınızda iş parçacığı olmadığı sürece bir kesme noktasına ulaşırsınız. Hata ayıklamayı sürdürmek için **Hata Ayıkla** menüsünden **adımla** veya **devam et** ' i seçin.

- Güvenlik konuları hata ayıklayıcının yığın, iş parçacığı, kayıt ve diğer bağlam bilgilerini hata ayıklamakta olduğunuz programdan okumasını engellemiş olabilir. Bir Web uygulamasında hata ayıklaması yapıyorsanız ve sanal dizine erişmek için doğru izinlere sahip değilseniz bu durum büyük olasılıkla gerçekleşir. Sanal dizin için güvenliği anonim olarak ayarlayıp yeniden deneyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)