---
title: Dağıtımdan sonra sorunları tanılama | Microsoft Docs
ms.date: 04/10/2018
ms.topic: conceptual
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bae6a7f5e95f2d853978cf1f8d9665a51ae80fd3
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911378"
---
# <a name="diagnose-problems-after-deployment-using-intellitrace-c-visual-basic"></a>IntelliTrace kullanarak dağıtımdan sonra sorunları tanılama (C#, Visual Basic)

IntelliTrace kullanarak dağıtımdan sonra ASP.NET Web uygulamanızdaki sorunları tanılamak için, Visual Studio 'Nun IntelliTrace günlüğünde hata ayıklamak için gerekli olan doğru kaynak dosyaları ve sembol dosyalarını otomatik olarak bulmasını sağlamak üzere yayınınızdan derleme bilgilerini ekleyin.

 IntelliTrace 'i denetlemek için Microsoft Monitoring Agent kullanıyorsanız, Web sunucunuzda uygulama performansı izlemeyi ayarlamayı da ayarlamanız gerekir. Bu, uygulamanız çalışırken Tanılama olaylarını kaydeder ve olayları bir IntelliTrace günlük dosyasına kaydeder. Daha sonra Visual Studio Enterprise (Professional veya Community Edition değil) içindeki olaylara bakabilir, bir olayın gerçekleştiği koda gidebilir, o zaman içindeki kayıtlı değerlere bakabilirsiniz ve iletilen kodu kullanarak iletme veya geriye doğru taşıyabilirsiniz. Sorunu bulduktan ve düzelttikten sonra, daha önce ve daha hızlı olabilecek olası sorunları çözebilmek için sürümünüzü oluşturma, yayınlama ve izleme döngüsünü yineleyin.

 ![Kod, derleme, yayınlama, izleme, tanılama, onarma](../debugger/media/ffr_cycle.png "FFR_Cycle")

 **Şunlar gerekir:**

- Derlemenizi ayarlamak için Visual Studio, Azure DevOps veya Team Foundation Server 2017, 2015, 2013, 2012 veya 2010

- Uygulamanızı izlemek ve tanılama verilerini kaydetmek için Microsoft Monitoring Agent

- Tanılama verilerini gözden geçirmek ve IntelliTrace ile kodunuzun hatalarını ayıklamak için Visual Studio Enterprise (profesyonel veya Community Edition değil)

## <a name="SetUpBuild"></a>1. Adım: sürüme derleme bilgilerini ekleyin
 Web projeniz için bir derleme bildirimi (*Builınfo. config* dosyası) oluşturmak üzere derleme işleminizi ayarlayın ve bu bildirimi yayınlayana dahil edin. Bu bildirim, belirli bir derlemeyi oluşturmak için kullanılan proje, kaynak denetimi ve derleme sistemi hakkında bilgiler içerir. Bu bilgiler, kaydedilen olayları gözden geçirmek için IntelliTrace günlüğünü açtıktan sonra Visual Studio ile eşleşen kaynak ve sembolleri bulmasına yardımcı olur.

### <a name="AutomatedBuild"></a>Team Foundation Server kullanarak otomatik derleme için derleme bildirimi oluşturma

 Team Foundation Sürüm Denetimi veya Git kullanarak bu adımları izleyin.

#### <a name="TFS2017"></a>Azure DevOps ve Team Foundation Server 2017

Visual Studio 2017 ve üzeri sürümler, kullanım dışı bırakılmış ve kaldırılmış olan *Builınfo. config* dosyasını içermez. Dağıtımdan sonra ASP.NET Web uygulamalarında hata ayıklamak için aşağıdaki yöntemlerden birini kullanın:

* Azure 'a dağıtım için [Application Insights](/azure/application-insights/)kullanın.

* IntelliTrace kullanmanız gerekiyorsa, projeyi Visual Studio 'da açın ve sembol dosyalarını eşleşen derlemeden yükleyin. Sembol dosyalarını **modüller** penceresinden yükleyebilir veya **Araçlar** > **seçenekler** ' de sembolleri yapılandırarak > **hata ayıklama** > **sembolleri**yapılandırabilirsiniz.

