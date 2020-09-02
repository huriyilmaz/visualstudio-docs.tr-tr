---
title: 'Nasıl yapılır: Grafik Tanılama kayıttan yürütme makinesini değiştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb14fb4017ea1df6659b9a1a0ac093cd7cf7e0b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811168"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Nasıl yapılır: Grafik Tanılama Kayıttan Yürütme Makinesini Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik bilgilerini yerel makinenizi kullanarak veya uzak bir makine ya da cihaz kullanarak çalabilirsiniz.  
  
## <a name="choosing-a-playback-machine"></a>Kayıttan yürütme makinesi seçme  
 Kayıttan yürütme makinesi, grafik olaylarını bir grafik günlüğünden çalmak için kullanılan bir makine veya cihazdır. Genellikle, yerel makine en kullanışlı seçenektir, ancak bir işleme sorunu yakalandığı makineden farklı donanım veya sürücü sürümlerine sahip bir makinede yeniden oluşturmayabilir; Bu durumda, sorunu daha iyi üreten bir uzaktan kayıttan yürütme makinesi seçebilir ve Tanılama için geliştirme makinenizi kullanmaya devam edebilirsiniz.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Grafik bilgilerini kayıttan yürütmek üzere yerel makineyi kullanmak için  
  
1. Grafik günlüğü Belgesi penceresinde, **kayıttan yürütme makinesi** bağlantısını seçin. **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusu görüntülenir.  
  
2. **El Ile yapılandırma**altında, **Adres** özelliğinde, girin `localhost` .  
  
3. **Kimlik doğrulama modu** özelliğini **yok**olarak ayarlayın.  
  
4. **Seç** düğmesini seçin.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Grafik bilgilerini kayıttan yürütmek üzere uzak bir makineyi kullanmak için  
  
1. Grafik günlüğü Belgesi penceresinde, **kayıttan yürütme makinesi** bağlantısını seçin. **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusu görüntülenir.  
  
2. **El Ile yapılandırma**altında, **Adres** özelliğinde, grafik bilgilerini kayıttan yürütmek için kullanmak Istediğiniz makinenin veya cihazın Windows etkı alanı adını veya IP adresini girin.  
  
3. Kayıttan yürütme makinesiyle bağlantıyı güvenli hale getirmek için kullanmak istediğiniz yetkilendirme türünü belirtin.  
  
    - Windows kimlik doğrulaması için **kimlik doğrulama modu** özelliğini **Windows**olarak ayarlayın.  
  
    - Kimlik doğrulaması yok için **kimlik doğrulama modu** özelliğini **yok**olarak ayarlayın.  
  
4. **Seç** düğmesini seçin.  
  
> [!NOTE]
> **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusu ayrıca, geliştirme makinenize doğrudan bağlı olan veya aynı alt ağda olan uzaktan hata ayıklama hedeflerini de gösterebilir. Bu uzaktan hata ayıklama hedeflerinden birini el ile yapılandırmadan Grafik Tanılama kayıttan yürütme makinesi olarak kullanabilirsiniz. **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusunda istediğiniz hedefi seçin ve ardından **Seç** düğmesini seçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Grafik Günlük Belgesi](../debugger/graphics-log-document.md)
