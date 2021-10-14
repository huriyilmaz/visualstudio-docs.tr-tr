---
title: Hata ayıklayıcı kaynak kodunu veya farklı bir şekilde görüntüleyemez
description: "\"Hata ayıklayıcı, yürütmenin durdurulmuş olduğu geçerli konum için kaynak kodu görüntüleyemez veya parçalara ayıramaz\" iletisine bakın."
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
ms.openlocfilehash: de2a86522119eaf07660b42e8ecda0e6cdf5024d
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129971848"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Hata Ayıklayıcı Kaynak Kodu veya Ayrıştırılmış Kodu Görüntüleyemez
Bu hata şunları okur:

 Hata ayıklayıcısı, yürütmenin durdurulmuş olduğu geçerli konum için kaynak kodunu veya disassembly kodunu görüntüleyemez.

 Bu hata iletisi çeşitli nedenlerle oluşabilir:

- Kaynak kodu olmayan bir konumda kesme noktasıyla karşılaşmış olabilir ve bu sırada ayrım desteği olmayan bir dilde hata ayıklamış olabilirsiniz. Kesme **noktaları penceresini açın,** kesme noktası bulun ve silin.

- Betikte hata ayıklarken programda iş parçacığı yoksa bir kesme noktasıyla karşılaşmış olabilirsiniz. Hata **ayıklamayı** devam **etmek için** Hata Ayıklama **menüsünden** Adım veya Devam'ı seçin.

- Güvenlikle ilgili dikkat edilmesi gerekenler hata ayıklayıcının hata ayıklarken programdan yığın, iş parçacığı, kayıt ve diğer bağlam bilgilerini okumasını önleyene kadar olabilir. Büyük olasılıkla bir Web uygulamasında hata ayıklarsanız ve sanal dizine erişmek için doğru izniniz yoksa bu durumla karşılaşabilirsiniz. Sanal dizinin güvenliğini Anonim olarak ayarlayın ve yeniden deneyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)