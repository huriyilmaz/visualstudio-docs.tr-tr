---
title: Unity uygulamalarıyla uygulama yaşam döngüsü yönetimi (ALM) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 90efd4e72ea172822e0bcc424bdbbc4bc7589098
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80233286"
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Unity Uygulamaları ile Uygulama Yaşam Döngüsü Yönetimi (ALM)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modern platformlar için uygulama geliştirme, yalnızca koddan çok daha fazla etkinlik içerir. DevOps (geliştirme + işlemler) olarak adlandırılan bu etkinlikler, uygulamanın tamamlanma yaşam döngüsünü kapsar ve planlama ve izleme işini içerir. kod tasarlama ve uygulama, bir kaynak kodu deposunu yönetme, derleme çalıştırma, sürekli tümleştirmeler ve dağıtımları yönetme, test (birim testleri ve UI testleri dahil), hem geliştirme hem de üretim ortamlarında çeşitli tanılama biçimlerini çalıştırma ve uygulama performansını ve kullanıcı davranışlarını telemetri ve analiz aracılığıyla gerçek zamanlı olarak izleme.  
  
 Visual Studio Team Services ve Team Foundation Server ile birlikte Visual Studio, uygulama yaşam döngüsü yönetimi veya ALM olarak da adlandırılan çeşitli DevOps özellikleri sağlar. Bunların birçoğu, özellikle C# ' ın bir komut dosyası dili olarak kullanılması halinde Unity ile oluşturulan Oyunlar ve modern grafik uygulamalar dahil olmak üzere platformlar arası projeler için geçerlidir. Ancak, Unity 'nin kendi geliştirme ortamı ve çalışma zamanı altyapısı bulunduğundan, Visual Studio 'da oluşturulan diğer proje türlerine yaptıkları için bir dizi ALM özelliği uygulanmaz.  
  
 Aşağıdaki tablolar, Unity ile çalışırken Visual Studio ALM özelliklerinin nasıl uygulanacağını veya uygulanacağını tanımlar. Özelliklerin kendileri hakkındaki ayrıntılar için bağlantılı belgelere başvurun.  
  
