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
ms.openlocfilehash: 20f7003bbcd319a6a8487d496697d3dcd0b7a18a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548427"
---
# <a name="network-usage"></a>Ağ Kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio **ağ** Tanılama Aracı, [Windows. Web. http API 'si](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx)kullanılarak gerçekleştirilen ağ işlemleriyle ilgili verileri toplar. Verilerin çözümlenmesi, erişim ve kimlik doğrulama sorunları, yanlış önbellek kullanımı ve kötü ekran ve indirme performansı gibi sorunları çözmenize yardımcı olabilir.  
  
 Ağ aracı yalnızca Windows Evrensel platform uygulamalarını destekler. Diğer platformlar Şu anda desteklenmiyor.  
  
> [!NOTE]
> Ağ aracının daha ayrıntılı bir açıklaması için bkz. [Visual Studio 'nun Ağ aracını tanıtma](https://devblogs.microsoft.com/visualstudio/?m=20155).  
  
## <a name="collecting-network-tool-data"></a>Ağ aracı verileri toplanıyor  
 **Ağ** aracını Visual Studio bilgisayarında açık bir Visual Studio projesiyle çalıştırmalısınız.  
  
1. Projeyi Visual Studio'da açın.  
  
2. Menüsünde **Hata Ayıkla/performans profili Oluşturucu...** öğesine tıklayın. **Ağ**' ı seçin ve ardından **Başlat**' ı seçin.  
  
3. Ağ aracı, uygulamanızın HTTP trafiğini toplamaya başlar.  
  
    Uygulamanızı çalıştırırken, sol bölmedeki Özet görünümü, yakalanan HTTP işlemlerinin bir listesini otomatik olarak görüntüler. Sağ bölmedeki Ayrıntılar panelinde daha fazla bilgi görmek için Özet görünümünde bir öğe seçin.  
  
4. Uygulamayı kapatmak için **Durdur** ' ı seçin.  
  
   Rapor penceresi şuna benzer görünmelidir:  
  
   ![Ağ penceresi](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Verileri analiz etme  
 Uygulamanızın çalıştığı sırada veya uygulama kapatıldıktan sonra bile, Özet görünümünde görünen ağ işlemlerinden herhangi birini seçerek yakalanan HTTP trafiğini çözümleyebilirsiniz.  
  
 **Ağ** Özeti Görünümü, uygulamanızın çalıştırıldığı her bir ağ işleminin verilerini gösterir. Listeyi sıralamak için bir sütun üst bilgisi seçin ya da **Içerik türü** filtre görünümünde görüntülenecek içerik türlerini seçin.  
  
 Fiddler gibi üçüncü taraf araçları tarafından tüketilen bir JSON dosyası oluşturmak için **farklı kaydet har** ' ı seçin.  
  
 **Ağ** ayrıntıları görünümleri Özet görünümünde bir ağ işlemi hakkında daha fazla bilgi görüntüler.  
  
 ![Ağ aracı ayrıntıları bölmesi](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|Ad|Açıklama|  
|-|-|  
|**Üst bilgiler**|Olayın istek üstbilgileri hakkında bilgi.|  
|**Gövde**|İstek ve yanıt yükü verileri.|  
|**Parametreler**|Sorgu dizesi parametre adları ve değerleri.|  
|**Özgü**|Yanıt ve istek tanımlama bilgisi verileri.|  
|**Zamanlama**|Seçilen kaynakları alırken aşamaların bir grafiği.|  
  
 Ağ **Özet** çubuğu, herhangi bir noktada görüntülenen ağ işlemlerinin sayısını, ne kadar veri aktarıldığını, ne kadar zaman aktarılacağını ve kaç hatanın (4xx veya 5xx yanıtı) görünür olduğunu gösterir.  
  
### <a name="analysis-tips"></a>Analiz ipuçları  
 Bu araç, ağla ilgili analizler çalıştırırken yararlı olabilecek bazı bölgeleri vurgular:  
  
1. Önbellekten tam olarak sunulan istekler **alındı** sütununda **(önbellekten)** olarak gösterilir. Bu, önbelleği Kullanıcı bant genişliğini kaydetmek için etkin bir şekilde kullanıp kullanmayacağınızı ya da yanıtları yanlışlıkla önbelleğe alma ve güncel olmayan verilerle uygulamanızın son kullanıcısını sağlama işlemleri yapılıp yapılmayacağını belirlemenize yardımcı olabilir.  
  
2. Hata yanıtları (4xx veya 5xx), **sonuçlar** sütununda kırmızı durum kodu ile gösterilir ve ayrıca Özet çubuğunda vurgulanır. Bu, uygulamanızdaki birçok olası istek arasında hata belirlemeyi kolaylaştırır.  
  
3. Yanıt oldukça yazdırma düğmesi (gövde sekmesi içinde), içeriğin okunabilirliğini artırarak JSON, XML, HTML, CSS, JavaScript ve TypeScript yanıt yükleri aracılığıyla ayrıştırmanıza yardımcı olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma araçlarını hata ayıklama olmadan Çalıştır](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Visual Studio blogu: Visual Studio 'nun ağ denetçisini tanıtma](https://blogs.msdn.com/b/visualstudio/)   
 [Channel 9 videosu: VS tanılama araçları – yeni ağ profili Oluşturucu](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
