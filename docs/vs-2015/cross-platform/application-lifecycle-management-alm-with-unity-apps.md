---
title: Unity Apps ile Uygulama Yaşam Döngüsü Yönetimi (ALM) | Microsoft Dokümanlar
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
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233286"
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Unity Uygulamaları ile Uygulama Yaşam Döngüsü Yönetimi (ALM)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modern platformlar için uygulama geliştirmek, kod yazmaktan çok daha fazla etkinlik içerir. DevOps (geliştirme + operasyonlar) olarak adlandırılan bu faaliyetler, uygulamanın tam yaşam döngüsünü kapsar ve çalışma planlama ve izleme, kod tasarlama ve uygulama, kaynak kodu deposunu yönetme, yapı çalıştırma, sürekli tümleştirmeleri yönetme yi içerir ve dağıtımlar, testler (birim testleri ve Kullanıcı Arabirimi testleri dahil), hem geliştirme hem de üretim ortamlarında çeşitli tanılama biçimleri nin çalıştırılması ve uygulama performansının ve kullanıcı davranışlarının telemetri ve analitik yoluyla gerçek zamanlı olarak izlenmesi.  
  
 Visual Studio Team Services ve Team Foundation Server ile birlikte, Uygulama Yaşam Döngüsü Yönetimi veya ALM olarak da adlandırılan çeşitli DevOps yetenekleri sağlar. Bunların çoğu, özellikle C# komut dosyası dili olarak C# kullanırken, Unity ile oluşturulan oyunlar ve sürükleyici grafik uygulamaları da dahil olmak üzere platformlar arası projeler için geçerlidir. Ancak, Unity'nin kendi geliştirme ortamı ve çalışma zamanı motoru olduğundan, bir dizi ALM özelliği Visual Studio'da inşa edilen diğer türde projelerde olduğu gibi geçerli değildir.  
  
 Aşağıdaki tablolar Visual Studio ALM özelliklerinin Unity ile çalışırken nasıl uygulandığını veya uygulanmadığını tanımlar. Özelliklerin kendisi yle ilgili ayrıntılar için bağlantılı belgelere bakın.  
  