#### <a name="TFS2013"></a>Team Foundation Server 2013
 Kaynak, derleme ve sembollerinizin konumlarını derleme bildirimine (Builınfo. config dosyası) eklemek için derleme işlem hattınızı ayarlayın. Team Foundation derlemesi bu dosyayı otomatik olarak oluşturur ve projenin çıkış klasörüne koyar.

1. [Derleme işlem hattınızı düzenleyin veya yeni bir derleme işlem hattı oluşturun.](/azure/devops/pipelines/get-started-designer?view=vsts)

     ![TFS 2013 ' de derleme işlem hattını görüntüleme](../debugger/media/ffr_tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")

2. Varsayılan şablon (TfvcTemplate.12.xaml) veya kendi özel şablonunuzu seçin.

     ![Yapı işlem şablonu &#45; TFS 2013 ' i seçin](../debugger/media/ffr_tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")

3. Kaynağınızın dizine otomatik olarak dizinlenmesini sağlamak için semboller (PDB) dosyasının kaydedileceği yeri belirtin.

     Özel bir şablon kullanırsanız, şablonun kaynağınızı dizinleyecek bir aktivitesi olduğundan emin olun. Daha sonra semboller dosyalarının kaydedileceği yeri belirtmek için bir MSBuild bağımsız değişkeni ekleyeceksiniz.

     ![Derleme işlem hattı TFS 2013 ' de simge yolunu ayarlama](../debugger/media/ffr_tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")

     Semboller hakkında daha fazla bilgi için bkz. [Publish symbol Data](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols?view=vsts).

4. Bu MSBuild bağımsız değişkenini, derleme bildirim dosyasına TFS ve semboller konumlarını içerecek şekilde ekleyin:

     **/p: IncludeServerNameInBuildInfo = true**

     Web sunucunuza erişebilen herkes, derleme bildiriminde bu konumları görebilir. Kaynak sunucunuzun güvenli olduğundan emin olun.

5. Özel bir şablon kullanırsanız, bu MSBuild bağımsız değişkenini simgeler dosyasının kaydedileceği yeri belirtmek için ekleyin:

     **/p: BuildSymbolStorePath =** \<*sembollerin yolu*>

     ![Derleme def TFS 2013 derleme sunucusu bilgilerini dahil et](../debugger/media/ffr_tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")

     Ve web proje dosyanıza (.csproj, .vbproj) bu satırları ekleyin:

    ```xml
    <!-- Import the targets file. Change the folder location as necessary. -->
       <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />

    ```

     Web sunucunuza erişebilen herkes, derleme bildiriminde bu konumları görebilir. Kaynak sunucunuzun güvenli olduğundan emin olun.

6. Yeni bir yapı çalıştırın.

    [2. Adım: uygulamanızı serbest bırakma](#DeployRelease) sayfasına gidin

#### <a name="TFS2012_2010"></a>Team Foundation Server 2012 veya 2010
 Projeniz için derleme bildirimini (Builınfo. config dosyası) otomatik olarak oluşturmak ve dosyayı projenizin çıkış klasörüne koymak için aşağıdaki adımları izleyin. Dosya "*ProjectName*" olarak görünür. Builınfo. config "çıkış klasöründedir, ancak uygulamanızı yayımladıktan sonra dağıtım klasöründe" Builınfo. config "olarak yeniden adlandırılır.

1. Team Foundation Yapı sunucunuza Visual Studio 2013 (herhangi bir sürüm) yükleyin.

2. Derleme işlem hattınızda, kaynağınızın otomatik olarak dizinlenmesini sağlamak için sembollerin nereye kaydedileceğini belirtin.

     Özel bir şablon kullanırsanız, şablonun kaynağınızı dizinleyecek bir aktivitesi olduğundan emin olun.

3. Yapı ardışık düzenine bu MSBuild bağımsız değişkenlerini ekleyin:

    - **/p: VisualStudioVersion = 12.0**

    - **/p: MSBuildAssemblyVersion = 12.0**

    - **/TV: 12.0**

    - **/p: IncludeServerNameInBuildInfo = true**

    - **/p: BuildSymbolStorePath =** \<*sembollerin yolu*>

4. Yeni bir yapı çalıştırın.

    [2. Adım: uygulamanızı serbest bırakma](#DeployRelease) sayfasına gidin

### <a name="ManualBuild"></a>Visual Studio kullanarak el ile derleme için derleme bildirimi oluşturma
 Projeniz için derleme bildirimini (Builınfo. config dosyası) otomatik olarak oluşturmak ve dosyayı projenizin çıkış klasörüne koymak için aşağıdaki adımları izleyin. Dosya "*ProjectName*" olarak görünür. Builınfo. config "çıkış klasöründedir, ancak uygulamanızı yayımladıktan sonra dağıtım klasöründe" Builınfo. config "olarak yeniden adlandırılır.

1. **Çözüm Gezgini**, Web projenizi kaldırın.

2. Proje dosyasını açın (. csproj,. vbproj). Şu satırları ekleyin:

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

    [2. Adım: uygulamanızı serbest bırakma](#DeployRelease) sayfasına gidin

### <a name="MSBuild"></a>MSBuild. exe kullanarak el ile derleme için derleme bildirimi oluşturma
 Bir derlemeyi çalıştırdığınızda bu derleme bağımsız değişkenlerini ekleyin:

 **/p: GenerateBuildInfoConfigFile = doğru**

 **/p: IncludeServerNameInBuildInfo = true**

 **/p: BuildSymbolStorePath =** \<*sembollerin yolu*>

## <a name="DeployRelease"></a>2. Adım: uygulamanızı serbest bırakma
 Uygulamanızı dağıtmak için derleme işleminiz tarafından oluşturulan [Web. deploy paketini](https://msdn.microsoft.com/library/dd394698.aspx) kullanırsanız, derleme bildirimi otomatik olarak "*ProjectName*" olarak yeniden adlandırılır. Builınfo. config "," Builınfo. config "için ve Web sunucunuzdaki uygulamanızın Web. config dosyası ile aynı klasöre konur.

 Uygulamanızı dağıtmak için başka yöntemler kullanıyorsanız, Derleme bildiriminin "*ProjectName*" olarak yeniden adlandırıldığından emin olun. Builınfo. config "," Builınfo. config "için ve Web sunucusundaki uygulamanızın Web. config dosyası ile aynı klasöre konur.

## <a name="step-3-monitor-your-app"></a>Adım 3: Uygulamanızı izleyin
 Uygulamanızı sorunlar için izleyebilmeniz, Tanılama olaylarını kaydetmek ve bu olayları bir IntelliTrace günlük dosyasına kaydetmek için Web sunucunuzda uygulama performansı izleme 'yi ayarlayın. Bkz. [dağıtım sorunları için yayını izleme](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="InvestigateEvents"></a>4. Adım: sorunu bulma
 Kayıtlı olayları gözden geçirmek ve IntelliTrace kullanarak kodunuzun hatalarını ayıklamak için geliştirme bilgisayarınızda veya başka bir bilgisayarda Visual Studio Enterprise gerekir. Sorunu tanılamanıza yardımcı olması için CodeLens, hata ayıklayıcı haritaları ve kod haritaları gibi araçları da kullanabilirsiniz.

### <a name="open-the-intellitrace-log-and-matching-solution"></a>IntelliTrace günlüğünü ve eşleşen çözümü açın

1. Visual Studio Enterprise IntelliTrace günlüğünü (. iTrace dosyası) açın. Ya da aynı bilgisayarda Visual Studio Enterprise varsa dosyaya çift tıklayın.

2. Proje çözümün bir parçası olarak oluşturulmadıysa, Visual Studio 'Nun eşleşen çözümü veya projeyi otomatik olarak açması için **çözümü aç** ' ı seçin. [S: IntelliTrace günlüğünde, dağıtılan Uygulamam hakkında bilgiler eksik. Bunun nedeni neden oldu? Ne yapmalıyım?](#InvalidConfigFile)

     Visual Studio, eşleşen çözümü ya da projeyi açtığında, bekleyen tüm değişiklikleri otomatik olarak rafla. Bu raf kümesi hakkında daha fazla bilgi edinmek için **Çıkış** penceresine veya **Takım Gezgini**bakın.

     Herhangi bir değişiklik yapmadan önce doğru kaynağa sahip olduğunu doğrulayın. Dallandırma kullanıyorsanız, Visual Studio 'Nun yayın dalı gibi eşleşen kaynağı bulduğu farklı bir dalda çalışıyor olabilirsiniz.

     ![IntelliTrace günlüğünden çözüm aç](../debugger/media/ffr_itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")

     Bu çözüm veya projeyle eşlenmiş bir çalışma alanınız varsa, Visual Studio bu çalışma alanını, bulunan kaynağı yerleştirmek için seçer.

     ![Kaynak denetiminden eşlenen çalışma alanına aç](../debugger/media/ffr_openprojectfromsourcecontrol_mapped.png "FFR_OpenProjectFromSourceControl_Mapped")

     Aksi halde, zaten eşleşmiş başka bir çalışma alanı seçin veya yeni bir çalışma alanı oluşturun. Visual Studio tüm dalı bu çalışma alanına eşleyecektir.

     ![Kaynak denetiminden &#45; aç yeni çalışma alanı oluştur](../debugger/media/ffr_openprojectfromsourcecontrol_createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")

     Belirli eşlemelere veya bilgisayarınızın adı olmayan bir ada sahip bir çalışma alanı oluşturmak için **Yönet**' i seçin.

     [S: Visual Studio neden seçili çalışma alanım kullanılamıyor?](#IneligibleWorkspace)

     [S: bir takım koleksiyonu veya farklı bir koleksiyon seçinceye kadar niçin devam edemiyorum?](#ChooseTeamProject)

### <a name="diagnose-a-performance-problem"></a>Performans sorunu tanıla

1. **Performans ihlalleri**altında, kaydedilen performans olaylarını, bunların toplam yürütme sürelerini ve diğer olay bilgilerini gözden geçirin. Sonra belirli performans olayı sırasında çağrılan yöntemlerde fazla araştırma yapın.

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

1. **Özel durum verileri**altında, kaydedilen özel durum olaylarını, türleri, iletileri ve özel durumların ne zaman oluştuğunu gözden geçirin. Kodu daha ayrıntılı incelemek için özel durumlar grubu içindeki en son olaydan başlayın.

     ![Özel durum olayından hata ayıklamayı Başlat](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")

     Ayrıca, olayı çift tıklatabilirsiniz.

     Uygulama kodunuzda bir özel durum oluştuysa, Visual Studio özel durumun olduğu yere gider.

     ![Özel durum olayından uygulama koduna git](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")

     Artık kaydedilen diğer değerleri, çağrı yığınını gözden geçirebilir veya diğer kayıtlı olaylar, ilgili kod ve bu noktalarda kaydedilmiş değerler [arasında "zamanda" geriye veya ileri doğru gitmek](../debugger/intellitrace.md)için **IntelliTrace** penceresini kullanabilirsiniz.

     [IntelliTrace günlüğündeki tüm bu olaylar ve bilgiler nelerdir?](../debugger/using-saved-intellitrace-data.md)

### <a name="WhatElse"></a>Buradan başka ne yapabilirim?

- [Bu kod hakkında daha fazla bilgi alın](../ide/find-code-changes-and-other-history-with-codelens.md). Bu koda yapılan başvuruları, değişiklik geçmişini, ilgili hataları, iş öğelerini, kod incelemelerini veya birim testlerini, Düzenleyiciden çıkmadan bulmak için, düzenleyicide CodeLens göstergelerini kullanın.

     ![CodeLens &#45; görünümü bu koda başvuruyor](../debugger/media/ffr_itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")

     ![Bu kod &#45; Için CodeLens View değişiklik geçmişi](../debugger/media/ffr_itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")

- [Hata ayıklarken kodunuzda yerinizi eşleyin.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) Hata ayıklama sırasında aranan yöntemleri görsel izlemek için çağrı yığınını eşleyin.

     ![Hata ayıklarken çağrı yığınını eşleyin](../debugger/media/ffr_itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")

### <a name="FAQ"></a>soru-cevap &

#### <a name="WhyInclude"></a>S: neden projem, kaynak denetimi, derleme ve sembolle ilgili bilgileri benim yayınmla içersin?
 Visual Studio, hata ayıklamaya çalıştığınız sürümün eşleşen çözümünü ve kaynağını bulmak için bu bilgileri kullanır. IntelliTrace günlüğünü açtıktan ve hata ayıklamayı başlatacak bir olay seçtikten sonra, Visual Studio, olayın gerçekleştiği Kodu bulmak ve göstermek için sembolleri kullanır. Daha sonra, kaydedilen değerlere bakabilir ve kodunuzun yürütülmesi sırasında iletme veya geriye doğru taşıyabilirsiniz.

 TFS kullanıyorsanız ve bu bilgiler derleme bildiriminde (Builınfo. config dosyası) yoksa, Visual Studio şu anda bağlı olan TFS 'deki eşleşen kaynak ve sembolleri arar. Visual Studio doğru TFS veya eşleşen kaynağı bulamazsa, farklı bir TFS seçmeniz istenir.

#### <a name="InvalidConfigFile"></a>S: IntelliTrace günlüğünde, dağıtılan Uygulamam hakkında bilgiler eksik. Bunun nedeni neden oldu? Ne yapmam gerekir?
 Bu durum, geliştirme bilgisayarınızdan dağıtırken veya dağıtım sırasında TFS 'ye bağlı olmadığınız durumlarda gerçekleşebilir.

1. Projenizin dağıtım klasörüne gidin.

2. Yapı bildirimini bulun ve açın (Builınfo. config dosyası).

3. Dosyanın gerekli bilgileri içerdiğinden emin olun:

- **ProjectName**

   Visual Studio 'daki projenizin adı. Örneğin:

  ```xml
  <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>
  ```

- **SourceControl**

- Kaynak denetimi sisteminiz ve bu gerekli özellikler hakkında bilgi:

  - **TFS**

    - **Projectcollectionuri**: Team Foundation Server ve proje KOLEKSIYONUNUZ için URI

    - **ProjectItemSpec**: uygulamanızın proje dosyasının yolu (. csproj veya. vbproj)

    - **ProjectVersionSpec**: projenizin sürümü

      Örneğin:

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

    - **Havuz URL 'si**: Team Foundation Server, proje koleksiyonunuz ve git deponuzun URI 'si

    - **ProjectPath**: uygulamanızın proje dosyasının yolu (. csproj veya. vbproj)

    - **CommitId**: yürütmeniz için kimlik

      Örneğin:

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

   `"TeamBuild"` ya da `"MSBuild"`ve bu gerekli özellikler ile derleme sisteminiz hakkında bilgi:

  - **BuildLabel** (TeamBuild için): derleme adı ve numarası. Bu etiket, dağıtım olayının adı olarak da kullanılır. Derleme numaraları hakkında daha fazla bilgi için bkz. [Tamamlanan yapılara anlamlı adlar sağlamak için yapı numaralarını kullanma](/azure/devops/pipelines/build/options?view=vsts).

  - **SymbolPath** (önerilen): SIMGELER (pdb dosyası) konumlarına yönelik URI 'lerin noktalı virgülle ayrılmış listesi. Bu URI 'Ler URL veya UNCs olabilir. Bu, Visual Studio 'Nun hata ayıklamada size yardımcı olacak eşleşen sembolleri bulmasını kolaylaştırır.

  - **BuildReportUrl** (TeamBuild için): TFS 'de yapı raporunun konumu

  - **BuildId** (TeamBuild için): TFS 'deki derleme ayrıntıları için URI. Bu URI, dağıtım olayının KIMLIĞI olarak da kullanılır. TeamBuild kullanmıyorsanız bu KIMLIK benzersiz olmalıdır.

  - **BuiltSolution**: Visual Studio 'nun eşleşen çözümü bulmak ve açmak için kullandığı çözüm dosyasının yolu. Bu, **SolutionPath** MSBuild özelliğinin içeriğidir.

    Örneğin:

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

#### <a name="IneligibleWorkspace"></a>S: Visual Studio neden seçili çalışma alanım kullanılamıyor?
 Y **:** Seçilen çalışma alanı, kaynak denetim klasörü ve yerel klasör arasında herhangi bir eşlemeye sahip değil. Bu çalışma alanı için bir eşleme oluşturmak için **Yönet**' i seçin. Aksi halde, zaten eşleşmiş bir çalışma alanı seçin veya yeni bir çalışma alanı oluşturun.

 ![Eşlenmiş çalışma alanı olmadan kaynak denetiminden Aç](../debugger/media/ffr_openprojectfromsourcecontrol_notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")

#### <a name="ChooseTeamProject"></a>S: bir takım koleksiyonu veya farklı bir koleksiyon seçinceye kadar niçin devam edemiyorum?
 Y **:** Bunun nedeni şu nedenlerden herhangi biri olabilir:

- Visual Studio TFS'ye bağlı değildir.

     ![Kaynak denetiminden &#45; aç bağlı değil](../debugger/media/ffr_openprojectfromsourcecontrol_notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")

- Visual Studio geçerli takım koleksiyonunuzda çözüm ya da proje bulamadı.

     Yapı bildirim dosyası (\<*ProjectName*>. Builınfo. config), Visual Studio 'Nun eşleşen kaynağı bulabileceği konumu belirtmez, Visual Studio eşleşen çözümü veya projeyi bulmak için şu anda bağlı olan TFS 'nizi kullanır. Geçerli takım koleksiyonunuzda eşleşen kaynak yoksa, Visual Studio farklı takım koleksiyonuna bağlanmanızı ister.

- Visual Studio, derleme bildirim dosyası (\<*ProjectName*> tarafından belirtilen koleksiyonda çözüm veya proje bulamadı. Builınfo. config).

     Belirtilen TFS artık eşleşen kaynağa sahip olmayabilir, hatta yeni bir TFS'ye geçtiğiniz için hiç varolmayabilir. Belirtilen TFS mevcut değilse Visual Studio bir dakika ya da sonrasında zaman aşımına uğrayabilir ve bu durumda sizden farklı bir koleksiyona bağlanmanız istenebilir. Devam etmek için doğru TFS sunucusuna bağlanın.

     ![Geçirilen kaynak denetiminden &#45; aç](../debugger/media/ffr_openprojectfromsourcecontrol_migrated.png "FFR_OpenProjectFromSourceControl_Migrated")

#### <a name="WhatWorkspace"></a>S: çalışma alanı nedir?
 Y **:** [Çalışma alanınız kaynağın bir kopyasını depolar](/azure/devops/repos/tfvc/create-work-workspaces?view=vsts) , böylece çalışmalarınızı iade etmeden önce bunları ayrı ayrı geliştirebilir ve test edebilirsiniz. Bulunan çözümle veya projeyle özel olarak eşleşen bir çalışma alanı yoksa, Visual Studio varsayılan çalışma alanı adı olarak bilgisayar adınızla birlikte yeni bir çalışma alanı oluşturmanızı veya mevcut bir çalışma alanı seçmenizi ister.

#### <a name="UntrustedSymbols"></a>S: güvenilmeyen simgeler hakkında bu iletiyi neden alıyorum?
 ![Güvenilmeyen semboller yoluyla hata ayıklaması yapılsın mı?](../debugger/media/ffr_ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")

 Y **:** Bu ileti, derleme bildirim dosyasındaki (\<*ProjectName*> semboller yolu olduğunda görüntülenir. Builınfo. config) güvenilen sembol yolları listesine dahil değildir. Hata ayıklama seçeneklerindeki sembol yolu listesine yolu ekleyebilirsiniz.