## <a name="agile-tools"></a>Çevik Araçlar  
 Başvuru bağlantısı: **[iş](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (Team Explorer Everywhere dahil VISUAL STUDIO Team SERVICES veya TFS kullanarak)  
  
 Genel Açıklama: tüm planlama ve izleme özellikleri proje türü ve kodlama dillerinden bağımsızdır.  
  
|Öne çıkan özelliği|Unity ile desteklenir|Ek açıklamalar|  
|-------------|--------------------------|-------------------------|  
|Biriktirme listeleri ve Sprint 'leri yönetme|Yes||  
|Çalışma izleme|Yes||  
|Takım odası işbirliği|Yes||  
|Kanban panoları|Yes||  
|İlerlemeyi raporla ve görselleştirin|Yes||  
  
## <a name="modeling"></a>Modelleme  
 Başvuru bağlantısı: ** [mimari çözümleme ve modelleme](../modeling/analyze-and-model-your-architecture.md)**  
  
 Genel Açıklama: Bu tasarım özellikleri kodlama dilinden bağımsız olsa da C# gibi .NET dilleri ile birlikte çalışarak, nesne hiyerarşileri ve sınıf ilişkileri ile geleneksel bir uygulama paradigması üzerinde çalışır. Unity içinde bir oyun tasarlamak, grafik nesnelerin, seslerin, gölgelendiricilerin, betiklerin vb. ilişkilerini tamamen farklı bir paradigma içerir. Bu nedenle, Visual Studio modelleme diyagramı araçları özellikle bir Unity projesinin tamamına uygun değildir. Bunlar, C# betikleri içindeki ilişkileri yönetmek için kullanılabilirler, ancak bu yalnızca bir kısmının bir parçasıdır.  
  
|Öne çıkan özelliği|Unity ile desteklenir|Ek açıklamalar|  
|-------------|--------------------------|-------------------------|  
|Sıralı diyagramlar|No||  
|Bağımlılık grafikleri|No||  
|Çağrı hiyerarşisi|No||  
|Sınıf Tasarımcısı|No||  
|Mimari Gezgini|No||  
|UML diyagramları (kullanım örneği, etkinlik, sınıf, bileşen, dizi ve DSL)|No||  
|Katman diyagramları|No||  
|Katman doğrulama|No||  
  
## <a name="code"></a>Kod  
  
|Öne çıkan özelliği|Unity ile desteklenir|Ek açıklamalar|  
|-------------|--------------------------|-------------------------|  
|[Team Foundation sürüm denetimi](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) veya Visual Studio Team Services kullanın|Yes|Unity projeleri yalnızca diğer projeler gibi sürüm denetim sistemlerine yerleştirilebilecek bir dosya koleksiyonudur, ancak bu tablodan sonra açıklanan bazı özel noktalar vardır.|  
|[Team Services 'da git 'i kullanmaya başlama](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Yes|Tablodan sonraki notlara bakın.|  
|[Kod Analizi/kod kalitesini geliştirme (başvurular, önerilen değişiklikler vb.)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Yes||  
|[Kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)|Yes||  
|[Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)|Yes||  
  
 Unity ile sürüm denetimi için özel hususlar:  
  
1. Unity, oyun varlıkları hakkındaki meta verileri, varsayılan olarak gizlenen tek ve donuk bir kitaplıkta izler. Dosyaları ve meta verileri eşitlenmiş halde tutmak için meta verilerin görünür olması ve daha yönetilebilir parçalara depolanması gerekir. Ayrıntılar için [Unity Ile dış sürüm denetim sistemleri](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Unity belgeleri) kullanma konusuna bakın.  
  
2. Bir Unity projesindeki tüm dosyalar ve klasörler, yukarıdaki bağlantıda da açıklandığı gibi, kaynak denetimi için uygun değildir. Varlıklar ve ProjectSettings klasörleri eklenmelidir, ancak kitaplık ve geçici klasörlerin olmaması gerekir. Kaynak denetimine gitmeyecek oluşturulan dosyaların ek bir listesi için, StackOverflow 'de [unity3d kaynak denetimi Için git kullanma](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) konusuna bakın. Birçok geliştirici bu konuya bağımsız olarak da BDE oturum açtı.  
  
3. Unity projesindeki (dokular veya ses dosyaları gibi) ikili varlıklar, büyük miktarda depolama alanı alabilir. Git deposu gibi çeşitli kaynak denetim sistemleri, değişiklik yalnızca dosyanın küçük bir kısmını etkilese bile, yapılan her değişiklik için dosyanın benzersiz bir kopyasını saklar. Bu, git deposunun blok haline gelmesine neden olabilir. Unity geliştiricileri bu şekilde ele almak için genellikle depolarına yalnızca son varlıkları eklemeyi ve OneDrive, DropBox veya git-ek gibi varlıklarının çalışma geçmişini tutmanın farklı bir araçlarını kullanır. Bu yaklaşım, bu tür varlıkların genellikle kaynak kodu değişiklikleriyle birlikte sürüm oluşturulması gerekmediği için geçerlidir. Geliştiriciler ayrıca, genellikle proje düzenleyicisinin varlık serileştirme modunu, metni, sahne dosyalarını, kaynak denetiminde birleştirme yapılmasına izin veren ikili biçim yerine metin halinde depolamaya zorlamak üzere ayarlar. Ayrıntılar için bkz. [Düzenleyici ayarları](https://docs.unity3d.com/Manual/class-EditorManager.html) (Unity belgeleri).  
  
## <a name="build"></a>Oluşturma  
 Başvuru bağlantısı: ** [derleme](/azure/devops/pipelines/index)**  
  
|Öne çıkan özelliği|Unity ile desteklenir|Ek açıklamalar|  
|-------------|--------------------------|-------------------------|  
|Şirket içi TFS sunucusu|Üç|Unity projeleri, Visual Studio derleme sistemi aracılığıyla değil Unity ortamı aracılığıyla oluşturulur (Unity için Visual Studio Araçları içinde derleme betikleri derler ancak yürütülebilir bir işlem oluşturmaz). Unity [projelerini komut satırından](https://docs.unity3d.com/Manual/CommandLineArguments.html) (Unity belgeleri) derlemek mümkündür. bu nedenle, Unity 'nin kendisi bu bilgisayarda yüklü olması şartıyla uygun Unity komutlarını yürütmek IÇIN bir TFS sunucusunda MSBuild işlemini yapılandırmak mümkündür.<br /><br /> Unity Ayrıca, bir git veya SVN deposunu izleyen ve düzenli derlemeler çalıştıran [Unity bulut derlemesini](https://build.cloud.unity3d.com/landing/)de sunmaktadır. Mevcut olduğunda, Team Foundation Sürüm Denetimi veya Visual Studio Team Services birlikte çalışmaz.|  
|Visual Studio Team Services bağlı şirket içi derleme sunucusu|Üç|Yukarıdaki koşulların aynısını göz önüne alarak, Visual Studio Team Services aracılığıyla tetiklenen derlemelerin şirket içi TFS bilgisayarı kullanması daha da olasıdır.  Yönergeler için bkz. [yapı sunucusu](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) .|  
|Visual Studio Team Services barındırılan denetleyici hizmeti|No|Unity derlemeleri Şu anda desteklenmiyor.|  
|Ön ve son betiklerle derleme tanımları|Yes|Bir derlemeyi çalıştırmak için Unity komut satırını kullanan özel bir derleme tanımı, ön ve derleme sonrası betikler için de yapılandırılabilir.|  
|Geçitli iadeler dahil sürekli tümleştirme|Yes|TFVC için geçitli iadeler, yalnızca git, iadeler yerine bir çekme isteği modelinde çalışmaktadır.|  
  
## <a name="testing"></a>Test Etme  
 Başvuru bağlantısı: ** [uygulamayı test etme](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Öne çıkan özelliği|Unity ile desteklenir|Ek açıklamalar|  
|-------------|--------------------------|-------------------------|  
|Testleri planlama, test çalışmaları oluşturma ve test paketlerini düzenleme|Yes||  
|El ile test|Yes||  
|Test Yöneticisi (kaydı ve kayıttan yürütme testleri)|Yalnızca Windows cihazları ve Android öykünücüleri||  
|Kod kapsamı|yok|Birim testi, Unity içinde, Visual Studio değil, için geçerli değildir, aşağıya bakın.|  
|[Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)|Unity içinde, ancak Visual Studio 'Ya değil|Unity, [Unity test araçlarının](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802) (Unity varlık deposu) bir parçası olarak kendi birim test çerçevesini sağlar. Birim testi sonuçları Unity içinde raporlanır ve Visual Studio içinde kullanıma sunulacaktır.|  
|[Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)|No|Kodlanmış UI testleri, uygulamanın kullanıcı arabirimindeki okunabilir denetimlere dayanır; Unity uygulamaları doğası halinde grafik olduğundan, içerik kodlanmış UI test araçları tarafından okunamaz.|  
  
## <a name="improve-code-quality"></a>Kod kalitesini geliştirme  
 Başvuru bağlantısı: ** [kod kalitesini geliştirme](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Öne çıkan özelliği|Unity ile desteklenir|Ek açıklamalar|  
|-------------|--------------------------|-------------------------|  
|[Yönetilen Kod Kalitesini Analiz Etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Yes|, Visual Studio içinde C# komut dosyası kodunu analiz edebilir.|  
|[Kod kopyası algılamayı kullanarak yinelenen kodu bulma](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Yes|, Visual Studio içinde C# komut dosyası kodunu analiz edebilir.|  
|[Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Yes|, Visual Studio içinde C# komut dosyası kodunu analiz edebilir.|  
|[Performans Gezgini](../profiling/performance-explorer.md)|No|[Unity profil oluşturucuyu](https://docs.unity3d.com/Manual/Profiler.html) (Unity Web sitesi) kullanın.|  
|[.NET Framework bellek sorunlarını çözümleme](../misc/analyze-dotnet-framework-memory-issues.md)|No|Visual Studio Araçları, profil oluşturma için mono Framework 'te (Unity tarafından kullanılan) kancalar içermez. [Unity profil oluşturucuyu](https://docs.unity3d.com/Manual/Profiler.html) (Unity belgeleri) kullanın.|  
  
## <a name="release-management"></a>Yayın yönetimi  
 Başvuru bağlantısı: ** [Release Management Ile dağıtımları otomatikleştirin](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Öne çıkan özelliği|Unity ile desteklenir|Ek açıklamalar|  
|-------------|--------------------------|-------------------------|  
|Yayın süreçlerini yönetme|Yes||  
|Betikler aracılığıyla dışarıdan yükleme için sunuculara dağıtım|Yes||  
|App Store 'a yükle|Kısmi|Bazı uygulama mağazalarında bu işlemi otomatik hale getirebilen uzantılar vardır.  [Visual Studio Team Services Için uzantılara](https://marketplace.visualstudio.com/VSTS)bakın; Örneğin, [Google Play için uzantı](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>HockeyApp ile izleme  
 Başvuru bağlantısı: ** [HockeyApp ile izleme](https://www.hockeyapp.net/features/)**  
  
|Öne çıkan özelliği|Unity ile desteklenir|Ek açıklamalar|  
|-------------|--------------------------|-------------------------|  
|Kilitlenme Analizi, telemetri ve Beta dağıtımı|Yes|HockeyApp, Beta dağıtımını işlemek ve kilitlenme raporları almak için öncelikli olarak faydalıdır.<br /><br /> C# betiklerinden telemetri için, Unity tarafından kullanılan .NET sürümünde çalışan herhangi bir analiz çerçevesini kullanmak mümkündür. Ancak bu, yalnızca oyun betikleri içinde analizler ve Unity altyapısının içinde daha derin değildir. Mevcut olan Application Insights için eklenti yoktur, ancak [Unity Analytics](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) ve [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity)gibi diğer analiz çözümleri için eklentiler mevcuttur. Bir Unity projesinin doğasını anlayan, Unity Analytics gibi hizmetler, genel çerçevelerden çok daha anlamlı analizler sunacaktır.|
