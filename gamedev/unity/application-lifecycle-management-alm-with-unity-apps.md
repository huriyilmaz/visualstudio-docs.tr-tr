---
title: Unity Apps ile Uygulama Yaşam Döngüsü Yönetimi (ALM) | Microsoft Docs
description: Unity Uygulamaları ile uygulama yaşam döngüsü yönetimini (ALM) anlama. Çevik araçlar, model, kod, derleme, test ve geliştirme kod kalitesini gözden geçirme.
ms.date: 08/21/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a09519701bba5dde08649a3b4875f4b2f1a15490
ms.sourcegitcommit: ac681e983f3b217c3fd9d2a31e3a3ddcc4dd3546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2021
ms.locfileid: "132041893"
---
# <a name="devops-with-unity-apps"></a>DevOps Unity uygulamalarıyla birlikte kullanma

Modern platformlar için uygulama geliştirmek, yalnızca kod yazmaktan çok daha fazla etkinlik içerir. DevOps (geliştirme + işlemler) olarak adlandırılan bu etkinlikler uygulamanın tam yaşam döngüsünü içerir ve hem geliştirme hem de üretim ortamlarında çeşitli tanılama biçimlerini çalıştırmayı, kod tasarlamayı ve uygulamayı, kaynak kod deposunu yönetmeyi, derlemeleri çalıştırmayı, sürekli tümleştirmeleri ve dağıtımları yönetmeyi, test (birim testleri ve UI testleri dahil), hem geliştirme hem de üretim ortamlarında çeşitli tanılama biçimlerini çalıştırmayı ve uygulama performansı ile kullanıcı davranışlarını gerçek zamanlı olarak izlemeyi içerir telemetri ve analiz aracılığıyla.

Visual Studio, Azure DevOps Services Team Foundation Server ile birlikte birçok farklı DevOps sağlar. Bunların çoğu özellikle C# betik dili olarak kullanırken Unity ile oluşturulan oyunlar ve çevreleyici grafik uygulamaları dahil olmak üzere platformlar &mdash; arası projeler için geçerlidir. Ancak Unity'nin kendi geliştirme ortamı ve çalışma zamanı altyapısı olduğundan, DevOps yerleşik diğer proje türlerine olduğu gibi bir dizi Visual Studio.

Aşağıdaki tablolarda, DevOps Unity ile Visual Studio veya uygulanamayabilecek özellikler tanımları. Özelliklerin kendileri hakkında ayrıntılı bilgi için bağlantılı belgelere bakın.

## <a name="agile-tools"></a>Çevik araçlar

Başvuru bağlantısı: [Çevik araçlar ve Çevik proje yönetimi](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true) hakkında (Azure Boards veya TFS kullanarak) Team Explorer Everywhere)

Genel Açıklama: Tüm planlama ve izleme özellikleri proje türünden ve kodlama dillerinden bağımsızdır.

|Özellik|Unity ile desteklenen|Ek Açıklamalar|
|-------------|--------------------------|-------------------------|
|Biriktirme listesi ve sprint'leri yönetme|Yes||
|İş izleme|Yes||
|Takım odası işbirliği|Yes||
|Kanban panoları|Yes||
|İlerlemeyi bildirme ve görselleştirme|Yes||

## <a name="modeling"></a>Modelleme

Başvuru bağlantısı: **[Mimariyi analiz etme ve modelleme](/visualstudio/modeling/analyze-and-model-your-architecture)**

Genel Açıklama: Bu tasarım özellikleri kodlama dilinden bağımsız olsa da veya C# gibi .NET dilleriyle çalışsa da nesne hiyerarşileri ve sınıf ilişkileriyle geleneksel bir uygulama paradigması üzerinde çalışır. Unity içinde oyun tasarlamak için grafik nesneleri, sesleri, gölgelendiricileri, betikleri vb. içeren farklı bir paradigma vardır. Bu nedenle, Visual Studio modelleme diyagramı araçları bir Unity projesinin tamamıyla özellikle ilgili değildir. C# betikleri içindeki ilişkileri yönetmek için de kullanılabilirler ancak bu, tüm bunların yalnızca bir kısmıdır.

|Özellik|Unity ile desteklenen|Ek Açıklamalar|
|-------------|--------------------------|-------------------------|
|Sıralı diyagramlar|Hayır||
|Bağımlılık grafikleri|Hayır||
|Çağrı hiyerarşisi|Hayır||
|Sınıf tasarımcısı|Hayır||
|Mimari gezgini|Hayır||
|UML diyagramları (kullanım durumu, etkinlik, sınıf, bileşen, dizi ve DSL)|Hayır||
|Katman diyagramları|Hayır||
|Katman doğrulaması|Hayır||

## <a name="code"></a>Kod

