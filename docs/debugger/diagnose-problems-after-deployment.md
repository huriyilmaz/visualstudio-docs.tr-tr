---
title: Dağıtım sonrasında sorunları tanılama | Microsoft Docs
description: Şirket içinde IntelliTrace kullanarak dağıtımdan sonra sorunları Visual Studio. Sürümünize derleme bilgilerini dahil edin. Sorunu bulmak için uygulamanızı bırakın ve takip edin.
ms.custom: SEO-VS-2020
ms.date: 04/10/2018
ms.topic: how-to
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 192389c32a8ff5193b545a1a4159441bab298a8b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725429"
---
# <a name="diagnose-problems-after-deployment-using-intellitrace-c-visual-basic"></a>IntelliTrace kullanarak dağıtımdan sonra sorunları tanılama (C#, Visual Basic)

IntelliTrace kullanarak dağıtımdan sonra ASP.NET web uygulamanıza ilişkin sorunları tanılamak için, derleme bilgilerini sürümünize dahil edin ve Visual Studio'nin IntelliTrace günlüğünde hata ayıklamak için gereken doğru kaynak dosyaları ve sembol dosyalarını otomatik olarak bulmasını sağlar.

 IntelliTrace'i Microsoft Monitoring Agent için bir uygulama kullanıyorsanız, web sunucunuzda uygulama performansı izlemesini de ayarlamanız gerekir. Bu, uygulama çalışırken tanılama olaylarını kaydeder ve olayları bir IntelliTrace günlük dosyasına kaydeder. Ardından Visual Studio Enterprise'daki olaylara bakabilirsiniz (ancak Professional veya Community sürümlerine bakmaz), olayın meydana olduğu koda gidebilir, zaman içinde kaydedilen değerlere bakabilir ve bu kodun içinde ileri veya geri gidebilirsiniz. Sorunu bulup düzeltdikten sonra, gelecekteki olası sorunları daha önce ve daha hızlı çözüme kavuşturmanızı sağlayacak şekilde sürümü derlemek, serbest bırakmak ve izlemek için döngüye tekrarlayın.

 ![Kod, derleme, sürüm, izleme, tanılama, düzeltme](../debugger/media/ffr_cycle.png "FFR_Cycle")

 **Şunlara ihtiyacınız var:**

- Visual Studio, Azure DevOps veya Team Foundation Server 2017, 2015, 2013, 2012 veya 2010

- Microsoft Monitoring Agent izleme ve tanılama verilerini kaydetme

- Visual Studio Enterprise verileri gözden geçirmek ve IntelliTrace ile Professional hata ayıklamak için Community veya Community sürümlerine sahip değil)

## <a name="step-1-include-build-information-with-your-release"></a><a name="SetUpBuild"></a> 1. Adım: Sürümünize derleme bilgilerini dahil edin
 Derleme işleminizi, web projeniz için bir derleme *bildirimi (BuildInfo.config* dosyası) oluşturmak ve bu bildirimi yayına dahil etmek için ayarlayın. Bu bildirim, belirli bir derlemeyi oluşturmak için kullanılan proje, kaynak denetimi ve derleme sistemi hakkında bilgi içerir. Bu bilgiler, Visual Studio intelliTrace günlüğünü açtıktan sonra eşleşen kaynak ve sembolleri bulumanıza yardımcı olur.

### <a name="create-the-build-manifest-for-an-automated-build-using-team-foundation-server"></a><a name="AutomatedBuild"></a>Team Foundation Server kullanarak otomatik derleme için derleme bildirimi Team Foundation Server

 İster Git ister Team Foundation Sürüm Denetimi bu adımları izleyin.

#### <a name="azure-devops-and-team-foundation-server-2017"></a><a name="TFS2017"></a>Azure DevOps ve Team Foundation Server 2017

Visual Studio 2017 ve sonraki sürümler, *kullanım dışıBuildInfo.config* kaldırılan bir dosya içermez. Dağıtımdan sonra ASP.NET web uygulamalarının hata ayıklaması için aşağıdaki yöntemlerden birini kullanın:

* Azure'a dağıtım için [Application Analizler.](/azure/application-insights/)

