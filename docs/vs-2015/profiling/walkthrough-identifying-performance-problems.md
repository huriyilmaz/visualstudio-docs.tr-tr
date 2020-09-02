---
title: 'İzlenecek yol: performans sorunlarını tanımlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 58
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bc4135b9b861a460295c67c576405edd5c63211
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695011"
---
# <a name="walkthrough-identifying-performance-problems"></a>İzlenecek Yol: Performans Sorunlarını Tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, performans sorunlarını belirlemek için bir uygulamanın profilini oluşturmayı gösterir.  
  
 Bu kılavuzda, yönetilen bir uygulamanın profilini oluşturma ve örnekleme ve izleme kullanarak uygulamadaki performans sorunlarını yalıtmak ve tanımlamak için adım adım ilerleyerek adım adım ilerleyerek.  
  
 Bu kılavuzda, aşağıdaki adımları izleyeceğinizi göreceksiniz:  
  
- Örnekleme yöntemini kullanarak bir uygulama profili oluşturma.  
  
- Bir performans sorununu bulmak ve onarmak için örneklenmiş profil oluşturma sonuçlarını çözümleyin.  
  
- İzleme yöntemini kullanarak bir uygulamayı profil haline getirme.  
  
- Bir performans sorununu bulmak ve onarmak için, işaretlenmiş profil oluşturma sonuçlarını çözümleyin.  
  
## <a name="prerequisites"></a>Ön koşullar  
  
- C# ' nin ara anlama.  
  
- [PeopleTrax örneğinin](../profiling/peopletrax-sample-profiling-tools.md)bir kopyası.  
  
  Profil oluşturma tarafından sağlanan bilgilerle çalışmak için, hata ayıklama sembol bilgilerinin kullanılabilir olması en iyisidir.  
  
## <a name="profiling-by-using-the-sampling-method"></a>Örnekleme yöntemi kullanılarak profil oluşturma  
 Örnekleme, etkin işlevi belirlemede, söz konusu işlemin düzenli aralıklarla sorgulandığı bir profil oluşturma yöntemidir. Elde edilen veriler, işlem örneklendiği zaman, söz konusu işlevin çağrı yığınının en üstünde ne sıklıkta olduğunu gösteren bir sayı sağlar.  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak bir uygulama profili oluşturma  
  
1. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]Yönetici ayrıcalıklarıyla açın. Profil oluşturma için yönetici olarak çalışma gerekir.  
  
2. PeopleTrax çözümünü açın.  
  
     PeopleTrax çözümü artık Çözüm Gezgini doldurur.  
  
3. Proje yapılandırma ayarını **serbest bırakma**olarak ayarlayın.  
  
     Uygulamanızdaki performans sorunlarını algılamak için bir yayın derlemesi kullanmanız gerekir. Bir hata ayıklama derlemesi, performansı olumsuz etkileyebilecek ve performans sorunlarını doğru bir şekilde göstermediği için derlenmiş ek bilgiler içerdiğinden, profil oluşturma için bir yayın derlemesi önerilir.  
  
4. **Çözümle** menüsünde, **Performans Sihirbazını Başlat**' ı tıklatın.  
  
     Performans Sihirbazı görüntülenir.  
  
5. **CPU örnekleme (önerilen)** seçeneğinin belirlendiğinden emin olun ve ardından **İleri**' ye tıklayın.  
  
6. **Profil oluşturmak Için hangi uygulamayı hedeflemek**Istiyorsunuz, PeopleTrax ' i seçin ve ardından **İleri**' ye tıklayın.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] projeyi oluşturur ve uygulamayı profil olarak başlatır. **PeopleTrax** uygulama penceresi görüntülenir.  
  
7. **Kişi al**seçeneğine tıklayın.  
  
8. **ExportData**öğesine tıklayın.  
  
     Not Defteri açılır ve **PeopleTrax**adresinden dışarıya aktarılmış verileri içeren yeni bir dosya görüntüler.  
  
9. Not defteri 'ni kapatın ve sonra **PeopleTrax** uygulamasını kapatın.  
  
     Profil Oluşturucu bir profil oluşturma verileri ( \* . vsp) dosyası oluşturur, dosya adını performans Gezgini penceresinin Raporlar bölümünde listeler ve veri dosyasının **Özet** görünümünü otomatik olarak ' ın ana penceresinde yükler [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .  
  
#### <a name="to-analyze-sampled-profiling-results"></a>Örneklenmiş profil oluşturma sonuçlarını çözümlemek için  
  
1. Özet görünümü, profil oluşturma çalışma sırasında CPU kullanımının bir zaman çizelgesini, en çok etkin olan uygulamanın çağrı ağacının dalını temsil eden **sık kullanılan yol** listesini ve kodu kendi işlev gövdesinde yürütürken en yoğun şekilde örnekleyen Işlevleri gösteren **işlevlerin** bir listesini görüntüler.  
  
     **Etkin yol** listesini Inceleyin ve PeopleNS. kişiler. GetNames yönteminin listenin sonuna en yakın PeopleTrax işlevi olduğuna dikkat edin. Konumu analiz için iyi bir aday yapar. **Işlev ayrıntıları** görünümündeki GetNames ayrıntılarını görüntülemek için işlev adına tıklayın.  
  
