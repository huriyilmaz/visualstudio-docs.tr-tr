---
title: Hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırın | Microsoft Docs
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b3d50f8fcad0294adec032322229e9dd6cedac2
ms.sourcegitcommit: 8e5b0106061bb43247373df33d0850ae68457f5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88508086"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçları çalıştırma

Visual Studio, performans ölçümü ve profil oluşturma araçlarının bir seçimini sunmaktadır. CPU kullanımı ve bellek kullanımı gibi bazı araçlar, hata ayıklayıcı ile veya olmadan çalışabilir ve derleme yapılandırmalarında yayın veya hata ayıklama yapabilir. Uygulama Zaman Çizelgesi gibi performans profil oluşturucu araçları, hata ayıklama veya sürüm yapılarında çalıştırılabilir. Hata ayıklayıcı ile tümleşik araçlar, Tanılama Araçları penceresi ve olayları sekmesi gibi yalnızca hata ayıklama oturumlarında çalıştırılır.

>[!NOTE]
>Windows 7 ve üzeri ile hata ayıklayıcı olmayan performans araçlarını kullanabilirsiniz. Hata ayıklayıcı ile tümleşik profil oluşturma araçlarını çalıştırmak için Windows 8 veya üzeri gereklidir.

Hata ayıklayıcı olmayan performans profil oluşturucusu ve hata ayıklayıcı ile tümleşik Tanılama Araçları, farklı bilgi ve deneyimler sağlar. Hata ayıklayıcı ile tümleşik araçlar, kesme noktaları ve değişken değerleri gösterir. Hata ayıklayıcı olmayan araçlar, son kullanıcı deneyimine daha yakın sonuçlar verir.

Hangi araçların ve sonuçların kullanılacağına karar vermek için aşağıdakileri göz önünde bulundurun:

- Dosya g/ç veya ağ yanıtlama hızı sorunları gibi dış performans sorunları, hata ayıklayıcıda veya hata ayıklayıcı olmayan araçlarda çok daha farklı bir şekilde görünmez.
- CPU yoğunluklu çağrıların neden olduğu sorunlar için, yayın ve hata ayıklama derlemeleri arasında önemli performans farklılıkları olabilir. Sorunun yayın yapılarında mevcut olup olmadığını denetleyin.
- Sorun yalnızca hata ayıklama derlemeleri sırasında gerçekleşirse, muhtemelen hata ayıklayıcı olmayan araçları çalıştırmanız gerekmez. Yayın derlemesi sorunları için, hata ayıklayıcı araçlarının daha fazla araştırma için yardım edilip edilmeyeceğini belirleyin.
- Yayın yapıları, işlev çağrıları ve sabitler gibi iyileştirmeler sağlar, kullanılmayan kod yollarını ayıklamalar ve hata ayıklayıcı tarafından kullanılamayan yollarla değişkenleri depolar. Hata ayıklayıcı ile tümleşik araçlarındaki performans numaraları, hata ayıklama derlemeleri bu iyileştirmelerin olmadığından daha az doğrudur.
- Hata ayıklayıcı, özel durum ve modül yükleme olayları gibi gerekli hata ayıklama işlemlerini yaptığı için performans sürelerini değiştirir.
- Performans profil oluşturucu araçlarındaki yayın derlemesi performans numaraları en kesin ve doğru. Hata ayıklayıcı ile tümleşik araç sonuçları, hata ayıklama ile ilgili diğer ölçülerle kıyaslamak için en yararlı seçenektir.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Hata ayıklarken profil oluşturma verilerini topla

**Hata ayıklama**  >  **başlatma hata ayıklamayı**seçerek veya **F5**tuşuna basarak, Visual Studio 'da hata ayıklamayı başlattığınızda, varsayılan olarak **Tanılama araçları** pencere görüntülenir. El ile açmak için **Debug**  >  **Windows**  >  **göster tanılama araçları**Hata Ayıkla ' yı seçin. **Tanılama araçları** pencere, olaylar, işlem belleğı ve CPU kullanımı hakkındaki bilgileri gösterir.

![Tanılama Araçları penceresinin ekran görüntüsü](../profiling/media/diagnostictoolswindow.png " Tanılama Araçları Penceresi")

