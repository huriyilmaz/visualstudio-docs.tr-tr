---
title: Özel projeleri yükseltme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: c91013e7d5650e82fd9e5f6e39e28c4609e4fbfe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82037213"
---
# <a name="upgrading-custom-projects"></a>Özel projeleri yükseltme
Proje dosyasında kalıcı olan bilgileri ürününüzün farklı Visual Studio sürümleri arasında değiştirirseniz, proje dosyanızı eski sürümden yeni sürüme yükseltmeyi desteklemeniz gerekir. **Visual Studio dönüştürme sihirbazına**katılımını sağlayan yükseltmeyi desteklemek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimini uygulayın. Bu arabirim, kopyalama yükseltme için kullanılabilen tek mekanizmayı içerir. Projenin yükseltilmesi, çözümün bir parçası olarak gerçekleşir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>Arabirim, proje fabrikası tarafından uygulanır veya en azından proje fabrikasında bilgiler kişilerden olmalıdır.  
  
 Arabirimi kullanan eski mekanizma <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> hala desteklenmektedir, ancak kavramsal olarak proje sistemini projenin bir parçası olarak yükseltir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>Bu nedenle arabirim, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirim çağrılıp uygulansa bile ortam tarafından çağırılır. Bu yaklaşım <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , yalnızca yükseltmenin ve projenin yalnızca bir kısmını kopyalamak için ' i kullanmanıza olanak sağlar ve bu işlemi, arabirime göre (muhtemelen yeni konumda) yapılacak işin geri kalanını devredebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .  
  
 Örnek bir uygulama için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> bkz. [VSSDK örnekleri](../misc/vssdk-samples.md).  
  
 Aşağıdaki senaryolar proje yükseltmeleri ile ortaya çıkar:  
  
- Dosya projenin destekleyebileceğinden daha yeni bir biçimde ise, bunu belirten bir hata döndürmelidir. Bu, ürününüzün eski sürümünün — Örneğin, Visual Studio .NET 2003 — sürümü denetlenecek kodu içerdiğini varsayar.  
  
- Bu <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> yöntemde bayrak belirtilmişse <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> , yükseltme, proje açılmadan önce yerinde bir yükseltme olarak uygulanır.  
  
- Bu <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> yöntemde bayrak belirtilmişse <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> , yükseltme bir kopya yükseltme olarak uygulanır.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>Çağrıda bayrak belirtilmişse <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> , proje açıldıktan sonra, Kullanıcı ortam tarafından proje dosyasını yerinde yükseltme olarak yükseltmek için bir kullanıcı tarafından istenir. Örneğin, ortam, Kullanıcı çözümün eski bir sürümünü açtığında kullanıcıdan yükseltme yapmanızı ister.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>Çağrıda bayrak belirtilmemişse <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> , kullanıcıdan proje dosyasını yükseltmesini istemelidir.  
  
     Aşağıda örnek bir yükseltme istemi iletisi verilmiştir:  
  
     "' %1 ' projesi, Visual Studio 'nun daha eski bir sürümüyle oluşturulmuş. Visual Studio 'nun bu sürümüyle açarsanız, Visual Studio 'nun eski sürümleriyle açamazsınız. Devam etmek ve bu projeyi açmak istiyor musunuz? "  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory uygulamak için  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>Arabirim yöntemini, özellikle de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> proje fabrikası uygulamanızdaki yöntemi uygulayın veya uygulamaları proje fabrikası uygulamanızdan çağrılabilir hale getirin.  
  
2. Çözümün açılması kapsamında bir yerinde yükseltme yapmak istiyorsanız, bayrağını <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> `VSPUVF_FLAGS` uygulamanızda parametre olarak belirtin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> .  
  
3. Çözümün açılması kapsamında bir yerinde yükseltme yapmak istiyorsanız, bayrağını <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> `VSPUVF_FLAGS` uygulamanızda parametre olarak belirtin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> .  
  
4. 2 ve 3. adımlarda, kullanarak gerçek dosya yükseltme adımları <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> aşağıdaki "uygulama" bölümünde açıklandığı gibi uygulanabilir `IVsProjectUpgade` veya gerçek dosya yükseltmeyi sürümüne atayabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .  
  