|Özellik|Unity ile desteklenen|Ek Açıklamalar|
|-------------|--------------------------|-------------------------|
|[Team Foundation Sürüm Denetimi (TFVC) veya](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true) Azure Repos|Yes|Unity projeleri, diğer tüm projelerde olduğu gibi sürüm denetimi sistemlerine yerleştirilebilecek dosyaların bir koleksiyonudur, ancak bu tablodan sonra açıklanan birkaç özel konu vardır.|
|[Azure Repos'de Git'i Azure Repos](/azure/devops/repos/git/gitquickstart?view=vsts&preserve-view=true&tabs=visual-studio)|Yes|Tablodan sonra notlara bakın.|
|[Kod Kalitesini Geliştirme](/visualstudio/test/improve-code-quality)|Yes||
|[Kod değişikliklerini ve diğer geçmişi bulma](/visualstudio/ide/find-code-changes-and-other-history-with-codelens)|Yes||
|[Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](/visualstudio/modeling/use-code-maps-to-debug-your-applications)|Yes||

Unity ile sürüm denetimi için dikkat edilmesi gereken özel noktalar:

1. Unity, oyun varlıklarıyla ilgili meta verileri varsayılan olarak gizlenen tek bir opak kitaplıkta izler. Dosyaları ve meta verileri eşit durumda tutmak için meta verileri görünür yapmak ve daha yönetilebilir öbeklerde depolamak gerekir. Ayrıntılar için Bkz. [Unity ile Dış Sürüm Denetim Sistemlerini Kullanma](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Unity belgeleri).

2. Yukarıdaki bağlantıda da açıklandığı gibi unity projesinde yer alan tüm dosya ve klasörler kaynak denetimi için uygun değildir. Assets ve ProjectSettings klasörleri eklenmiştir, ancak Kitaplık ve Geçici klasörleri eklenmez. Kaynak denetimine girilemeyse de oluşturulan dosyaların ek listesi için StackOverflow'da [Unity3D](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) kaynak denetimi için Git kullanma? tartışmalarına bakın. Birçok geliştirici de bu konuya bağımsız olarak blog yazdı.

3. Unity projesinde dokular veya ses dosyaları gibi ikili varlıklar büyük miktarda depolama alanı kaplar. Git gibi çeşitli kaynak denetim sistemleri, değişiklik dosyanın yalnızca küçük bir bölümünü etkilese bile yapılan her değişiklik için bir dosyanın benzersiz bir kopyasını depolar. Bu, Git deposunun şişirilmiş hale neden olabilir. Unity geliştiricileri bu durumla karşılaşmak için genellikle depolarına yalnızca son varlıklar eklemeyi ve varlıklarının çalışma geçmişini (OneDrive, DropBox veya git-ek gibi) tutmanın farklı bir varlığını kullanmayı seçer. Bu yaklaşım işe yarar çünkü bu tür varlıkların genellikle kaynak kodu değişiklikleriyle birlikte sürümüne sahip olması gerekmektedir. Geliştiriciler ayrıca, metin dosyalarını ikili biçim yerine metinde depolamaya zorlamak için proje düzenleyicisinin Varlık Serileştirme Modu'nun da birleştirilmesini sağlar ve bu da kaynak denetiminde birleştirmelere olanak sağlar. Ayrıntılar için bkz. [Düzenleyici Ayarlar](https://docs.unity3d.com/Manual/class-EditorManager.html) (Unity belgeleri).

## <a name="build"></a>Derleme

Başvuru bağlantısı: **[Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)**

