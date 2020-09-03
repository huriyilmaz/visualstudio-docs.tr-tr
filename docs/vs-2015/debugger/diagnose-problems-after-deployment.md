---
title: Dağıtımdan sonra sorunları tanılama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
caps.latest.revision: 66
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 41b24cf97ef0768ee700841aa859698cd2307710
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74298296"
---
# <a name="diagnose-problems-after-deployment"></a>Dağıtımdan sonra sorunları tanılama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliTrace kullanarak dağıtımdan sonra ASP.NET Web uygulamanızdaki sorunları tanılamak için, Visual Studio 'Nun IntelliTrace günlüğünde hata ayıklamak için gerekli olan doğru kaynak dosyaları ve sembol dosyalarını otomatik olarak bulmasını sağlamak üzere yayınınızdan derleme bilgilerini ekleyin.  
  
 IntelliTrace 'i denetlemek için Microsoft Monitoring Agent kullanıyorsanız, Web sunucunuzda uygulama performansı izlemeyi ayarlamayı da ayarlamanız gerekir. Bu, uygulamanız çalışırken Tanılama olaylarını kaydeder ve olayları bir IntelliTrace günlük dosyasına kaydeder. Daha sonra Visual Studio Enterprise (Professional veya Community Edition değil) içindeki olaylara bakabilir, bir olayın gerçekleştiği koda gidebilir, o zaman içindeki kayıtlı değerlere bakabilirsiniz ve iletilen kodu kullanarak iletme veya geriye doğru taşıyabilirsiniz. Sorunu bulduktan ve düzelttikten sonra, daha önce ve daha hızlı olabilecek olası sorunları çözebilmek için sürümünüzü oluşturma, yayınlama ve izleme döngüsünü yineleyin.  
  
 ![Kod, derleme, yayınlama, izleme, tanılama, onarma](../debugger/media/ffr-cycle.png "FFR_Cycle")  
  
 **Şunlara ihtiyacınız var:**  
  
- Derlemenizi ayarlamak için Visual Studio 2015 veya Team Foundation Server 2015, 2013, 2012 veya 2010  
  
- Uygulamanızı izlemek ve tanılama verilerini kaydetmek için Microsoft Monitoring Agent  
  
- Tanılama verilerini gözden geçirmek ve IntelliTrace ile kodunuzun hatalarını ayıklamak için Visual Studio Enterprise (profesyonel veya Community Edition değil)  
  
## <a name="step-1-include-build-information-with-your-release"></a><a name="SetUpBuild"></a> 1. Adım: sürüme derleme bilgilerini ekleyin  
 Web projeniz için bir yapı bildirimi (BuildInfo.config dosyası) oluşturmak üzere derleme işleminizi ayarlayın ve bu bildirimi yayınlayana ekleyin. Bu bildirim, belirli bir derlemeyi oluşturmak için kullanılan proje, kaynak denetimi ve derleme sistemi hakkında bilgiler içerir. Bu bilgiler, kaydedilen olayları gözden geçirmek için IntelliTrace günlüğünü açtıktan sonra Visual Studio ile eşleşen kaynak ve sembolleri bulmasına yardımcı olur.  
  
### <a name="create-the-build-manifest-for-an-automated-build-using-team-foundation-server"></a><a name="AutomatedBuild"></a> Team Foundation Server kullanarak otomatik derleme için derleme bildirimi oluşturma  
 Team Foundation Sürüm Denetimi veya Git kullanarak bu adımları izleyin.  
  
#### <a name="team-foundation-server-2013"></a><a name="TFS2013"></a> Team Foundation Server 2013  
 Derleme bildirimine kaynak, derleme ve sembollerinizin konumlarını eklemek için derleme tanımınızı ayarlayın (BuildInfo.config dosyası). Team Foundation derlemesi bu dosyayı otomatik olarak oluşturur ve projenin çıkış klasörüne koyar.  
  