5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>Visual Studio Geçiş Sihirbazı 'nı kullanarak Kullanıcı için yükseltme ile ilgili iletileri gönderme yöntemlerini kullanın.  
  
6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> arabirim, proje yükseltmesinin bir parçası olarak gerçekleşmesi gereken herhangi bir tür dosya yükseltmesini uygulamak için kullanılır. Bu arabirim öğesinden çağrılmaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , ancak proje sisteminin bir parçası olan dosyaları yükseltmek için bir mekanizma olarak sağlanır, ancak ana proje sistemi doğrudan farkında olmayabilir. Örneğin, derleyici ile ilgili dosyalar ve özellikler proje sisteminin geri kalanını işleyen geliştirme ekibi tarafından işlenmezse bu durum ortaya çıkabilir.  
  
## <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade uygulaması  
 Proje sisteminiz yalnızca uygularsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , **Visual Studio dönüştürme sihirbazına**katılamaz. Ancak, arabirimini uygulasanız bile <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , uygulamaya dosya yükseltmeyi de atayabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .  
  
#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade 'i uygulamak için  
  
1. Bir Kullanıcı bir projeyi açmayı denediğinde, proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> açıldıktan sonra ve proje üzerinde diğer herhangi bir kullanıcı eylemi alınmadan önce, yöntemi ortam tarafından çağrılır. Kullanıcının çözümü yükseltmesi zaten istenirse, <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> bayrak `grfUpgradeFlags` parametreye geçirilir. Kullanıcı bir projeyi doğrudan açarsa (örneğin, **var olan proje Ekle** komutunu kullanarak), <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> bayrak geçirilir ve projenin kullanıcıdan yükseltmesini istemek gerekir.  
  
2. Çağrıya yanıt olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Proje, proje dosyasının yükseltilip yükseltilmediğini değerlendirmelidir. Projenin proje türünü yeni bir sürüme yükseltmesi gerekmiyorsa, yalnızca <xref:Microsoft.VisualStudio.VSConstants.S_OK> bayrağı döndürebilir.  
  
3. Projenin proje türünü yeni bir sürüme yükseltmesi gerekiyorsa, bu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> yöntemi çağırarak ve parametresi için değerini geçirerek proje dosyasının değiştirilip değiştirilemeyeceğini belirlemelidir <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` . Ardından projenin aşağıdakileri yapması gerekir:  
  
   - `VSQueryEditResult`Parametresinde döndürülen değer `pfEditCanceled` ise <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> , proje dosyası yazılabildiğinden yükseltme devam edebilir.  
  
   - `VSQueryEditResult`Parametresinde döndürülen değer `pfEditCanceled` ise <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> ve `VSQueryEditResult` değer <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit kümesine sahipse, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> kullanıcıların izinleri sorunu çözmesi için hata döndürmemelidir. Projenin ardından şunları yapması gerekir:  
  
        Çağırarak hatayı kullanıcıya bildirin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> . ve <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> hata kodunu öğesine döndürün <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .  
  
   - `VSQueryEditResult`Değer ise <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> ve `VSQueryEditResultFlags` değer <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit kümesine sahipse, proje dosyası <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> ,,...) çağırarak kullanıma alınmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> .  
  
4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>Proje dosyasındaki çağrı dosyanın kullanıma alınmasına ve alınacak en son sürüme neden oluyorsa, proje kaldırılır ve yeniden yüklenir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Yöntemi, projenin başka bir örneği oluşturulduktan sonra yeniden çağrılır. Bu ikinci çağrıda, proje dosyası diske yazılabilir; Projenin bir önceki biçimde proje dosyasının bir kopyasını ile kaydetmesi önerilir. ESKI uzantı, gerekli yükseltme değişikliklerini yapın ve proje dosyasını yeni biçimde kaydedin. Yine, yükseltme işleminin herhangi bir bölümü başarısız olursa, yöntemi dönerek hata olduğunu belirtmelidir <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> . Bu, projenin Çözüm Gezgini bellekten kaldırılmasına neden olur.  
  
    Yöntemine yapılan çağrının <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (ReportOnly değerini belirtmek) ve bayraklarını döndürdüğü durum için ortamda oluşan tamamlanmış işlemi anlamak önemlidir <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> .  
  
5. Kullanıcı proje dosyasını açmaya çalışır.  
  
6. Ortam, uygulamanızı çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> .  
  
7. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>Dönerse `true` , ortam uygulamanızı çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> .  
  
8. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> dosyayı açmak ve proje nesnesini başlatmak için uygulamanızı çağırır, örneğin, Project1.  
  
9. Ortam, `IVsProjectUpgrade::UpgradeProject` Proje dosyasının yükseltilmesi gerekip gerekmediğini öğrenmek için uygulamanızı çağırır.  
  
10. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>Parametresi için bir değerini çağırır ve geçirin <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` .  
  