## <a name="agile-tools"></a>Çevik araçlar  
 Referans linki: **[Çalışma](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (Her Yerde Team Explorer dahil Görsel Stüdyo Ekip Hizmetleri veya TFS kullanarak)  
  
 Genel Yorum: tüm planlama ve izleme özellikleri proje türü nden ve kodlama dillerinden bağımsızdır.  
  
|Özellik|Birlik ile desteklenen|Ek Yorumlar|  
|-------------|--------------------------|-------------------------|  
|Biriktirme listelerini ve sprintleri yönetme|Evet||  
|İş takibi|Evet||  
|Takım odası işbirliği|Evet||  
|Kanban panoları|Evet||  
|İlerlemeyi bildirme ve görselleştirme|Evet||  
  
## <a name="modeling"></a>Modelleme  
 Referans linki: ** [Analiz ve Modelleme Mimarisi](../modeling/analyze-and-model-your-architecture.md)**  
  
 Genel Yorum: Bu tasarım özellikleri kodlama dilinden bağımsız olsa da veya C# gibi .NET dilleriyle çalışsa lar da, nesne hiyerarşileri ve sınıf ilişkileri yle geleneksel bir uygulama paradigması üzerinde çalışırlar. Unity içinde bir oyun tasarlamak tamamen farklı bir paradigma içerir, yani grafik nesneleri, sesler, gölgeli, komut dosyası ve benzeri ilişkileri. Bu nedenle, Visual Studio modelleme diyagramı araçları özellikle bir Birlik projesinin tamamı ile ilgili değildir. C# komut dosyaları içindeki ilişkileri yönetmek için kullanılabilirler, ancak bu bütünün yalnızca bir parçasıdır.  
  
|Özellik|Birlik ile desteklenen|Ek Yorumlar|  
|-------------|--------------------------|-------------------------|  
|Sıralı diyagramlar|Hayır||  
|Bağımlılık grafikleri|Hayır||  
|Çağrı hiyerarşisi|Hayır||  
|Sınıf tasarımcısı|Hayır||  
|Mimari kaşif|Hayır||  
|UML diyagramları (kullanım örneği, etkinlik, sınıf, bileşen, dizi ve DSL)|Hayır||  
|Katman diyagramları|Hayır||  
|Katman doğrulama|Hayır||  
  
## <a name="code"></a>Kod  
  
|Özellik|Birlik ile desteklenen|Ek Yorumlar|  
|-------------|--------------------------|-------------------------|  
|[Team Foundation Sürüm Kontrolü](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) veya Visual Studio Takım Hizmetlerini Kullanma|Evet|Birlik projeleri, diğer projeler gibi sürüm denetim sistemlerine yerleştirilebilen dosyaların bir koleksiyonudur, ancak bu tablodan sonra açıklanan birkaç özel husus vardır.|  
|[Ekip Hizmetlerinde Git ile başlarken](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Evet|Tablodan sonraki notlara bakın.|  
|[Kod analizi/Kod kalitesini iyileştirme (başvurular, önerilen değişiklikler, vb.)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Evet||  
|[Kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)|Evet||  
|[Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)|Evet||  
  
 Unity ile sürüm kontrolü için özel hususlar:  
  
1. Unity, varsayılan olarak gizli olan tek ve opak bir kitaplıkta oyun varlıklarıyla ilgili meta verileri izler. Dosyaları ve meta verileri eşit tutmak için meta verileri görünür hale getirmek ve daha yönetilebilir parçalar halinde depolamak gerekir. Ayrıntılar için, [Unity (Unity](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) belgeleri) ile Dış Sürüm Kontrol Sistemleri Kullanma'ya bakın.  
  
2. Yukarıdaki bağlantıda açıklandığı gibi, Birle'nin tüm dosyaları ve klasörleri kaynak denetimi için uygun değildir. Varlıklar ve ProjectSettings klasörleri eklenmelidir, ancak Kitaplık ve Geçici klasörler eklenmemelidir. Kaynak denetimine girmeyen oluşturulan dosyaların ek bir listesi için StackOverflow'da [Unity3D kaynak denetimi için Git nasıl kullanılır?](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) Birçok geliştirici de bağımsız olarak bu konuda blogged var.  
  
3. Dokular veya ses dosyaları gibi bir Unity projesindeki ikili varlıklar büyük miktarda depolama alanı kaplayabilir. Git gibi çeşitli kaynak denetim sistemleri, değişiklik dosyanın yalnızca küçük bir bölümünü etkilese bile, yapılan her değişiklik için bir dosyanın benzersiz bir kopyasını saklar. Bu git deposu şişirilmiş olmasına neden olabilir. Bu sorunu gidermek için, Unity geliştiricileri genellikle depolarına yalnızca son varlıkları eklemeyi ve OneDrive, DropBox veya git-annex gibi varlıklarının çalışma geçmişini tutmanın farklı bir araçlarını kullanmayı seçerler. Bu tür varlıkların genellikle kaynak kodu değişiklikleriyle birlikte sürülmesi gerekmediği için bu yaklaşım çalışır. Geliştiriciler ayrıca genellikle proje düzenleyicisinin Varlık Serileştirme Modunu, kaynak denetiminde birleştirmelere izin veren ikili biçim yerine sahne dosyalarını metinde depolamak için Metni Zorlamaya ayarlar. Ayrıntılar için [Editör Ayarları](https://docs.unity3d.com/Manual/class-EditorManager.html) (Unity belgeleri) bakın.  
  
## <a name="build"></a>Oluşturma  
 Referans linki: ** [Yapı](/azure/devops/pipelines/index)**  
  
|Özellik|Birlik ile desteklenen|Ek Yorumlar|  
|-------------|--------------------------|-------------------------|  
|Şirket içi TFS sunucusu|Mümkün|Birlik projeleri Visual Studio yapı sistemi üzerinden değil, Unity ortamı üzerinden inşa edilir (Visual Studio Tools for Unity içinde bina komut dosyaları derleyecek ama yürütülebilir üretmek değil). [Komut satırından (Unity](https://docs.unity3d.com/Manual/CommandLineArguments.html) documentation) Unity projeleri oluşturmak mümkündür, böylece bir TFS sunucusunda bir MSBuild işlemini uygun Unity komutlarını yürütmek için yapılandırmak mümkündür, çünkü Unity kendisi bu bilgisayara yüklü olması koşuluyla.<br /><br /> Unity ayrıca, git veya SVN deposunu izleyen ve periyodik yapılar çalıştıran [Unity Cloud Build'i](https://build.cloud.unity3d.com/landing/)de sunar. Şu anda Team Foundation Sürüm Kontrolü veya Visual Studio Takım Hizmetleri ile çalışmıyor.|  
|Visual Studio Takım Hizmetleri ile bağlantılı şirket içi yapı sunucusu|Mümkün|Yukarıdaki koşullar göz önüne alındığında, visual studio takım hizmetleri aracılığıyla tetiklenen yapıları şirket içi Bir TFS bilgisayarı kullanmak için yönlendirmek daha da mümkündür.  Talimatlar için [Yapı sunucusuna](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) bakın.|  
|Visual Studio Takım Hizmetleri'nin barındırılan kontrolör hizmeti|Hayır|Birlik yapılaşmaları şu anda desteklenmez.|  
|Ön ve post-scriptler ile tanımoluşturma|Evet|Bir yapıyı çalıştırmak için Birlik komut satırını kullanan özel bir yapı tanımı, yapı öncesi ve sonrası komut dosyaları için de yapılandırılabilir.|  
|Kapılı check-in'ler de dahil olmak üzere sürekli entegrasyon|Evet|TFVC için kapılı check-in'ler yalnızca Git iadeyerine çekme isteği modelinde çalıştığı için.|  
  
## <a name="testing"></a>Sınama  
 Referans linki: ** [Uygulamayı test etme](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Özellik|Birlik ile desteklenen|Ek Yorumlar|  
|-------------|--------------------------|-------------------------|  
|Testleri planlama, test örnekleri oluşturma ve test paketlerini düzenleme|Evet||  
|Manuel test|Evet||  
|Test Yöneticisi (kayıt ve oynatma testleri)|Yalnızca Windows aygıtları ve Android emülatörleri||  
|Kod kapsamı|yok|Birim testi Visual Studio içinde değil, Unity içinde gerçekleştiği için geçerli değildir, aşağıya bakın.|  
|[Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)|Birlik içinde, ama Visual Studio değil|Unity, [Unity Test Tools](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802) (Unity Asset Store) kapsamında kendi birim test çerçevesini sağlar. Ünite test sonuçları Birlik içinde raporlanır ve Visual Studio içinde su yüzüne çıkmayacaktır.|  
|[Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)|Hayır|Kodlanmış UI testleri, uygulamanın UI'sindeki okunabilir denetimlere dayanır; Birlik uygulamaları grafiksel dir ve bu nedenle içerik Kodlu Kullanıcı Aracı test araçları tarafından okunamaz.|  
  
## <a name="improve-code-quality"></a>Kod kalitesini artırma  
 Referans linki: ** [Kod Kalitesini Artırın](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Özellik|Birlik ile desteklenen|Ek Yorumlar|  
|-------------|--------------------------|-------------------------|  
|[Yönetilen Kod Kalitesini Analiz Etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Evet|Visual Studio içindeki C# komut dosyası kodunu analiz edebilir.|  
|[Kod Klon Algılama kullanarak Yinelenen Kodu Bulma](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Evet|Visual Studio içindeki C# komut dosyası kodunu analiz edebilir.|  
|[Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Evet|Visual Studio içindeki C# komut dosyası kodunu analiz edebilir.|  
|[Performans Gezgini](../profiling/performance-explorer.md)|Hayır|Unity [Profiler](https://docs.unity3d.com/Manual/Profiler.html) 'ı (Unity web sitesini) kullanın.|  
|[.NET Framework bellek sorunlarını çözümleme](../misc/analyze-dotnet-framework-memory-issues.md)|Hayır|Visual Studio araçlarının profil oluşturma için Mono çerçevesine (Unity tarafından kullanıldığı gibi) kancaları yoktur. Unity [Profiler](https://docs.unity3d.com/Manual/Profiler.html) (Birlik belgeleri) kullanın.|  
  
## <a name="release-management"></a>Yayın yönetimi  
 Referans bağlantısı: ** [Yayın Yönetimi ile dağıtımları otomatikleştirin](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Özellik|Birlik ile desteklenen|Ek Yorumlar|  
|-------------|--------------------------|-------------------------|  
|Sürüm süreçlerini yönetme|Evet||  
|Komut dosyaları aracılığıyla yan yükleme için sunuculara dağıtım|Evet||  
|Uygulama mağazasına yükleyin|Kısmi|Bazı uygulama mağazaları için bu işlemi otomatikleştirebilecek uzantılar mevcuttur.  [Visual Studio Takım Hizmetleri Uzantılarına](https://marketplace.visualstudio.com/VSTS)Bakın; örneğin, [Google Play için uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>HockeyApp ile Monitör  
 Referans linki: ** [HockeyApp ile monitör](https://www.hockeyapp.net/features/)**  
  
|Özellik|Birlik ile desteklenen|Ek Yorumlar|  
|-------------|--------------------------|-------------------------|  
|Çarpışma analitiği, telemetri ve beta dağılımı|Evet|HockeyApp öncelikle beta dağıtım işleme ve çökme raporları elde etmek için yararlıdır.<br /><br /> C# komut dosyasından telemetri için, Unity tarafından kullanılan .NET sürümünde çalışması koşuluyla herhangi bir analiz çerçevesi kullanmak mümkündür. Ancak bu, Unity motorunun içinde değil, yalnızca oyun komut dosyaları içinde analiz yapılmasına olanak tanır. Şu anda Application Insights için eklenti yoktur, ancak eklentiler [Unity Analytics](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) ve [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity)gibi diğer analiz çözümleri için kullanılabilir. Birlik projesinin doğasını anlayan Unity Analytics gibi hizmetler elbette genel çerçevelerden çok daha anlamlı analizler sağlayacaktır.|