2. **Işlev ayrıntıları** görünümü iki pencere içerir. Maliyet dağılımı penceresi, işlevi tarafından gerçekleştirilen çalışmanın grafik görünümünü, çağırdığı işlevlerin yaptığı çalışmayı ve işlev çağıran işlevlerin örneklendiği örnek sayısına katkısı sağlar. Bir işlev adına tıklayarak, görünümün odağı olan işlevini değiştirebilirsiniz. Örneğin, PeopleNS. kişiler. Getkişileri ' ne tıklayarak Getinsanları seçili işlevi yapabilirsiniz.  
  
     **Işlev kod görünümü** penceresi, varsa işlevin kaynak kodunu gösterir ve seçili işlevdeki en pahalı satırları vurgular. {1 & gt; GetNames & lt; 1} seçildiğinde, bu işlevin uygulama kaynaklarından bir dize okuyabileceğini ve sonra <xref:System.IO.StringReader> dizedeki her satırı bir satıra eklemek için kullandığını görebilirsiniz <xref:System.Collections.ArrayList> . Bu işlevi iyileştirmek için belirgin bir yol yoktur.  
  
3. PeopleNS. kişiler. Getkişiler tek GetNames çağıranıdır, kodunu incelemek için maliyet dağılımı penceresinde Getkişiler ' e tıklayın. Bu yöntem <xref:System.Collections.ArrayList> , GetNames tarafından üretilen kişilerin ve şirketlerin adlarından PersonInformationNS. PersonInformation nesnelerinden birini döndürür. Ancak, bir PersonInformation nesnesi oluşturulduğu her seferinde GetNames iki kez çağrılır. Yöntemin başlangıcında yalnızca bir kez ve PersonInformation oluşturma döngüsü sırasında bu listelerde dizin oluşturarak, metodun kolayca iyileştirebilmesini sağlayabilirsiniz.  
  
4. Örnek uygulama kodu ile birlikte Getkişiler 'in alternatif bir sürümü sağlanır ve derleme özelliklerine koşullu bir derleme sembolü ekleyerek iyileştirilmiş işlevi çağırabilirsiniz. Çözüm Gezgini penceresinde, kişiler projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın. Özellik sayfası menüsünde **Oluştur** ' a tıklayın ve sonra koşullu derleme sembolü metin kutusuna **OPTIMIZED_GETPEOPLE** yazın. En iyileştirilmiş Getkişiler sürümü, sonraki derlemede orijinal yöntemin yerini alır.  
  
5. Performans oturumunu yeniden çalıştırın. Performans Gezgini araç çubuğunda, **profil oluşturma Ile Başlat**' a tıklayın. **Kişi al** ' a ve ardından **verileri dışarı aktar**' a tıklayın. Görüntülenen Not Defteri penceresini kapatın ve ardından Insanlar Trax uygulamasını kapatın.  
  
     Yeni bir profil oluşturma veri dosyası oluşturulur ve ana pencerede yeni veriler için bir **Özet** görünümü görüntülenir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .  
  
6. İki profil oluşturma çalıştırmasını karşılaştırmak için, Performans Gezgini iki veri dosyasını seçin, dosyalara sağ tıklayın ve ardından **performans raporlarını karşılaştır**' a tıklayın. Ana pencerede bir karşılaştırma raporu penceresi görüntülenir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . **Delta** sütunu, önceki **taban çizgisi** değerindeki işlevlerin performans değerindeki değişikliği sonraki **karşılaştırma** değerine gösterir. **Sütun** açılan listesinden Karşılaştırılacak değerleri seçebilirsiniz. **Kapsanan örnekleri seçin%**.  
  
     Getkişiler ve GetNames yöntemlerinin önemli performans kazançlarını gösterdiğine dikkat edin.  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>Izleme yöntemini kullanarak profil oluşturma  
 İzleme, profil oluşturucunun, profili oluşturulmuş ikililerin özel olarak oluşturulmuş sürümlerine araştırma işlevleri eklediği bir profil oluşturma yöntemidir. Araştırmalar, planlama bilgilerini girişte ve bu işlevlerdeki tüm çağrı sitesinde bulunan işlevlerin giriş ve çıkış bilgileri toplar. İzleme işlemi, diske yazma ve ağ üzerinden iletişim kurma gibi giriş/çıkış işlemleriyle ilgili sorunları araştırmak için yararlıdır. İzleme, örneklemeye göre daha ayrıntılı bilgiler sağlar, ancak işlem yürütmesinde daha fazla zorlayıcıdır ve daha fazla ek yük tutar. Belgelenmiş ikili dosyalar aynı zamanda hata ayıklama veya sürüm ikilileriyle daha büyüktür ve dağıtıma yönelik değildir.  
  
 Bu kılavuzda, daha önce profili oluşturulan PeopleTrax uygulamasında iyileştirebildiğimiz daha fazla kodu saptamak için izleme yöntemini kullanacağız. Özet görünüm zaman çizelgesinin filtresini kullanarak analizine, kişi listesinin bir not defteri dosyasına yazıldığı, profili oluşturulmuş uygulamamızda verileri dışarı aktarma senaryosuna odaklanacağız.  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>İzleme yöntemini kullanarak var olan bir uygulamayı profil haline getirme  
  
