---
title: Ağ kullanımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6de07c705129aaef705d0c9651d53fdf35e6d0c0
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850746"
---
# <a name="network-usage"></a>Ağ Kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio **ağ** Tanılama aracını kullanarak gerçekleştirilen ağ işlemleri hakkındaki verileri toplar [Windows.Web.Http API](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx). Verileri çözümleme, erişim ve kimlik doğrulaması ile ilgili sorunlar, yanlış önbellek kullanımı ve görüntü gibi sorunları çözmek ve indirme performansını yardımcı olabilir.  
  
 Ağ aracı yalnızca Windows Evrensel platform uygulamalarını destekler. Diğer platformlar, şu anda desteklenmiyor.  
  
> [!NOTE]
> Ağ aracının daha ayrıntılı bir açıklaması için bkz. [Visual Studio 'nun Ağ aracını tanıtma](https://devblogs.microsoft.com/visualstudio/?m=20155).  
  
## <a name="collecting-network-tool-data"></a>Ağ aracı verileri toplanıyor  
 Çalıştırmalısınız **ağ** aracı ile Visual Studio bilgisayarda açık bir Visual Studio projesi.  
  
1. Projeyi Visual Studio'da açın.  
  
2. Menüsünde **Hata Ayıkla/performans profili Oluşturucu...** öğesine tıklayın. **Ağ**' ı seçin ve ardından **Başlat**' ı seçin.  
  
3. Ağ aracı, uygulamanızın HTTP trafiğini toplamaya başlar.  
  
    Uygulamanızı çalıştırma gibi Özet görünümü sol bölmesinde otomatik olarak yakalanan HTTP işlemlerini listesini görüntüler. Özet görünümünde ayrıntılar bölmesini sağ bölmede, daha fazla bilgi görmek için bir öğe seçin.  
  
4. Seçin **Durdur** uygulamayı kapatmak için.  
  
   Rapor penceresi şuna benzer görünmelidir:  
  
   ![Ağ penceresi](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Verileri çözümleme  
 Uygulamanız çalışırken veya bile uygulama, Özet görünümünde görüntülenen ağ işlemlerden birini seçerek kapatıldıktan sonra yakalanan HTTP trafiği analiz edebilirsiniz.  
  
 **Ağ** Özet görünümü, uygulamanızın çalıştırmada her ağ işlemi için verileri gösterilir. Listeyi sıralamak için sütun başlığını seçin ya da görüntülemek için içerik türlerini seçin **içerik türü** filtre görünümü.  
  
 Seçin **HAR olarak Kaydet** Fiddler gibi üçüncü taraf araçları tarafından tüketilebilecek bir JSON dosyası oluşturmak için.  
  
 **Ağ** ayrıntıları görünümlerini Özet görünümünde ağ işlemi hakkında daha fazla bilgi görüntüler.  
  
 ![Ağ aracı ayrıntıları bölmesi](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|||  
|-|-|  
|**Üst bilgileri**|İstek üst bilgilerini ilgili olay bilgileri.|  
|**Gövde**|İstek ve yanıt yük verisi.|  
|**Parametreler**|Sorgu dizesi parametresi adları ve değerleri.|  
|**Çerezler**|Yanıt ve istek tanımlama bilgisi verisi.|  
|**Zamanlamaları**|Bir grafik, seçilen kaynaklar alınıyor aşamaları.|  
  
 Ağ **Özet** çubuğu gösterir ne kadar verinin aktarıldığı, belirli bir anda, görüntülenen ağ işlemlerinin sayısı ne kadar süre geçtiğini bunları ve kaç hatalar (istek yanıt veren 4xx veya 5xx) indirmek için görünür.  
  
### <a name="analysis-tips"></a>Çözümleme ipuçları  
 Bu araç, ağla ilgili analizler çalıştırırken yararlı olabilecek bazı bölgeleri vurgular:  
  
1. Önbellekten tam olarak sunulan istekleri olarak gösterilen **(önbellekten)** içinde **alınan** sütun. Bu, önbelleğin etkili bir şekilde kullanıcı bant genişliğinden tasarruf etmek kullanmanıza veya yanlışlıkla yanıtları önbelleğe alma ve güncel olmayan verileri ile uygulamanızın son kullanıcı sağlama belirlemenize yardımcı olabilir.  
  
2. Hata yanıtları (4xx veya 5xx), **sonuçlar** sütununda kırmızı durum kodu ile gösterilir ve ayrıca Özet çubuğunda vurgulanır. Bu, birçok olası istekler arasında kolay nokta hataları uygulamanızı sağlar.  
  
3. Yanıt oldukça yazdırma düğmesi (gövde sekmesi içinde), içeriğin okunabilirliğini artırarak JSON, XML, HTML, CSS, JavaScript ve TypeScript yanıt yükleri aracılığıyla ayrıştırmanıza yardımcı olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma araçlarını hata ayıklama olmadan çalıştır](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Visual Studio blogu: Visual Studio 'nun ağ denetçisini tanıtma](https://blogs.msdn.com/b/visualstudio/)   
 [Channel 9 videosu: VS tanılama araçları – yeni ağ profili Oluşturucu](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