- **Bellek kullanımını**, **UI analizini**ve **CPU kullanımını**görüntüleyip görüntüleyemeyeceğinizi belirlemek için araç çubuğundaki **Ayarlar** simgesini kullanın.

- Daha fazla seçenek içeren **Tanılama Araçları özellik sayfalarını** açmak için **Ayarlar** açılan listesinden **Ayarlar** ' ı seçin.

- Visual Studio Enterprise çalıştırıyorsanız, **araç**  >  **seçenekleri**  >  **IntelliTrace**'e giderek IntelliTrace 'i etkinleştirebilir veya devre dışı bırakabilirsiniz.

Hata ayıklamayı durdurduğunuzda Tanılama oturumu sonlanır.

### <a name="the-events-tab"></a>Olaylar sekmesi

Bir hata ayıklama oturumu sırasında, Tanılama Araçları penceresinin Olaylar sekmesinde oluşan tanılama olayları listelenir. Kategori ön ekleri *kesme noktası*, *Dosya*ve diğerleri, bir kategorinin listesini hızlıca taramanızı sağlar veya ilgilendiğiniz kategorileri atlar.

Belirli olay kategorilerini seçerek veya temizleyerek, olayları görünüm içinde ve dışında filtrelemek için **filtre** açılan listesini kullanın.

![Tanılama olay filtresinin ekran görüntüsü](../profiling/media/diagnosticeventfilter.png "Tanılama olay filtresi")

Olay listesinde belirli bir dizeyi bulmak için arama kutusunu kullanın. Dört olayla eşleşen dize *adı* için bir aramanın sonuçları aşağıda verilmiştir:

![Tanılama olayı aramasının ekran görüntüsü](../profiling/media/diagnosticseventsearch.png "Tanılama olayı arama")

Daha fazla bilgi için, [Tanılama Araçları penceresinin Olaylar sekmesinde arama ve filtreleme](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)bölümüne bakın.

## <a name="collect-profiling-data-without-debugging"></a>Profil oluşturma verilerini hata ayıklama olmadan topla

Performans verilerini hata ayıklama olmadan toplamak için, performans profil Oluşturucu araçlarını çalıştırabilirsiniz.

1. Visual Studio 'da bir proje açıkken, çözüm yapılandırmasını **yayın**olarak ayarlayın ve dağıtım hedefi olarak **yerel Windows hata ayıklayıcısı**'Nı   (veya **yerel makine**) seçin.

1. **Hata ayıklama**  >  **performans profil oluşturucuyu**seçin veya **alt** + **F2**tuşuna basın.

1. Tanılama araçları başlatma sayfasında, çalıştırılacak bir veya daha fazla araç seçin. Yalnızca proje türü, işletim sistemi ve programlama dili için geçerli olan araçlar gösterilir. Bu Tanılama oturumu için devre dışı bırakılan araçları görmek için **tüm araçları göster** ' i seçin.

   ![Tanılama araçlarının ekran görüntüsü](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Tanılama oturumu başlatmak için **Başlat**' ı seçin.

   Oturum çalışırken, bazı araçlar tanılama araçları sayfasındaki gerçek zamanlı verilerin grafiklerini, ayrıca veri toplamayı duraklatma ve sürdürmeye yönelik denetimleri gösterir.

    ![Performans ve Tanılama merkezinde veri toplamanın ekran görüntüsü](../profiling/media/diaghubcollectdata.png "Merkez verileri topla")

1. Tanılama oturumunu sonlandırmak için, **toplamayı durdur**' u seçin.

   Analiz edilen veriler **rapor** sayfasında görünür.

Raporları kaydedebilir ve Tanılama Araçları başlatma sayfasında **son açılan oturumlar** listesinden açabilirsiniz.

![Tanılama Araçları son açılan oturumlar listesinin ekran görüntüsü](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

## <a name="collect-profiling-data-from-the-command-line"></a>Komut satırından profil oluşturma verilerini toplama

Komut satırından performans verilerini ölçmek için, Visual Studio ya da uzak araçlarla birlikte bulunan VSDiagnostics.exe kullanabilirsiniz. Bu, Visual Studio yüklü olmayan sistemlerdeki performans izlemelerini yakalamak veya performans izlemelerinin toplanması için yararlıdır. Ayrıntılı yönergeler için bkz. [komut satırından uygulama performansını ölçme](../profiling/profile-apps-from-command-line.md).