1. [Derleme tanımınızı düzenleyin veya yeni bir derleme tanımı oluşturun.](https://msdn.microsoft.com/library/1c2eca2d-9a65-477e-9b23-0678ff7882ee)  
  
    ![TFS 2013 ' de derleme tanımını görüntüleme](../debugger/media/ffr-tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")  
  
2. Varsayılan şablon (TfvcTemplate.12.xaml) veya kendi özel şablonunuzu seçin.  
  
    ![TFS 2013 &#45; yapı işlem şablonu seçin](../debugger/media/ffr-tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")  
  
3. Kaynağınızın dizine otomatik olarak dizinlenmesini sağlamak için semboller (PDB) dosyasının kaydedileceği yeri belirtin.  
  
    Özel bir şablon kullanırsanız, şablonun kaynağınızı dizinleyecek bir aktivitesi olduğundan emin olun. Daha sonra semboller dosyalarının kaydedileceği yeri belirtmek için bir MSBuild bağımsız değişkeni ekleyeceksiniz.  
  
    ![Derleme tanımı TFS 2013 ' de simge yolunu ayarlama](../debugger/media/ffr-tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")  
  
    Semboller hakkında daha fazla bilgi için bkz. [Publish symbol Data](https://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6).  
  
4. Bu MSBuild bağımsız değişkenini, derleme bildirim dosyasına TFS ve semboller konumlarını içerecek şekilde ekleyin:  
  
    **/p: IncludeServerNameInBuildInfo = true**  
  
    Web sunucunuza erişebilen herkes, derleme bildiriminde bu konumları görebilir. Kaynak sunucunuzun güvenli olduğundan emin olun.  
  
5. Özel bir şablon kullanırsanız, bu MSBuild bağımsız değişkenini simgeler dosyasının kaydedileceği yeri belirtmek için ekleyin:  
  
    **/p: BuildSymbolStorePath =**\<*path to symbols*>  
  
    ![Derleme def TFS 2013 derleme sunucusu bilgilerini dahil et](../debugger/media/ffr-tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")  
  
    Ve web proje dosyanıza (.csproj, .vbproj) bu satırları ekleyin:  
  
   ```  
   <!-- Import the targets file. Change the folder location as necessary. -->  
      <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />  
  
   ```  
  
6. Yeni bir yapı çalıştırın.  
  
   **2. adım** : [Adım 2: uygulamanızı serbest bırakma](#DeployRelease)  
  
#### <a name="team-foundation-server-2012-or-2010"></a><a name="TFS2012_2010"></a> Team Foundation Server 2012 veya 2010  
 Projeniz için derleme bildirimini (BuildInfo.config dosyası) otomatik olarak oluşturmak ve dosyayı projenizin çıkış klasörüne koymak için aşağıdaki adımları izleyin. Dosya, çıkış klasöründe "*ProjectName*.BuildInfo.config" olarak görünür, ancak uygulamanızı yayımladıktan sonra dağıtım klasöründe "BuildInfo.config" olarak yeniden adlandırılır.  
  
1. Team Foundation Yapı sunucunuza Visual Studio 2013 (herhangi bir sürüm) yükleyin.  
  
2. Yapı tanımınızda, kaynağı otomatik olarak endeksleyen simgelerin kaydedileceği konumu belirtin.  
  
    Özel bir şablon kullanırsanız, şablonun kaynağınızı dizinleyecek bir aktivitesi olduğundan emin olun.  
  
3. Yapı tanımınıza bu MSBuild bağımsız değişkenlerini ekleyin:  
  
   - **/p: VisualStudioVersion = 12.0**  
  
   - **/p: MSBuildAssemblyVersion = 12.0**  
  
   - **/TV: 12.0**  
  
   - **/p: IncludeServerNameInBuildInfo = true**  
  
   - **/p: BuildSymbolStorePath =**\<*path to symbols*>  
  
4. Yeni bir yapı çalıştırın.  
  
   **2. adım** : [Adım 2: uygulamanızı serbest bırakma](#DeployRelease)  
  
### <a name="create-the-build-manifest-for-a-manual-build-using-visual-studio"></a><a name="ManualBuild"></a> Visual Studio kullanarak el ile derleme için derleme bildirimi oluşturma  
 Projeniz için derleme bildirimini (BuildInfo.config dosyası) otomatik olarak oluşturmak ve dosyayı projenizin çıkış klasörüne koymak için aşağıdaki adımları izleyin. Dosya, çıkış klasöründe "*ProjectName*.BuildInfo.config" olarak görünür, ancak uygulamanızı yayımladıktan sonra dağıtım klasöründe "BuildInfo.config" olarak yeniden adlandırılır.  
  
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
  
   **2. adım** : [Adım 2: uygulamanızı serbest bırakma](#DeployRelease)  
  
### <a name="create-the-build-manifest-for-a-manual-build-using-msbuildexe"></a><a name="MSBuild"></a> MSBuild.exe kullanarak el ile derleme için derleme bildirimi oluşturma  
 Bir derlemeyi çalıştırdığınızda bu derleme bağımsız değişkenlerini ekleyin:  
  
 **/p: GenerateBuildInfoConfigFile = doğru**  
  
 **/p: IncludeServerNameInBuildInfo = true**  
  
 **/p: BuildSymbolStorePath =**\<*path to symbols*>  
  
## <a name="step-2-release-your-app"></a><a name="DeployRelease"></a> 2. Adım: uygulamanızı serbest bırakma  
 Uygulamanızı dağıtmak için derleme işleminiz tarafından oluşturulan [Web. deploy paketini](https://msdn.microsoft.com/library/dd394698.aspx) kullanırsanız, derleme bildirimi otomatik olarak "*ProjectName*.BuildInfo.config" iken "BuildInfo.config" olarak yeniden adlandırılır ve Web sunucunuzdaki uygulamanızın Web.config dosyası ile aynı klasöre konur.  
  
 Uygulamanızı dağıtmak için başka yöntemler kullanıyorsanız, Derleme bildiriminin "*ProjectName*.BuildInfo.config" iken "BuildInfo.config" olarak yeniden adlandırıldığından ve Web sunucusundaki uygulamanızın Web.config dosyası ile aynı klasöre yerleştirdiğinizden emin olun.  
  
## <a name="step-3-monitor-your-app"></a>Adım 3: Uygulamanızı izleyin  
 Uygulamanızı sorunlar için izleyebilmeniz, Tanılama olaylarını kaydetmek ve bu olayları bir IntelliTrace günlük dosyasına kaydetmek için Web sunucunuzda uygulama performansı izleme 'yi ayarlayın. Bkz. [dağıtım sorunları için yayını izleme](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## <a name="step-4-find-the-problem"></a><a name="InvestigateEvents"></a> 4. Adım: sorunu bulma  
 Kayıtlı olayları gözden geçirmek ve IntelliTrace kullanarak kodunuzun hatalarını ayıklamak için geliştirme bilgisayarınızda veya başka bir bilgisayarda Visual Studio Enterprise gerekir. Sorunu tanılamanıza yardımcı olması için CodeLens, hata ayıklayıcı haritaları ve kod haritaları gibi araçları da kullanabilirsiniz.  
  
### <a name="open-the-intellitrace-log-and-matching-solution"></a>IntelliTrace günlüğünü ve eşleşen çözümü açın  
  
1. Visual Studio Enterprise IntelliTrace günlüğünü (. iTrace dosyası) açın. Ya da aynı bilgisayarda Visual Studio Enterprise varsa dosyaya çift tıklayın.  
  
2. Proje çözümün bir parçası olarak oluşturulmadıysa, Visual Studio 'Nun eşleşen çözümü veya projeyi otomatik olarak açması için **çözümü aç** ' ı seçin. [S: IntelliTrace günlüğünde, dağıtılan Uygulamam hakkında bilgiler eksik. Bunun nedeni neden oldu? Ne yapmalıyım?](#InvalidConfigFile)  
  
     Visual Studio, eşleşen çözümü ya da projeyi açtığında, bekleyen tüm değişiklikleri otomatik olarak rafla. Bu raf kümesi hakkında daha fazla bilgi edinmek için **Çıkış** penceresine veya **Takım Gezgini**bakın.  
  
     Herhangi bir değişiklik yapmadan önce doğru kaynağa sahip olduğunu doğrulayın. Dallandırma kullanıyorsanız, Visual Studio 'Nun yayın dalı gibi eşleşen kaynağı bulduğu farklı bir dalda çalışıyor olabilirsiniz.  
  
     ![IntelliTrace günlüğünden çözüm aç](../debugger/media/ffr-itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")  
  
     Bu çözüm veya projeyle eşlenmiş bir çalışma alanınız varsa, Visual Studio bu çalışma alanını, bulunan kaynağı yerleştirmek için seçer.  
  
     ![Kaynak denetiminden eşlenen çalışma alanına aç](../debugger/media/ffr-openprojectfromsourcecontrol-mapped.png "FFR_OpenProjectFromSourceControl_Mapped")  
  
     Aksi halde, zaten eşleşmiş başka bir çalışma alanı seçin veya yeni bir çalışma alanı oluşturun. Visual Studio tüm dalı bu çalışma alanına eşleyecektir.  
  
     ![Kaynak denetiminden Aç &#45; yeni çalışma alanı oluştur](../debugger/media/ffr-openprojectfromsourcecontrol-createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")  
  
     Belirli eşlemelere veya bilgisayarınızın adı olmayan bir ada sahip bir çalışma alanı oluşturmak için **Yönet**' i seçin.  
  
     [S: Visual Studio neden seçili çalışma alanım kullanılamıyor?](#IneligibleWorkspace)  
  
     [S: bir takım koleksiyonu veya farklı bir koleksiyon seçinceye kadar niçin devam edemiyorum?](#ChooseTeamProject)  
  
### <a name="diagnose-a-performance-problem"></a>Performans sorunu tanıla  
  
1. **Performans ihlalleri**altında, kaydedilen performans olaylarını, bunların toplam yürütme sürelerini ve diğer olay bilgilerini gözden geçirin. Sonra belirli performans olayı sırasında çağrılan yöntemlerde fazla araştırma yapın.  
  
     ![Performans olayı ayrıntılarını görüntüleme](../debugger/media/ffr-itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     Ayrıca, olayı çift tıklatabilirsiniz.  
  
2. Olay sayfasında, bu çağrılar için yürütme zamanını gözden geçirin. Yürütme ağacında yavaş bir çağrı bulun.  
  
     İç içe ya da başka şekilde birden fazla çağrınız varsa, en yavaş çağrılar kendi bölümünde görüntülenir.  
  
     Yuvalanmış çağrıları ve zamanın o anında kaydedilmiş değerleri gözden geçirmek için o çağrıyı genişletin. Sonra o çağrıdan hata ayıklamayı başlatın.  
  
     ![Yöntem çağrısından hata ayıklamayı Başlat](../debugger/media/ffr-itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     Ayrıca, aramayı çift tıklatabilirsiniz.  
  
     Yöntem uygulama kodunuzda ise, Visual Studio bu yönteme gider.  
  
     ![Performans olayından uygulama koduna git](../debugger/media/ffr-itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     Artık kaydedilen diğer değerleri, çağrı yığınını gözden geçirebilir, kodunuzda adım adım ilerlerseniz veya bu performans olayı sırasında çağrılan [diğer yöntemler arasında "zamanda" geriye veya ileri doğru gitmek](../debugger/intellitrace.md) için **IntelliTrace** penceresini kullanabilirsiniz. [IntelliTrace günlüğündeki tüm bu olaylar ve bilgiler nelerdir?](../debugger/using-saved-intellitrace-data.md) [Buradan başka ne yapabilirim?](#WhatElse) [Performans olayları hakkında daha fazla bilgi mi istiyorsunuz?](https://devblogs.microsoft.com/devops/performance-details-in-intellitrace/)  
  
### <a name="diagnose-an-exception"></a>Bir özel durumu tanıla  
  
1. **Özel durum verileri**altında, kaydedilen özel durum olaylarını, türleri, iletileri ve özel durumların ne zaman oluştuğunu gözden geçirin. Kodu daha ayrıntılı incelemek için özel durumlar grubu içindeki en son olaydan başlayın.  
  
     ![Özel durum olayından hata ayıklamayı Başlat](../debugger/media/ffr-itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     Ayrıca, olayı çift tıklatabilirsiniz.  
  
     Uygulama kodunuzda bir özel durum oluştuysa, Visual Studio özel durumun olduğu yere gider.  
  
     ![Özel durum olayından uygulama koduna git](../debugger/media/ffr-itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     Artık kaydedilen diğer değerleri, çağrı yığınını gözden geçirebilir veya diğer kayıtlı olaylar, ilgili kod ve bu noktalarda kaydedilmiş değerler [arasında "zamanda" geriye veya ileri doğru gitmek](../debugger/intellitrace.md)için **IntelliTrace** penceresini kullanabilirsiniz. [IntelliTrace günlüğündeki tüm bu olaylar ve bilgiler nelerdir?](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="what-else-can-i-do-from-here"></a><a name="WhatElse"></a> Buradan başka ne yapabilirim?  
  
- [Bu kod hakkında daha fazla bilgi alın](../ide/find-code-changes-and-other-history-with-codelens.md). Bu koda yapılan başvuruları, değişiklik geçmişini, ilgili hataları, iş öğelerini, kod incelemelerini veya birim testlerini, Düzenleyiciden çıkmadan bulmak için düzenleyicide CodeLens göstergelerini kullanın.  
  
     ![CodeLens &#45; bu koda yönelik başvuruları görüntüle](../debugger/media/ffr-itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")  
  
     ![CodeLens &#45; bu kodun değişiklik geçmişini görüntüle](../debugger/media/ffr-itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")  
  
- [Hata ayıklarken kodunuzda yerinizi eşleyin.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) Hata ayıklama sırasında aranan yöntemleri görsel izlemek için çağrı yığınını eşleyin.  
  
     ![Hata ayıklarken çağrı yığınını eşleyin](../debugger/media/ffr-itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")  
  
### <a name="q--a"></a><a name="FAQ"></a> SORU-CEVAP &  
  
#### <a name="q-why-include-information-about-my-project-source-control-build-and-symbols-with-my-release"></a><a name="WhyInclude"></a> S: neden projem, kaynak denetimi, derleme ve sembolle ilgili bilgileri benim yayınmla içersin?  
 Visual Studio, hata ayıklamaya çalıştığınız sürümün eşleşen çözümünü ve kaynağını bulmak için bu bilgileri kullanır. IntelliTrace günlüğünü açtıktan ve hata ayıklamayı başlatacak bir olay seçtikten sonra, Visual Studio, olayın gerçekleştiği Kodu bulmak ve göstermek için sembolleri kullanır. Daha sonra, kaydedilen değerlere bakabilir ve kodunuzun yürütülmesi sırasında iletme veya geriye doğru taşıyabilirsiniz.  
  
 TFS kullanıyorsanız ve bu bilgiler derleme manfıest (BuildInfo.config dosyasında) değilse, Visual Studio şu anda bağlı olan TFS 'deki eşleşen kaynak ve sembolleri arar. Visual Studio doğru TFS veya eşleşen kaynağı bulamazsa, farklı bir TFS seçmeniz istenir.  
  
#### <a name="q-the-intellitrace-log-is-missing-information-about-my-deployed-app-why-did-this-happen-what-do-i-do"></a><a name="InvalidConfigFile"></a> S: IntelliTrace günlüğünde, dağıtılan Uygulamam hakkında bilgiler eksik. Bunun nedeni neden oldu? Ne yapmalıyım?  
 Bu durum, geliştirme bilgisayarınızdan dağıtırken veya dağıtım sırasında TFS 'ye bağlı olmadığınız durumlarda gerçekleşebilir.  
  
1. Projenizin dağıtım klasörüne gidin.  
  
2. Derleme bildirimini bulun ve açın (BuildInfo.config dosyası).  
  
3. Dosyanın gerekli bilgileri içerdiğinden emin olun:  
  
- **ProjectName**  
  
   Visual Studio 'daki projenizin adı. Örneğin:  
  
  ```  
  <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>  
  ```  
  
- **SourceControl**  
  
- Kaynak denetimi sisteminiz ve bu gerekli özellikler hakkında bilgi:  
  
  - **TFS**  
  
    - **Projectcollectionuri**: Team Foundation Server ve proje KOLEKSIYONUNUZ için URI  
  
    - **ProjectItemSpec**: uygulamanızın proje dosyasının yolu (. csproj veya. vbproj)  
  
    - **ProjectVersionSpec**: projenizin sürümü  
  
      Örneğin:  
  
    ```  
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
  
    ```  
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
  
  - **BuildLabel** (TeamBuild için): derleme adı ve numarası. Bu etiket, dağıtım olayının adı olarak da kullanılır. Derleme numaraları hakkında daha fazla bilgi için bkz. [Tamamlanan yapılara anlamlı adlar sağlamak için yapı numaralarını kullanma](https://msdn.microsoft.com/library/1f302e9d-4b0a-40b5-8009-b69ca6f988c3).  
  
  - **SymbolPath** (önerilen): SIMGELER (pdb dosyası) konumlarına yönelik URI 'lerin noktalı virgülle ayrılmış listesi. Bu URI 'Ler URL veya UNCs olabilir. Bu, Visual Studio 'Nun hata ayıklamada size yardımcı olacak eşleşen sembolleri bulmasını kolaylaştırır.  
  
  - **BuildReportUrl** (TeamBuild için): TFS 'de yapı raporunun konumu  
  
  - **BuildId** (TeamBuild için): TFS 'deki derleme ayrıntıları için URI. Bu URI, dağıtım olayının KIMLIĞI olarak da kullanılır. TeamBuild kullanmıyorsanız, bu kimliğin benzersiz olması gerekir.  
  
  - **BuiltSolution**: Visual Studio 'nun eşleşen çözümü bulmak ve açmak için kullandığı çözüm dosyasının yolu. Bu, **SolutionPath** MSBuild özelliğinin içeriğidir.  
  
    Örneğin:  
  
  - **TFS**  
  
    ```  
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
  
    ```  
    <Build type="MSBuild">   
       <MSBuild>  
          <SymbolPath>\\gittf\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuiltSolution>/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MSBuild>  
    </Build>  
    ```  
  
#### <a name="q-why-does-visual-studio-say-my-selected-workspace-is-ineligible"></a><a name="IneligibleWorkspace"></a> S: Visual Studio neden seçili çalışma alanım kullanılamıyor?  
 Y **:** Seçilen çalışma alanı, kaynak denetim klasörü ve yerel klasör arasında herhangi bir eşlemeye sahip değil. Bu çalışma alanı için bir eşleme oluşturmak için **Yönet**' i seçin. Aksi halde, zaten eşleşmiş bir çalışma alanı seçin veya yeni bir çalışma alanı oluşturun.  
  
 ![Eşlenmiş çalışma alanı olmadan kaynak denetiminden Aç](../debugger/media/ffr-openprojectfromsourcecontrol-notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")  
  
#### <a name="q-why-cant-i-continue-until-i-choose-a-team-collection-or-a-different-collection"></a><a name="ChooseTeamProject"></a> S: bir takım koleksiyonu veya farklı bir koleksiyon seçinceye kadar niçin devam edemiyorum?  
 Y **:** Bunun nedeni şu nedenlerden herhangi biri olabilir:  
  
- Visual Studio TFS'ye bağlı değildir.  
  
     ![&#45; bağlı değil kaynak denetiminden Aç](../debugger/media/ffr-openprojectfromsourcecontrol-notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")  
  
- Visual Studio geçerli takım koleksiyonunuzda çözüm ya da proje bulamadı.  
  
     Yapı bildirim dosyası ( \<*ProjectName*>.BuildInfo.config) Visual Studio 'nun eşleşen kaynağı bulabileceği yeri belirtmezse, Visual Studio eşleşen çözümü veya projeyi bulmak için şu anda bağlı olan TFS 'nizi kullanır. Geçerli takım koleksiyonunuzda eşleşen kaynak yoksa, Visual Studio farklı takım koleksiyonuna bağlanmanızı ister.  
  
- Visual Studio derleme bildirim dosyası (.BuildInfo.config) tarafından belirtilen koleksiyonda çözüm ya da proje bulamadı \<*ProjectName*> .  
  
     Belirtilen TFS artık eşleşen kaynağa sahip olmayabilir, hatta yeni bir TFS'ye geçtiğiniz için hiç varolmayabilir. Belirtilen TFS mevcut değilse Visual Studio bir dakika ya da sonrasında zaman aşımına uğrayabilir ve bu durumda sizden farklı bir koleksiyona bağlanmanız istenebilir. Devam etmek için doğru TFS sunucusuna bağlanın.  
  
     ![Geçirilen &#45; kaynak denetiminden Aç](../debugger/media/ffr-openprojectfromsourcecontrol-migrated.png "FFR_OpenProjectFromSourceControl_Migrated")  
  
#### <a name="q-whats-a-workspace"></a><a name="WhatWorkspace"></a> S: çalışma alanı nedir?  
 Y **:** [Çalışma alanınız kaynağın bir kopyasını depolar](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a) , böylece çalışmalarınızı iade etmeden önce bunları ayrı ayrı geliştirebilir ve test edebilirsiniz. Bulunan çözümle veya projeyle özel olarak eşleşen bir çalışma alanı yoksa, Visual Studio varsayılan çalışma alanı adı olarak bilgisayar adınızla birlikte yeni bir çalışma alanı oluşturmanızı veya mevcut bir çalışma alanı seçmenizi ister.  
  
#### <a name="q-why-do-i-get-this-message-about-untrusted-symbols"></a><a name="UntrustedSymbols"></a> S: güvenilmeyen simgeler hakkında bu iletiyi neden alıyorum?  
 ![Güvenilmeyen semboller yoluyla hata ayıklaması yapılsın mı?](../debugger/media/ffr-ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")  
  
 Y **:** Bu ileti, derleme bildirimi dosyasındaki ( \<*ProjectName*>.BuildInfo.config) semboller yolu güvenilir sembol yolları listesine dahil edilmediğinde görüntülenir. Hata ayıklama seçeneklerindeki sembol yolu listesine yolu ekleyebilirsiniz.