* IntelliTrace'i kullanmak için projeyi Visual Studio ve eşleşen derlemeden sembol dosyalarını yükleme. Sembol dosyalarını Modüller penceresinden **veya Araçlar Seçenekler** Hata Ayıklama Sembolleri'nin altında sembolleri  >    >  **yapılandırarak**  >  **yükleyebilirsiniz.**

#### <a name="team-foundation-server-2013"></a><a name="TFS2013"></a>Team Foundation Server 2013
 Derleme bildirimine (derleme dosyası) kaynak, derleme ve sembollerinizin konumlarını eklemek için derleme işlem hattınızı BuildInfo.config ayarlayın. Team Foundation Build bu dosyayı otomatik olarak oluşturur ve projenizin çıkış klasörüne koyar.

1. [Derleme işlem hattınızı düzenleyin veya yeni bir derleme işlem hattı oluşturun.](/azure/devops/pipelines/get-started-designer?view=vsts&preserve-view=true)

     ![TFS 2013'te derleme işlem hattını görüntüleme](../debugger/media/ffr_tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")

2. Varsayılan şablon (TfvcTemplate.12.xaml) veya kendi özel şablonunuzu seçin.

     ![TFS 2013 &#45; oluşturma işlemi şablonunu seçme](../debugger/media/ffr_tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")

3. Kaynağınız otomatik olarak dizine alındıklarından emin olmak için sembollerin (PDB) nereye kaydedilir olduğunu belirtin.

     Özel bir şablon kullanırsanız, şablonun kaynağınızı dizinleyecek bir aktivitesi olduğundan emin olun. Daha sonra, sembollerin nereye MSBuild belirtmek için bir bağımsız değişken ekleyebilirsiniz.

     ![Derleme işlem hattı TFS 2013'te sembol yolu ayarlama](../debugger/media/ffr_tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")

     Semboller hakkında daha fazla bilgi için [bkz. Sembol verilerini yayımlama.](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols?view=vsts&preserve-view=true)

4. Derleme bildirimi MSBuild TFS ve semboller konumlarınızı eklemek için bu bağımsız değişkeni ekleyin:

     **/p:IncludeServerNameInBuildInfo=True**

     Web sunucunuza erişen herkes bu konumları derleme bildiriminde görebilir. Kaynak sunucunuz güvenli olduğundan emin olun.

5. Özel bir şablon kullanıyorsanız, semboller dosyasının MSBuild belirtmek için bu bağımsız değişkeni ekleyin:

     **/p:BuildSymbolStorePath=**\<*path to symbols*>

     ![Derleme def TFS 2013'e derleme sunucusu bilgilerini dahil etme](../debugger/media/ffr_tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")

     Ve web proje dosyanıza (.csproj, .vbproj) bu satırları ekleyin:

    ```xml
    <!-- Import the targets file. Change the folder location as necessary. -->
       <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />

    ```

     Web sunucunuza erişen herkes bu konumları derleme bildiriminde görebilir. Kaynak sunucunuz güvenli olduğundan emin olun.

6. Yeni bir yapı çalıştırın.

    [2. Adım: Uygulamanızı serbest bırakma'ya gidin](#DeployRelease)

#### <a name="team-foundation-server-2012-or-2010"></a><a name="TFS2012_2010"></a>Team Foundation Server 2012 veya 2010
 Projeniz için derleme bildirimini (BuildInfo.config dosyası) otomatik olarak oluşturmak ve dosyayı projenizin çıkış klasörüne koymak için bu adımları izleyin. Dosya, çıkış klasöründe *"ProjectName*.BuildInfo.config" olarak görünür ancak siz BuildInfo.config dağıtım klasöründe "BuildInfo.config" olarak yeniden adlandırılır.

1. Team Foundation Visual Studio 2013 sunucunuza bir sürüm (herhangi bir sürüm) yükleyin.

2. Derleme işlem hattında, kaynağınız otomatik olarak dizine alındıklarından emin olmak için sembollerin kaydedilene bir yer belirtin.

     Özel bir şablon kullanırsanız, şablonun kaynağınızı dizinleyecek bir aktivitesi olduğundan emin olun.

3. Bu bağımsız MSBuild derleme işlem hattınıza ekleyin:

    - **/p:VisualStudioVersion=12.0**

    - **/p:MSBuildAssemblyVersion=12.0**

    - **/tv:12.0**

    - **/p:IncludeServerNameInBuildInfo=True**

    - **/p:BuildSymbolStorePath=**\<*path to symbols*>

4. Yeni bir yapı çalıştırın.

    [2. Adım: Uygulamanızı serbest bırakma'ya gidin](#DeployRelease)

### <a name="create-the-build-manifest-for-a-manual-build-using-visual-studio"></a><a name="ManualBuild"></a>Visual Studio kullanarak el ile derleme için derleme bildirimi oluşturma
 Projeniz için derleme bildirimini (BuildInfo.config dosyası) otomatik olarak oluşturmak ve dosyayı projenizin çıkış klasörüne koymak için bu adımları izleyin. Dosya, çıkış klasöründe *"ProjectName*.BuildInfo.config" olarak görünür ancak siz BuildInfo.config dağıtım klasöründe "BuildInfo.config" olarak yeniden adlandırılır.

1. Bu **Çözüm Gezgini** web projenizi kaldır.

2. Proje dosyasını (.csproj, .vbproj) açın. Şu satırları ekleyin:

    ```xml
    <!-- **************************************************** -->
    <!-- Build info -->
    <PropertyGroup>
       <!-- Generate the BuildInfo.config file -->
       <GenerateBuildInfoConfigFile>True</GenerateBuildInfoConfigFile>
       <!-- Include server name in build info -->
       <IncludeServerNameInBuildInfo>True</IncludeServerNameInBuildInfo>
       <!-- Include the symbols path so Visual Studio can find the matching deployed code when you start debugging. -->
       <BuildSymbolStorePath><path to symbols></BuildSymbolStorePath>
    </PropertyGroup>
    <!-- **************************************************** -->
    ```

3. Güncelleştirilen proje dosyasında denetleyin.

4. Yeni bir yapı çalıştırın.

    [2. Adım: Uygulamanızı serbest bırakma'ya gidin](#DeployRelease)

### <a name="create-the-build-manifest-for-a-manual-build-using-msbuildexe"></a><a name="MSBuild"></a> MSBuild.exe kullanarak el ile derleme için derleme bildirimi MSBuild.exe
 Derlemeyi çalıştırarak şu derleme bağımsız değişkenlerini ekleyin:

 **/p:GenerateBuildInfoConfigFile=True**

 **/p:IncludeServerNameInBuildInfo=True**

 **/p:BuildSymbolStorePath=**\<*path to symbols*>

## <a name="step-2-release-your-app"></a><a name="DeployRelease"></a> 2. Adım: Uygulamalarınızı serbest bırakma
 Uygulamanızı dağıtmak için derleme işleminiz tarafından oluşturulan [Web.Deploy](/previous-versions/aspnet/dd394698(v=vs.110)) paketini kullanırsanız, derleme bildirimi otomatik olarak "*ProjectName*.BuildInfo.config" yerine "BuildInfo.config" olarak yeniden adlandırılır ve web sunucunuzda uygulamanızın Web.config dosyasıyla aynı klasöre eklenir.

 Uygulamanızı dağıtmak için başka yöntemler kullanırsanız, derleme bildiriminin "*ProjectName*.BuildInfo.config" yerine "BuildInfo.config" olarak yeniden adlandırıldıklarından ve web sunucusunda uygulamanızın Web.config dosyasıyla aynı klasöre geçirildiklerinden emin olun.

## <a name="step-3-monitor-your-app"></a>Adım 3: Uygulamanızı izleyin
 Web sunucunuzda uygulama performansı izlemesini ayarlayın; böylece uygulamanızı sorunlar için izleyebilir, tanılama olaylarını kaydedebilir ve bu olayları bir IntelliTrace günlük dosyasına kaydedebilirsiniz. Bkz. [Dağıtım sorunları için sürümü izleme.](../debugger/using-the-intellitrace-stand-alone-collector.md)

## <a name="step-4-find-the-problem"></a><a name="InvestigateEvents"></a> 4. Adım: Sorunu bulma
 Kaydedilen olayları gözden geçirmek Visual Studio Enterprise IntelliTrace kullanarak kodunuzun hata ayıklaması için geliştirme bilgisayarınızda veya başka bir bilgisayarda yeni bir bilgisayar gerekir. Sorunu tanılamanıza yardımcı olmak için CodeLens, hata ayıklayıcı eşlemeleri ve kod eşlemeleri gibi araçları da kullanabilirsiniz.

### <a name="open-the-intellitrace-log-and-matching-solution"></a>IntelliTrace günlüğünü ve eşleşen çözümü açın

1. IntelliTrace günlüğünü (.iTrace dosyası) Visual Studio Enterprise. Veya aynı bilgisayarda bir dosyanız varsa Visual Studio Enterprise çift tıklayın.

2. Proje **bir çözümün** parçası Visual Studio eşleşen çözümü veya projeyi otomatik olarak açmak için Çözümü aç'ı seçin. [S: IntelliTrace günlüğünde dağıtılan uygulamam hakkında eksik bilgiler var. Bu neden oldu? Ne yapabilirim?](#InvalidConfigFile)

     Visual Studio çözümü veya projeyi açtığında bekleyen değişiklikleri otomatik olarak rafa alacak. Bu raf kümesi hakkında daha fazla ayrıntı almak için Çıkış **penceresine bakın veya** **Takım Gezgini.**

     Herhangi bir değişiklik yapmadan önce doğru kaynağın siz olduğunu onaylayın. Dallama kullanıyorsanız, yayın dalınız gibi eşleşen kaynağı Visual Studio farklı bir dalda çalışıyor olabilirsiniz.

     ![IntelliTrace günlüğünden çözümü açma](../debugger/media/ffr_itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")

     Bu çözüme veya projeye eşlenmiş mevcut bir çalışma alanınız Visual Studio, bulduğu kaynağı koymak için çalışma alanını seçer.

     ![Kaynak denetiminden eşlenmiş çalışma alanına açma](../debugger/media/ffr_openprojectfromsourcecontrol_mapped.png "FFR_OpenProjectFromSourceControl_Mapped")

     Aksi halde, zaten eşleşmiş başka bir çalışma alanı seçin veya yeni bir çalışma alanı oluşturun. Visual Studio tüm dalı bu çalışma alanına eşleyecektir.

     ![Kaynak denetiminden Aç &#45; yeni çalışma alanı oluştur](../debugger/media/ffr_openprojectfromsourcecontrol_createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")

     Belirli eşlemelere veya bilgisayarınızın adı olmayan bir ada sahip bir çalışma alanı oluşturmak için **Yönet**' i seçin.

     [s: seçili çalışma alanım neden Visual Studio söyleyin?](#IneligibleWorkspace)

     [S: bir takım koleksiyonu veya farklı bir koleksiyon seçinceye kadar niçin devam edemiyorum?](#ChooseTeamProject)

### <a name="diagnose-a-performance-problem"></a>Performans sorunu tanıla

1. **Performans ihlalleri** altında, kaydedilen performans olaylarını, bunların toplam yürütme sürelerini ve diğer olay bilgilerini gözden geçirin. Sonra belirli performans olayı sırasında çağrılan yöntemlerde fazla araştırma yapın.

     ![Performans olayı ayrıntılarını görüntüleme](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")

     Ayrıca, olayı çift tıklatabilirsiniz.

2. Olay sayfasında, bu çağrılar için yürütme zamanını gözden geçirin. Yürütme ağacında yavaş bir çağrı bulun.

     İç içe ya da başka şekilde birden fazla çağrınız varsa, en yavaş çağrılar kendi bölümünde görüntülenir.

     Yuvalanmış çağrıları ve zamanın o anında kaydedilmiş değerleri gözden geçirmek için o çağrıyı genişletin. Sonra o çağrıdan hata ayıklamayı başlatın.

     ![Yöntem çağrısından hata ayıklamayı Başlat](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")

     Ayrıca, aramayı çift tıklatabilirsiniz.

     Yöntem uygulama kodunuzda ise, Visual Studio bu yönteme gider.

     ![Performans olayından uygulama koduna git](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")

     Artık kaydedilen diğer değerleri, çağrı yığınını gözden geçirebilir, kodunuzda adım adım ilerlerseniz veya bu performans olayı sırasında çağrılan [diğer yöntemler arasında "zamanda" geriye veya ileri doğru gitmek](../debugger/intellitrace.md) için **IntelliTrace** penceresini kullanabilirsiniz.

    - [IntelliTrace günlüğündeki tüm bu olaylar ve bilgiler nelerdir?](../debugger/using-saved-intellitrace-data.md)
    - [Buradan başka ne yapabilirim?](#WhatElse)
    - [Performans olayları hakkında daha fazla bilgi mi istiyorsunuz?](https://devblogs.microsoft.com/devops/performance-details-in-intellitrace/)

### <a name="diagnose-an-exception"></a>Bir özel durumu tanıla

1. **Özel durum verileri** altında, kaydedilen özel durum olaylarını, türleri, iletileri ve özel durumların ne zaman oluştuğunu gözden geçirin. Kodu daha ayrıntılı incelemek için özel durumlar grubu içindeki en son olaydan başlayın.

     ![Özel durum olayından hata ayıklamayı Başlat](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")

     Ayrıca, olayı çift tıklatabilirsiniz.

     Uygulama kodunuzda bir özel durum oluştuysa, Visual Studio özel durumun olduğu yere gider.

     ![Özel durum olayından uygulama koduna git](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")

     Artık kaydedilen diğer değerleri, çağrı yığınını gözden geçirebilir veya diğer kayıtlı olaylar, ilgili kod ve bu noktalarda kaydedilmiş değerler [arasında "zamanda" geriye veya ileri doğru gitmek](../debugger/intellitrace.md)için **IntelliTrace** penceresini kullanabilirsiniz.

     [IntelliTrace günlüğündeki tüm bu olaylar ve bilgiler nelerdir?](../debugger/using-saved-intellitrace-data.md)

### <a name="what-else-can-i-do-from-here"></a><a name="WhatElse"></a> Buradan başka ne yapabilirim?

- [Bu kod hakkında daha fazla bilgi alın](../ide/find-code-changes-and-other-history-with-codelens.md). Bu koda yapılan başvuruları, değişiklik geçmişini, ilgili hataları, iş öğelerini, kod incelemelerini veya birim testlerini, Düzenleyiciden çıkmadan bulmak için, düzenleyicide CodeLens göstergelerini kullanın.

     ![CodeLens &#45; bu koda yönelik başvuruları görüntüle](../debugger/media/ffr_itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")

     ![CodeLens &#45; bu kodun değişiklik geçmişini görüntüle](../debugger/media/ffr_itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")

- [Hata ayıklarken kodunuzda yerinizi eşleyin.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) Hata ayıklama sırasında aranan yöntemleri görsel izlemek için çağrı yığınını eşleyin.

     ![Hata ayıklarken çağrı yığınını eşleyin](../debugger/media/ffr_itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")

### <a name="q--a"></a><a name="FAQ"></a> SORU-CEVAP &

#### <a name="q-why-include-information-about-my-project-source-control-build-and-symbols-with-my-release"></a><a name="WhyInclude"></a> S: neden projem, kaynak denetimi, derleme ve sembolle ilgili bilgileri benim yayınmla içersin?
 Visual Studio, bu bilgileri, hata ayıklamaya çalıştığınız sürümün eşleşen çözümünü ve kaynağını bulmak için kullanır. ıntellitrace günlüğünü açtıktan ve hata ayıklamayı başlatacak bir olay seçtikten sonra Visual Studio, bir olayın gerçekleştiği kodu bulmak ve göstermek için sembolleri kullanır. Daha sonra, kaydedilen değerlere bakabilir ve kodunuzun yürütülmesi sırasında iletme veya geriye doğru taşıyabilirsiniz.

 TFS kullanıyorsanız ve bu bilgiler derleme bildiriminde (BuildInfo.config dosyasında) yoksa, Visual Studio, bağlı olan TFS 'deki eşleşen kaynak ve sembolleri arar. Visual Studio doğru tfs veya eşleşen kaynağı bulamazsa, farklı bir tfs seçmeniz istenir.

#### <a name="q-the-intellitrace-log-is-missing-information-about-my-deployed-app-why-did-this-happen-what-do-i-do"></a><a name="InvalidConfigFile"></a> S: IntelliTrace günlüğünde, dağıtılan Uygulamam hakkında bilgiler eksik. Bunun nedeni neden oldu? Ne yapmalıyım?
 Bu durum, geliştirme bilgisayarınızdan dağıtırken veya dağıtım sırasında TFS 'ye bağlı olmadığınız durumlarda gerçekleşebilir.

1. Projenizin dağıtım klasörüne gidin.

2. Derleme bildirimini bulun ve açın (BuildInfo.config dosyası).

3. Dosyanın gerekli bilgileri içerdiğinden emin olun:

- **ProjectName**

   Visual Studio içindeki projenizin adı. Örnek:

  ```xml
  <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>
  ```

- **SourceControl**

- Kaynak denetimi sisteminiz ve bu gerekli özellikler hakkında bilgi:

  - **TFS**

    - **projectcollectionuri**: Team Foundation Server ve proje koleksiyonunuz için urı

    - **ProjectItemSpec**: uygulamanızın proje dosyasının yolu (. csproj veya. vbproj)

    - **ProjectVersionSpec**: projenizin sürümü

      Örnek:

    ```xml
    <SourceControl type="TFS">
       <TfsSourceControl>
          <ProjectCollectionUri>http://fabrikamfiber:8080/tfs/FabrikamFiber</ProjectCollectionUri>
          <ProjectItemSpec>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectItemSpec>
          <ProjectVersionSpec>LFabrikamFiber_BuildAndPublish_20130813@$/WorkInProgress</ProjectVersionSpec>
       </TfsSourceControl>
    </SourceControl>
    ```

  - **Git**

    - **GitSourceControl**: **GitSourceControl** şemasının konumu

    - **havuz url 'si**: Team Foundation Server, proje koleksiyonunuz ve Git deponuzun urı 'si

    - **ProjectPath**: uygulamanızın proje dosyasının yolu (. csproj veya. vbproj)

    - **CommitId**: yürütmeniz için kimlik

      Örnek:

    ```xml
    <SourceControl type="Git">
       <GitSourceControl xmlns="http://schemas.microsoft.com/visualstudio/deploymentevent_git/2013/09">
          <RepositoryUrl>http://gittf:8080/tfs/defaultcollection/_git/FabrikamFiber</RepositoryUrl>
          <ProjectPath>/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectPath>
          <CommitId>50662c96502dddaae5cd5ced962d9f14ec5bc64d</CommitId>
       </GitSourceControl>
    </SourceControl>
    ```

- **Derleme**

   `"TeamBuild"`Ya da `"MSBuild"` ve bu gerekli özellikler ile derleme sisteminiz hakkında bilgi:

  - **BuildLabel** (TeamBuild için): derleme adı ve numarası. Bu etiket, dağıtım olayının adı olarak da kullanılır. Derleme numaraları hakkında daha fazla bilgi için bkz. [Tamamlanan yapılara anlamlı adlar sağlamak için yapı numaralarını kullanma](/azure/devops/pipelines/build/options?view=vsts&preserve-view=true).

  - **SymbolPath** (önerilen): SIMGELER (pdb dosyası) konumlarına yönelik URI 'lerin noktalı virgülle ayrılmış listesi. Bu URI 'Ler URL veya UNCs olabilir. bu, Visual Studio hata ayıklamanıza yardımcı olmak için eşleşen sembolleri bulmasını kolaylaştırır.

  - **BuildReportUrl** (TeamBuild için): TFS 'de yapı raporunun konumu

  - **BuildId** (TeamBuild için): TFS 'deki derleme ayrıntıları için URI. Bu URI, dağıtım olayının KIMLIĞI olarak da kullanılır. TeamBuild kullanmıyorsanız bu KIMLIK benzersiz olmalıdır.

  - **builtsolution**: Visual Studio eşleşen çözümü bulmak ve açmak için kullandığı çözüm dosyasının yolu. Bu, **SolutionPath** MSBuild özelliğinin içeriğidir.

    Örnek:

  - **TFS**

    ```xml
    <Build type="TeamBuild">
       <MsBuild>
          <BuildLabel kind="label">FabrikamFiber_BuildAndPublish_20130813.1</BuildLabel>
          <SymbolPath>\\fabrikamfiber\FabrikamFiber.CallCenter\Symbols</SymbolPath>
          <BuildReportUrl kind="informative, url" url="http://fabrikamfiber:8080/tfs/FabrikamFiber/_releasePipeline/FindRelease?buildUri=fabrikamfiber%3a%2f%2f%2fBuild%2fBuild%2f448">Build Report Url</BuildReportUrl>
          <BuildId kind="id">1c4444d2-518d-4673-a590-dce2773c7744,fabrikamfiber:///Build/Build/448</BuildId>
          <BuiltSolution>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>
       </MsBuild>
    </Build>
    ```

  - **Git**

    ```xml
    <Build type="MSBuild">
       <MSBuild>
          <SymbolPath>\\gittf\FabrikamFiber.CallCenter\Symbols</SymbolPath>
          <BuiltSolution>/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>
       </MSBuild>
    </Build>
    ```

#### <a name="q-why-does-visual-studio-say-my-selected-workspace-is-ineligible"></a><a name="IneligibleWorkspace"></a>s: seçili çalışma alanım neden Visual Studio söyleyin?
 Y **:** Seçilen çalışma alanı, kaynak denetim klasörü ve yerel klasör arasında herhangi bir eşlemeye sahip değil. Bu çalışma alanı için bir eşleme oluşturmak için **Yönet**' i seçin. Aksi halde, zaten eşleşmiş bir çalışma alanı seçin veya yeni bir çalışma alanı oluşturun.

 ![Eşlenmiş çalışma alanı olmadan kaynak denetiminden Aç](../debugger/media/ffr_openprojectfromsourcecontrol_notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")

#### <a name="q-why-cant-i-continue-until-i-choose-a-team-collection-or-a-different-collection"></a><a name="ChooseTeamProject"></a> S: bir takım koleksiyonu veya farklı bir koleksiyon seçinceye kadar niçin devam edemiyorum?
 Y **:** Bunun nedeni şu nedenlerden herhangi biri olabilir:

- Visual Studio TFS'ye bağlı değildir.

     ![&#45; bağlı değil kaynak denetiminden Aç](../debugger/media/ffr_openprojectfromsourcecontrol_notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")

- Visual Studio geçerli takım koleksiyonunuzda çözüm ya da proje bulamadı.

     yapı bildirim dosyası ( \<*ProjectName*> . BuildInfo.config) Visual Studio eşleşen kaynağı nerede bulabileceğinizi belirtmezse, Visual Studio eşleşen çözümü veya projeyi bulmak için şu anda bağlı olan TFS 'yi kullanır. Geçerli takım koleksiyonunuzda eşleşen kaynak yoksa, Visual Studio farklı takım koleksiyonuna bağlanmanızı ister.

- Visual Studio derleme bildirimi dosyası ( .BuildInfo.config) tarafından belirtilen koleksiyonda çözüm veya \<*ProjectName*> projeyi bulamadınız.

     Belirtilen TFS artık eşleşen kaynağa sahip olmayabilir, hatta yeni bir TFS'ye geçtiğiniz için hiç varolmayabilir. Belirtilen TFS mevcut değilse Visual Studio bir dakika ya da sonrasında zaman aşımına uğrayabilir ve bu durumda sizden farklı bir koleksiyona bağlanmanız istenebilir. Devam etmek için doğru TFS sunucusuna bağlanın.

     ![Geçirilen kaynak denetimi &#45; açma](../debugger/media/ffr_openprojectfromsourcecontrol_migrated.png "FFR_OpenProjectFromSourceControl_Migrated")

#### <a name="q-whats-a-workspace"></a><a name="WhatWorkspace"></a> S: Çalışma alanı nedir?
 **A:** Çalışma [alanınız kaynağın bir kopyasını depolar,](/azure/devops/repos/tfvc/create-work-workspaces?view=vsts&preserve-view=true) böylece çalışmanızı iade etmeden önce bu kopyayı ayrı olarak geliştirebilir ve test edin. Bulunan çözümle veya projeyle özel olarak eşleşen bir çalışma alanı yoksa, Visual Studio varsayılan çalışma alanı adı olarak bilgisayar adınızla birlikte yeni bir çalışma alanı oluşturmanızı veya mevcut bir çalışma alanı seçmenizi ister.

#### <a name="q-why-do-i-get-this-message-about-untrusted-symbols"></a><a name="UntrustedSymbols"></a> S: Güvenilmeyen sembollerle ilgili bu iletiyi neden alıyorum?
 ![Güvenilmeyen sembollerle hata ayıklama yolu](../debugger/media/ffr_ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")

 **A:** Bu ileti, derleme bildirimi dosyasındaki (.BuildInfo.config) sembol yolu güvenilen sembol yolları \<*ProjectName*> listesine dahil etmediği zaman görüntülenir. Hata ayıklama seçeneklerindeki sembol yolu listesine yolu ekleyebilirsiniz.