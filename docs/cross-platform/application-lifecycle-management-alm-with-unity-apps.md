---
title: Unity Apps ile Uygulama Yaşam Döngüsü Yönetimi (ALM) | Microsoft Dokümanlar
ms.date: 08/21/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 17bdd86829da199e01a527aa382b8ed3bdfade17
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232942"
---
# <a name="devops-with-unity-apps"></a>Unity uygulamaları ile DevOps

Modern platformlar için uygulama geliştirmek, kod yazmaktan çok daha fazla etkinlik içerir. DevOps (geliştirme + operasyonlar) olarak adlandırılan bu etkinlikler, uygulamanın tüm yaşam döngüsünü kapsar ve çalışma planlama ve izleme, kod tasarlama ve uygulama, kaynak kodu deposunu yönetme, yapı çalıştırma, sürekli tümleştirmeleri yönetmeyi içerir ve dağıtımlar, testler (birim testleri ve Kullanıcı Arabirimi testleri dahil), hem geliştirme hem de üretim ortamlarında çeşitli tanılama biçimleri nin çalıştırılması ve uygulama performansının ve kullanıcı davranışlarının telemetri ve analitik yoluyla gerçek zamanlı olarak izlenmesi.

Visual Studio, Azure DevOps Hizmetleri ve Team Foundation Server ile birlikte çeşitli DevOps özellikleri sunar. Bunların çoğu, özellikle C# komut dosyası dili olarak C# kullanırken Unity&mdash;ile oluşturulan oyunlar ve sürükleyici grafik uygulamaları da dahil olmak üzere platformlar arası projeler için geçerlidir. Ancak, Birlik kendi geliştirme ortamı ve çalışma motoru olduğundan, DevOps özellikleri bir dizi Onlar Visual Studio inşa projelerin diğer tür için olduğu gibi geçerli değildir.

Aşağıdaki tablolar, Visual Studio'daki DevOps özelliklerinin Unity ile çalışırken nasıl uygulandığını veya uygulanmadığını tanımlar. Özelliklerin kendisi yle ilgili ayrıntılar için bağlantılı belgelere bakın.

## <a name="agile-tools"></a>Çevik araçlar

Referans bağlantısı: [Çevik araçlar ve Çevik proje yönetimi hakkında](/azure/devops/boards/backlogs/backlogs-overview?view=vsts) (Her Yerde Team Explorer dahil Olmak üzere Azure Panoları veya TFS kullanarak)

Genel Yorum: tüm planlama ve izleme özellikleri proje türü nden ve kodlama dillerinden bağımsızdır.

|Özellik|Birlik ile desteklenen|Ek Yorumlar|
|-------------|--------------------------|-------------------------|
|Biriktirme listelerini ve sprintleri yönetme|Evet||
|İş takibi|Evet||
|Takım odası işbirliği|Evet||
|Kanban panoları|Evet||
|İlerlemeyi bildirme ve görselleştirme|Evet||

## <a name="modeling"></a>Modelleme