|Özellik|Unity ile desteklenen|Ek Açıklamalar|
|-------------|--------------------------|-------------------------|
|Şirket içi Team Foundation Server (TFS)|Mümkün|Unity projeleri, Visual Studio derleme sistemi aracılığıyla değil Unity ortamı aracılığıyla derlenmiş olur (Unity için Visual Studio Araçları derleme betikleri derler ancak yürütülebilir bir derleme oluşturmaz). Unity projelerini komut satırı [(Unity](https://docs.unity3d.com/Manual/CommandLineArguments.html) belgeleri) ile oluşturmak mümkündür. Bu nedenle, Unity'nin kendisi bu bilgisayara yüklenmiş olması şartıyla TFS sunucusundaki bir MSBuild işlemini uygun Unity komutlarını yürütacak şekilde yapılandırmak mümkündür.<br /><br /> Unity ayrıca Git veya SVN deposunu izleyen ve düzenli derlemeler çalıştıran [Unity Cloud Build](https://build.cloud.unity3d.com/landing/)sunar. Şu anda TFVC veya Azure DevOps Services.|
|Şirket içi derleme sunucusu Azure DevOps Services|Mümkün|Yukarıdaki koşullarla aynı olduğu sürece, şirket içi TFS bilgisayarı kullanmak için Azure DevOps Services derlemeleri doğrudan yönlendirebilirsiniz. Yönergeler [için bkz. Derleme ve](/azure/devops/pipelines/agents/agents?view=vsts&preserve-view=true) sürüm aracıları.|
|Azure DevOps Services'nin barındırılan denetleyici hizmeti|Hayır|Unity derlemeleri şu anda desteklenmiyor.|
|Ön ve son betiklerle tanım oluşturma|Yes|Derlemeyi çalıştırmak için Unity komut satırı kullanan özel bir derleme tanımı, derleme öncesi ve sonrası betikler için de yalıtabilirsiniz.|
|Geçitli iadeler de dahil olmak üzere sürekli tümleştirme|Yes|TFVC için geçitli iadeler yalnızca Git iadeler yerine çekme isteği modelinde çalışır.|

## <a name="test"></a>Test etme

|Özellik|Unity ile desteklenen|Ek Açıklamalar|
|-------------|--------------------------|-------------------------|
|Testleri planlama, test çalışmalarını oluşturma ve test paketlerini düzenleme|Yes||
|El ile test etme|Yes||
|Test Yöneticisi (kayıt ve kayıttan yürütme testleri)|Windows cihazları ve Android öykünücülerini destekler||
|Kod kapsamı|yok|Birim testi Unity'de olduğu için geçerli değildir ve Visual Studio aşağıya bakın.|
|[Kodunuzu birim testi](/visualstudio/test/unit-test-your-code)|Unity içinde, ancak Visual Studio|Unity, Unity test araçlarının (Unity Varlık Deposu) bir [parçası olarak kendi](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802) birim test çerçevesini sağlar. Birim testi sonuçları Unity içinde raporlanmaz ve birim içinde Visual Studio.|
|[Kodunuzu test etmek için UI otomasyonunu kullanma](/visualstudio/test/use-ui-automation-to-test-your-code)|Hayır|Kodlanmış UI testleri, uygulamanın kullanıcı arabiriminde okunabilir denetimlere güvenmektedir; Unity uygulamaları doğası gereği grafikseldir ve bu nedenle kodlanmış UI test araçları tarafından içerik okunamaz.|

## <a name="improve-code-quality"></a>Kod kalitesini geliştirme

Başvuru bağlantısı: **[Kod kalitesini geliştirme](/visualstudio/test/improve-code-quality)**

|Özellik|Unity ile desteklenen|Ek Açıklamalar|
|-------------|--------------------------|-------------------------|
|[Yönetilen kod kalitesini analiz etme](/visualstudio/code-quality/code-analysis-for-managed-code-overview)|Yes|C# betik kodunu analiz etmek için Visual Studio.|
|[Kod kopyalama algılamayı kullanarak yinelenen kod bulma](https://msdn.microsoft.com/library/hh205279.aspx)|Yes|C# betik kodunu analiz etmek için Visual Studio.|
|[Yönetilen kodun karmaşıklığını ve sürdürülebilirliğini ölçme](/visualstudio/code-quality/code-metrics-values)|Yes|C# betik kodunu analiz etmek için Visual Studio.|
|[Performans araçları](/visualstudio/profiling/performance-explorer)|Hayır|Unity [Profiler'i](https://docs.unity3d.com/Manual/Profiler.html) (Unity web sitesi) kullanın.|
|.NET Framework bellek sorunlarını çözümleme|Hayır|Visual Studio araçları, profil oluşturma için Mono çerçevesine (Unity tarafından kullanılan şekilde) bağlı değildir. Unity [Profiler'i (Unity](http://docs.unity3d.com/Manual/Profiler.html) belgeleri) kullanın.|

## <a name="release-management"></a>Yayın yönetimi

Başvuru bağlantısı: [Azure Pipelines ve TFS'de derleme ve yayın](/azure/devops/pipelines/overview?view=vsts&preserve-view=true)

|Özellik|Unity ile desteklenen|Ek Açıklamalar|
|-------------|--------------------------|-------------------------|
|Yayın işlemlerini yönetme|Yes||
|Betikler aracılığıyla yan yükleme için sunuculara dağıtım|Yes||
|Upload app store'a|Kısmi|Bazı uygulama mağazalarında bu işlemi otomatikleştiren uzantılar mevcuttur. Bkz. [Uzantılar Azure DevOps Services;](https://marketplace.visualstudio.com/VSTS) Örneğin, için [uzantısı Google Play.](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play)|

## <a name="monitor-with-hockeyapp"></a>HockeyApp ile izleme

Başvuru bağlantısı: **[HockeyApp ile izleme](https://marketplace.visualstudio.com/items?itemName=ms.hockeyapp)**

|Özellik|Unity ile desteklenen|Ek Açıklamalar|
|-------------|--------------------------|-------------------------|
|Kilitlenme analizi, telemetri ve beta dağıtımı|Yes|HockeyApp, beta dağıtımını işleme ve kilitlenme raporlarını alma konusunda öncelikli olarak yararlıdır.<br /><br /> C# betiklerinden gelen telemetri için, Unity tarafından kullanılan .NET sürümünde çalıştırması şartıyla herhangi bir analiz çerçevesini kullanmak mümkündür. Ancak, bu yalnızca oyun betikleri içinde analize olanak sağlar ve Unity altyapısının daha derine iner. Şu anda Application Analizler için eklenti yoktur, ancak [Unity Analytics](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) ve Google Analytics gibi diğer analiz çözümleri için eklentiler [kullanılabilir.](https://github.com/googleanalytics/google-analytics-plugin-for-unity) Unity projesinin doğasını anan Unity Analytics gibi hizmetler, elbette genel çerçevelerden çok daha anlamlı analizler sağlar.|
