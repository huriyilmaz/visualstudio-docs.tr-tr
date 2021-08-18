---
title: Grafik tanılama kayıttan yürütme makinesini Değiştir
description: Grafik bilgilerini, yerel makinenizi kullanarak veya sorunu daha iyi üreten bir uzak makine veya cihaz kullanarak grafik günlüğünden yürütün.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 70ac7cbc1081e2c7a9a04c96393a5ac6af51cede
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133841"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Nasıl yapılır: Grafik Tanılama Kayıttan Yürütme Makinesini Değiştirme
Grafik bilgilerini yerel makinenizi kullanarak veya uzak bir makine ya da cihaz kullanarak çalabilirsiniz.

## <a name="choosing-a-playback-machine"></a>Kayıttan yürütme makinesi seçme
 Kayıttan yürütme makinesi, grafik olaylarını bir grafik günlüğünden çalmak için kullanılan bir makine veya cihazdır. Genellikle, yerel makine en kullanışlı seçenektir, ancak bir işleme sorunu yakalandığı makineden farklı donanım veya sürücü sürümlerine sahip bir makinede yeniden oluşturmayabilir; Bu durumda, sorunu daha iyi üreten bir uzaktan kayıttan yürütme makinesi seçebilir ve Tanılama için geliştirme makinenizi kullanmaya devam edebilirsiniz.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Grafik bilgilerini kayıttan yürütmek üzere yerel makineyi kullanmak için

1. Grafik günlüğü Belgesi penceresinde, **kayıttan yürütme makinesi** bağlantısını seçin. **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusu görüntülenir.

2. **El Ile yapılandırma** altında, **Adres** özelliğinde, girin `localhost` .

3. **Kimlik doğrulama modu** özelliğini **yok** olarak ayarlayın.

4. **Seç** düğmesini seçin.

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Grafik bilgilerini kayıttan yürütmek üzere uzak bir makineyi kullanmak için

1. Grafik günlüğü Belgesi penceresinde, **kayıttan yürütme makinesi** bağlantısını seçin. **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusu görüntülenir.

2. **el ile yapılandırma** altında, **adres** özelliğinde, grafik bilgilerini kayıttan yürütmek için kullanmak istediğiniz makinenin veya cihazın Windows etki alanı adını veya ıp adresini girin.

3. Kayıttan yürütme makinesiyle bağlantıyı güvenli hale getirmek için kullanmak istediğiniz yetkilendirme türünü belirtin.

    - Windows kimlik doğrulaması için, **kimlik doğrulama modu** özelliğini **Windows** olarak ayarlayın.

    - Kimlik doğrulaması yok için **kimlik doğrulama modu** özelliğini **yok** olarak ayarlayın.

4. **Seç** düğmesini seçin.

> [!NOTE]
> **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusu ayrıca, geliştirme makinenize doğrudan bağlı olan veya aynı alt ağda olan uzaktan hata ayıklama hedeflerini de gösterebilir. Bu uzaktan hata ayıklama hedeflerinden birini el ile yapılandırmadan Grafik Tanılama kayıttan yürütme makinesi olarak kullanabilirsiniz. **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusunda istediğiniz hedefi seçin ve ardından **Seç** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Grafik Günlük Belgesi](graphics-log-document.md)