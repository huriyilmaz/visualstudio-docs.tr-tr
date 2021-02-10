---
title: Snapshot Debugger için başlangıç sayfası
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f237f121d0bd0a5eaa57cd2b198024d22951622
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942002"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Snapshot Debugger kullanmaya başlama

Visual Studio Snapshot Debugger artık hizmetinize bağlı ve hata ayıklamayla ilgili yardım almak için anlık görüntüler toplamaya başlayabilirsiniz.

Snapshot Debugger kullanmak için, kodunuzda bazı anlık görüntü noktaları ayarlayın, anlık görüntüleri toplamaya başlamak için düğmeye tıklayın ve ardından senaryonuzu çalıştırın. Bir anlık görüntü noktası belirlediğiniz kod çalıştırıldığında, uygulamanızın bir anlık görüntüsü alınır. Ardından Tanılama Araçları penceresinde Visual Studio 'da üzerine tıklayarak anlık görüntüyü açın. Artık, yerel olarak hizmetinize benzer şekilde, anlık görüntüde hata ayıklaması yapabilirsiniz. Ayrıntılı yönergeler için okumaya devam edin.

## <a name="collect-and-view-snapshots"></a>Anlık görüntüleri toplama ve görüntüleme

Snapshot Debugger, uygulamanızın anlık görüntülerini toplar. Anlık görüntüler, zaman içinde bir noktada uygulamanızın resimleri gibidir. Kodda bir anlık görüntü noktası ayarlayarak, Visual Studio 'ya ne zaman ve nereye bir anlık görüntü toplanacağını söylemiş olursunuz. Anlık görüntü noktasında araştırdığınız sorunun anlık görüntüsünü aldığınızdan emin olmak için ihtiyacınız olan tüm koşulları ayarlarsınız.

### <a name="set-a-snappoint"></a>Anlık görüntü noktası ayarla

1. Kod Düzenleyicisi 'nde, bir anlık görüntü noktası ayarlamak için ilgilendiğiniz kod satırının yanındaki sol cilt payı tıklatın. Bu kodun çalıştırılacağını bildiğiniz bir kod olduğundan emin olun.

    ![Düzenleyicide bir anlık görüntü noktası ayarlama](../media/snapshot-startpage-set-snappoint.png)

    Sola tıkladığınızda, mor altıon görünür.

2. Anlık görüntü noktasını açmak için **toplamayı Başlat** ' a tıklayın.

### <a name="open-a-snapshot"></a>Anlık görüntü aç

1. Anlık görüntü noktası isabet edildiğinde, sağdaki Tanılama Araçları penceresinde bir anlık görüntü görüntülenir. Pencere açılmazsa, **Hata Ayıkla**  >  **Windows**  >  **göster tanılama araçları** öğesini seçerek açabilirsiniz.

    ![Tanılama Araçları penceresinde anlık görüntü](../media/snapshot-startpage-diagsession-window.png)

2. Anlık görüntüye çift tıklayarak açın.

### <a name="inspect-snapshot-data"></a>Anlık görüntü verilerini İnceleme

Bu görünümden, veri Ipuçlarını görüntülemek, Yereller, Izler ve çağrı yığını pencerelerini kullanmak ve ayrıca ifadeleri değerlendirmek için değişkenlerin üzerine geldiğinizde arama yapabilirsiniz.

Web sitesinin kendisi de canlı ve son kullanıcılar etkilenmemektedir. Varsayılan olarak, anlık görüntü noktası başına yalnızca bir anlık görüntü yakalanır. Diğer bir deyişle, anlık görüntü yakalandıktan sonra, anlık görüntü noktası kapanır. Anlık görüntü noktasında başka bir anlık görüntü yakalamak istiyorsanız, **koleksiyonu Güncelleştir**' e tıklayarak anlık görüntü noktasını yeniden açabilirsiniz.

### <a name="set-a-logpoint"></a>Logpoint ayarlama

1. Bir anlık görüntü noktası simgesine (mor altıon) sağ tıklayın ve **Ayarlar**' ı seçin.

2. Anlık görüntü **noktası ayarları** penceresinde **Eylemler**' i seçin.

    ![Anlık görüntü noktası koşulları](../media/snapshot-startpage-logpoint.png)

3. **İleti** alanına, günlüğe kaydetmek istediğiniz bir günlük iletisi girin. Ayrıca, günlük iletinizde değişkenleri küme ayraçları içine yerleştirerek değerlendirebilirsiniz.

    **Çıkış penceresi gönder**' i seçerseniz, oturum noktası isabet edildiğinde ileti Tanılama Araçları penceresinde görünür.

    **Uygulama günlüğüne gönder**' i seçerseniz ileti, `System.Diagnostics.Trace` `ILogger` oturum noktası isabet edildiğinde App Insights gibi (veya .NET Core) iletileri görebileceğiniz her yerde görüntülenir.

## <a name="learn-more"></a>Daha Fazla Bilgi Edinin

[Belgeler sayfasında](../debug-live-azure-applications.md)Snapshot Debugger hakkında daha fazla bilgi edinebilirsiniz. Hataları bulmayı kolaylaştırmak için koşulları ayarlama hakkında daha fazla bilgi edinin.

## <a name="dont-show-me-this-again"></a>Bunu bir daha gösterme

Snapshot Debugger bağladığınızda Snapshot debugger başlangıç sayfasını hiçbir zaman göstermek için, **Araçlar** seçenekler Snapshot Debugger **oturum başlatma seçeneğinde ' Başlarken ' sayfasını göster** seçeneğini değiştirin  >    >  .

![Snapshot Debugger araç seçeneği sayfası](../media/snapshot-startpage-tools-options.png)