1. Gerekirse, Visual Studio 'da PeopleTrax uygulamasını açın.  
  
     Yönetici olarak çalıştırdığınızdan ve çözüme yönelik derleme yapılandırmasının **serbest**olarak ayarlandığından emin olun.  
  
2. Performans Gezgini, **Araçlar**' a tıklayın.  
  
3. Performans Gezgini araç çubuğunda, **profil oluşturma Ile Başlat**' a tıklayın.  
  
     Profil Oluşturucu projeyi oluşturur ve uygulamayı profil olarak başlatır. PeopleTrax uygulama penceresi görüntülenir.  
  
4. **Kişi al**seçeneğine tıklayın.  
  
     PeopleTrax veri kılavuzu, verilerle doldurulur.  
  
5. Yaklaşık 10 saniye bekleyip **verileri dışarı aktar**' a tıklayın.  
  
     **Not defteri** başlar ve PeopleTrax 'deki kişilerin listesini içeren yeni bir dosya görüntüler. Bekliyor, filtreleme için veri dışarı aktarma yordamını daha kolay bir şekilde tanımlamanızı sağlar.  
  
6. **Not defteri**'ni kapatın ve sonra **PeopleTrax** uygulamasını kapatın.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] bir performans oturumu raporu üretir (*. vsp).  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>Belgelenmiş profil oluşturma sonuçlarını çözümlemek için  
  
1. Raporun **Özet** görünümünün zaman çizelgesi grafiği, profil oluşturma çalışmasının süresi boyunca programın CPU kullanımını gösterir. Verileri dışarı aktar işlemi, grafiğin sağ tarafındaki büyük tepe veya plasyon u olmalıdır. Yalnızca dışa aktarma işleminde toplanan verileri göstermek ve analiz etmek için performans oturumunu filtreleyebiliriz. Verileri dışarı aktarma işleminin başladığı grafikte noktanın soluna tıklayın. İşlemin sağ tarafına tekrar tıklayın. Sonra, zaman çizelgesinin sağındaki bağlantı listesinden **seçime göre filtrele** ' ye tıklayın.  
  
    **Etkin yol** ağacı, <xref:System.String.Concat%2A> PeopleTrax. Form1. ExportData yöntemi tarafından çağrılan yöntemin zamanın büyük bir yüzdesini tükettiğini gösterir. **System. String. Concat** , **en çok bireysel çalışma listesi olan işlevlerin** en üstünde da olduğundan, işlevde harcanan süreyi azaltmak olası bir iyileştirme noktasıdır.  
  
2. Işlev Ayrıntıları görünümünde daha fazla bilgi görmek için Özet tablolarından birinde **System. String. Concat** öğesine çift tıklayın.  
  
3. PeopleTrax. Form1. ExportData 'ın Concat öğesini çağıran tek yöntem olduğunu görebilirsiniz. Yöntemi, Işlev ayrıntıları görünümünün hedefi olarak belirlemek için **çağırma işlevleri** listesindeki **PeopleTrax. Form1. ExportData** öğesine tıklayın.  
  
4. Işlev kod görünümü penceresinde yöntemini inceleyin. **System. String. Concat**için değişmez değer çağrısı olmadığına dikkat edin. Bunun yerine, + = işleneninin bazı kullanımları vardır. Bu, derleyicinin **System. String. Concat**çağrıları ile yerini almıştır. .NET Framework bir dizedeki herhangi bir değişiklik, yeni bir dizenin ayrılmasına neden olur. .NET Framework <xref:System.Text.StringBuilder> dize birleştirme için iyileştirilmiş bir sınıf içerir  
  
5. Bu sorun alanını iyileştirilmiş kodla değiştirmek için, PeopleTrax projesine koşullu derleme simgesi olarak OPTIMIZED_EXPORTDATA ekleyin.  
  
6. Çözüm Gezgini, PeopleTrax projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
    PeopleTrax proje özellikleri formu görüntülenir.  
  
7. **Derleme** sekmesine tıklayın.  
  
8. **Koşullu derleme sembolleri** metin kutusuna **OPTIMIZED_EXPORTDATA**yazın.  
  
9. Proje özellik formunu kapatın ve istendiğinde **Tümünü Kaydet** ' i seçin.  
  
   Uygulamayı yeniden çalıştırdığınızda, performans ile işaretlenmiş iyileştirmeler görürsünüz. Performansla ilgili Kullanıcı görünür iyileştirmeleri olsa bile profil oluşturma oturumunu yeniden çalıştırmanız önerilir. Sorunu düzelttikten sonra verileri gözden geçirmek, ilk sorun başka bir sorunu gizlebileceğinden önemlidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tahmin](../profiling/overviews-performance-tools.md)   
 [Başlarken](../profiling/getting-started-with-performance-tools.md)   
 [/Z7,/Zi,/ZI (hata ayıklama bilgileri biçimi)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)