Referans bağlantısı: ** [Çözümleme ve model mimarisi](../modeling/analyze-and-model-your-architecture.md)**

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
|[Team Foundation Sürüm Denetimini (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts) veya Azure Depolarını Kullanma|Evet|Birlik projeleri, diğer projeler gibi sürüm denetim sistemlerine yerleştirilebilen dosyaların bir koleksiyonudur, ancak bu tablodan sonra açıklanan birkaç özel husus vardır.|
|[Azure Repos'ta Git ile başlarken](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio)|Evet|Tablodan sonraki notlara bakın.|
|[Kod Kalitesini Geliştirme](../test/improve-code-quality.md)|Evet||
|[Kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)|Evet||
|[Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)|Evet||

Unity ile sürüm kontrolü için özel hususlar:

1. Unity, varsayılan olarak gizli olan tek ve opak bir kitaplıkta oyun varlıklarıyla ilgili meta verileri izler. Dosyaları ve meta verileri eşit tutmak için meta verileri görünür hale getirmek ve daha yönetilebilir parçalar halinde depolamak gerekir. Ayrıntılar için, [Unity (Unity](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) belgeleri) ile Dış Sürüm Kontrol Sistemleri Kullanma'ya bakın.

2. Yukarıdaki bağlantıda açıklandığı gibi, Birle'nin tüm dosyaları ve klasörleri kaynak denetimi için uygun değildir. Varlıklar ve ProjectSettings klasörleri eklenmelidir, ancak Kitaplık ve Geçici klasörler eklenmemelidir. Kaynak denetimine girmeyen oluşturulan dosyaların ek bir listesi için StackOverflow'da [Unity3D kaynak denetimi için Git nasıl kullanılır?](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) Birçok geliştirici de bağımsız olarak bu konuda blogged var.

3. Dokular veya ses dosyaları gibi bir Unity projesindeki ikili varlıklar büyük miktarda depolama alanı kaplayabilir. Git gibi çeşitli kaynak denetim sistemleri, değişiklik dosyanın yalnızca küçük bir bölümünü etkilese bile, yapılan her değişiklik için bir dosyanın benzersiz bir kopyasını saklar. Bu git deposu şişirilmiş olmasına neden olabilir. Bu sorunu gidermek için, Unity geliştiricileri genellikle depolarına yalnızca son varlıkları eklemeyi ve OneDrive, DropBox veya git-annex gibi varlıklarının çalışma geçmişini tutmanın farklı bir araçlarını kullanmayı seçerler. Bu tür varlıkların genellikle kaynak kodu değişiklikleriyle birlikte sürülmesi gerekmediği için bu yaklaşım çalışır. Geliştiriciler ayrıca genellikle proje düzenleyicisinin Varlık Serileştirme Modunu, kaynak denetiminde birleştirmelere izin veren ikili biçim yerine sahne dosyalarını metinde depolamak için Metni Zorlamaya ayarlar. Ayrıntılar için [Editör Ayarları](https://docs.unity3d.com/Manual/class-EditorManager.html) (Unity belgeleri) bakın.

## <a name="build"></a>Oluşturma

Referans bağlantısı: ** [Azure Ardışık Hatları](/azure/devops/pipelines/index?view=vsts)**

|Özellik|Birlik ile desteklenen|Ek Yorumlar|
|-------------|--------------------------|-------------------------|
|Şirket Içi Ekip Hazırlık Sunucusu (TFS)|Mümkün|Birlik projeleri Visual Studio yapı sistemi üzerinden değil, Unity ortamı üzerinden inşa edilir (Visual Studio Tools for Unity içinde bina komut dosyaları derleyecek ama yürütülebilir üretmek değil). [Komut satırından (Unity](https://docs.unity3d.com/Manual/CommandLineArguments.html) documentation) Unity projeleri oluşturmak mümkündür, böylece bir TFS sunucusunda bir MSBuild işlemini uygun Unity komutlarını yürütmek için yapılandırmak mümkündür, çünkü Unity kendisi bu bilgisayara yüklü olması koşuluyla.<br /><br /> Unity ayrıca, git veya SVN deposunu izleyen ve periyodik yapılar çalıştıran [Unity Cloud Build'i](https://build.cloud.unity3d.com/landing/)de sunar. Şu anda TFVC veya Azure DevOps Hizmetleri ile çalışmıyor.|
|Azure DevOps Hizmetleri'ne bağlı şirket içi yapı sunucusu|Mümkün|Yukarıdaki koşullar göz önüne alındığında, Azure DevOps Hizmetleri aracılığıyla tetiklenen yapıları şirket içi Bir TFS bilgisayarı kullanmak üzere yönlendirmek de mümkündür. Talimatlar için [Yapı ve sürüm temsilcilerine](/azure/devops/pipelines/agents/agents?view=vsts) bakın.|
|Azure DevOps Hizmetlerinin barındırılan denetleyici hizmeti|Hayır|Birlik yapılaşmaları şu anda desteklenmez.|
|Ön ve post-scriptler ile tanımoluşturma|Evet|Bir yapıyı çalıştırmak için Birlik komut satırını kullanan özel bir yapı tanımı, yapı öncesi ve sonrası komut dosyaları için de yapılandırılabilir.|
|Kapılı check-in'ler de dahil olmak üzere sürekli entegrasyon|Evet|TFVC için kapılı check-in'ler yalnızca Git iadeyerine çekme isteği modelinde çalıştığı için.|

## <a name="test"></a>Test

|Özellik|Birlik ile desteklenen|Ek Yorumlar|
|-------------|--------------------------|-------------------------|
|Testleri planlama, test örnekleri oluşturma ve test paketlerini düzenleme|Evet||
|Manuel test|Evet||
|Test Yöneticisi (kayıt ve oynatma testleri)|Yalnızca Windows aygıtları ve Android emülatörleri||
|Kod kapsamı|yok|Birim testi Visual Studio içinde değil, Unity içinde gerçekleştiği için geçerli değildir, aşağıya bakın.|
|[Birim kodunuzu test edin](../test/unit-test-your-code.md)|Birlik içinde, ama Visual Studio değil|Unity, [Unity test araçlarının](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802) (Unity Asset Store) bir parçası olarak kendi birim test çerçevesini sağlar. Ünite test sonuçları Birlik içinde raporlanır ve Visual Studio içinde su yüzüne çıkmayacaktır.|
|[Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)|Hayır|Kodlanmış UI testleri, uygulamanın UI'sindeki okunabilir denetimlere dayanır; Birlik uygulamaları grafiksel dir ve bu nedenle içerik Kodlu Kullanıcı Aracı test araçları tarafından okunamaz.|

## <a name="improve-code-quality"></a>Kod kalitesini artırma

Referans bağlantısı: ** [Kod kalitesini artırın](../test/improve-code-quality.md)**

|Özellik|Birlik ile desteklenen|Ek Yorumlar|
|-------------|--------------------------|-------------------------|
|[Yönetilen kod kalitesini analiz edin](../code-quality/code-analysis-for-managed-code-overview.md)|Evet|Visual Studio içindeki C# komut dosyası kodunu analiz edebilir.|
|[Kod klon algılamakullanarak yinelenen kodu bulma](https://msdn.microsoft.com/library/hh205279.aspx)|Evet|Visual Studio içindeki C# komut dosyası kodunu analiz edebilir.|
|[Yönetilen kodun karmaşıklığını ve korunabilirliğini ölçme](../code-quality/code-metrics-values.md)|Evet|Visual Studio içindeki C# komut dosyası kodunu analiz edebilir.|
|[Performans araçları](../profiling/performance-explorer.md)|Hayır|Unity [Profiler](https://docs.unity3d.com/Manual/Profiler.html) 'ı (Unity web sitesini) kullanın.|
|[.NET Framework bellek sorunlarını çözümleme](https://msdn.microsoft.com/library/dn342825.aspx)|Hayır|Visual Studio araçlarının profil oluşturma için Mono çerçevesine (Unity tarafından kullanıldığı gibi) kancaları yoktur. Unity [Profiler](http://docs.unity3d.com/Manual/Profiler.html) (Birlik belgeleri) kullanın.|

## <a name="release-management"></a>Yayın yönetimi

Referans bağlantısı: [Azure Ardışık Hatları ve TFS'de oluşturma ve yayımla](/azure/devops/pipelines/overview?view=vsts)

|Özellik|Birlik ile desteklenen|Ek Yorumlar|
|-------------|--------------------------|-------------------------|
|Sürüm süreçlerini yönetme|Evet||
|Komut dosyaları aracılığıyla yan yükleme için sunuculara dağıtım|Evet||
|Uygulama mağazasına yükleyin|Kısmi|Bazı uygulama mağazaları için bu işlemi otomatikleştirebilecek uzantılar mevcuttur. [Azure DevOps Hizmetleri Uzantılarına](https://marketplace.visualstudio.com/VSTS)bakın; örneğin, [Google Play için uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>HockeyApp ile Monitör

Referans linki: ** [HockeyApp ile monitör](https://www.hockeyapp.net/features/)**

|Özellik|Birlik ile desteklenen|Ek Yorumlar|
|-------------|--------------------------|-------------------------|
|Çarpışma analitiği, telemetri ve beta dağılımı|Evet|HockeyApp öncelikle beta dağıtım işleme ve çökme raporları elde etmek için yararlıdır.<br /><br /> C# komut dosyasından telemetri için, Unity tarafından kullanılan .NET sürümünde çalışması koşuluyla herhangi bir analiz çerçevesi kullanmak mümkündür. Ancak bu, Unity motorunun içinde değil, yalnızca oyun komut dosyaları içinde analiz yapılmasına olanak tanır. Şu anda Application Insights için eklenti yoktur, ancak eklentiler [Unity Analytics](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) ve [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity)gibi diğer analiz çözümleri için kullanılabilir. Birlik projesinin doğasını anlayan Unity Analytics gibi hizmetler elbette genel çerçevelerden çok daha anlamlı analizler sağlayacaktır.|