11. Ortamı için döner <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> `VSQueryEditResult` ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit ' de ayarlanır `VSQueryEditResultFlags` .  
  
12. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>Uygulamanızın çağrısı `IVsQueryEditQuerySave::QueryEditFiles` ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> ).  
  
    Bu çağrı, proje dosyanızın yeni bir kopyasının kullanıma alınması ve en son sürümün alınması ve ayrıca proje dosyanızı yeniden yüklenmesi gereksinimini ortadan çıkarabilir. Bu noktada, iki işlemlerden biri gerçekleşir:  
  
- Kendi proje yeniden yükleme uygulamanızı işlebiliyorsanız, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) uygulamanızı çağırır. Bu çağrıyı aldığınızda, projenizin ilk örneğini yeniden yükleyin (Project1) ve proje dosyanızı yükseltmeye devam edin. Ortam, `true` () için geri döntakdirde kendi proje yeniden yükleme uygulamanızı işleceğini bilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
- Kendi proje yeniden yükleme işlemeyin, `false` () için öğesini geri döndürürler <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> . Bu durumda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ([QEF_ForceEdit_NoPrompting](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags), [QEF_DisallowInMemoryEdits](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags),) önce, ortam, örneğin, Project2 gibi başka bir yeni, örnek oluşturur.  
  
  1. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> Project1 ilk proje nesnesini çağırır, bu nedenle bu nesneyi etkin olmayan duruma yerleştirir.  
  
  2. Ortam `IVsProjectFactory::CreateProject` , Project2 projenizin ikinci bir örneğini oluşturmak için uygulamanızı çağırır.  
  
  3. Ortam, `IPersistFileFormat::Load` dosyayı açmak ve Project2 ikinci proje nesnesini başlatmak için uygulamanızı çağırır.  
  
  4. Ortam `IVsProjectUpgrade::UpgradeProject` , proje nesnesinin yükseltilmesi gerekip gerekmediğini belirlemekte ikinci bir kez çağrı yapmış olur. Ancak bu çağrı, Project2 projesinin yeni, ikinci bir örneğinde yapılır. Bu, çözümde açılan projem.  
  
      > [!NOTE]
      > İlk projenizin, Project1, etkin olmayan durumda yerleştirildiğinden, <xref:Microsoft.VisualStudio.VSConstants.S_OK> uygulamanıza ilk çağrıdan geri dönmeniz gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> . Uygulamasının uygulanması için bkz. [temel proje](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) `IVsProjectUpgrade::UpgradeProject` .  
  
  5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>Parametresi için bir değerini çağırır ve geçirin <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` .  
  
  6. Ortam döndürülür <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> ve proje dosyası yazılabildiğinden yükseltme devam edebilir.  
  
  Yükseltme işlemi başarısız olursa, öğesinden geri <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> dönün `IVsProjectUpgrade::UpgradeProject` . Yükseltme gerekmez veya yükseltme yapmadıysanız, `IVsProjectUpgrade::UpgradeProject` çağrıyı hiçbir işlem olmadan değerlendirin. Geri dönerseniz <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> , projeniz için çözüme bir yer tutucu düğüm eklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Dönüştürme Sihirbazı](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Proje öğeleri yükseltiliyor](../misc/upgrading-project-items.md)   
 [Projeler](../extensibility/internals/projects.md)