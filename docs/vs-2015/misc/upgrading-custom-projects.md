---
title: Özel Projeleri Yükseltme | Microsoft Dokümanlar
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
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037213"
---
# <a name="upgrading-custom-projects"></a>Özel Projeleri Yükseltme
Proje dosyasında kalıcı bilgileri ürününüzün farklı Visual Studio sürümleri arasında değiştirirseniz, proje dosyanızın eski sürümden yeni sürüme yükseltilmesine destek olmanız gerekir. **Visual Studio Dönüşüm Sihirbazı'na**katılmanızı sağlayan yükseltmeyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> desteklemek için arabirimi uygulayın. Bu arabirim, kopya yükseltme için kullanılabilen tek mekanizmayı içerir. Projenin yükseltme süreçi, çözümün bir bir araçı açılışının bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Arabirim proje fabrikası tarafından uygulanır veya en azından proje fabrikasından elde edilmelidir.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Arabirimi kullanan eski mekanizma hala desteklenir, ancak proje açık bir parçası olarak proje sistemini kavramsal olarak yükseltir. Bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> nedenle <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirim [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çağrılsa veya uygulansa bile arabirim ortam tarafından çağrılır. Bu yaklaşım, kopyave proje yalnızca yükseltme bölümlerini uygulamak için kullanmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> ve yerinde yapılacak işin geri kalanını (büyük olasılıkla yeni <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> konumda) arabirim tarafından temsilci sağlar.  
  
 Örnek bir uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>için [VSSDK Örnekleri](../misc/vssdk-samples.md)bölümüne bakın.  
  
 Proje yükseltmeleri ile ilgili aşağıdaki senaryolar ortaya çıkar:  
  
- Dosya, projenin destekedebileceğinden daha yeni bir biçimdeyse, bunu belirten bir hata döndürmesi gerekir. Bu, ürününüzün eski sürümünün (örneğin Visual Studio .NET 2003) sürümü denetlenecek kod içerdiğini varsayar.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> Bayrak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yöntemde belirtilirse, yükseltme, projenin açılışından önce yerinde yükseltme olarak uygulanacaktır.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> Bayrak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yöntemde belirtilirse, yükseltme kopya yükseltmesi olarak uygulanır.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Aramada <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> bayrak belirtilirse, proje açıldıktan sonra kullanıcıdan proje dosyasını yerinde yükseltme olarak yükseltmesi istenir. Örneğin, ortam, kullanıcı çözümün eski bir sürümünü açtığında kullanıcıdan yükseltmesini ister.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Aramada <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> bayrak belirtilmemişse, kullanıcıdan proje dosyasını yükseltmesini isteminiz gerekir.  
  
     Aşağıda bir örnek yükseltme istemi iletisi verilmiştir:  
  
     "Proje '%1' Visual Studio eski bir sürümü ile oluşturuldu. Visual Studio'nun bu sürümüyle açarsanız, Visual Studio'nun eski sürümleriyle açamayabilirsiniz. Bu projeye devam etmek ve açmak istiyor musunuz?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory uygulamak için  
  
1. Arabirim yöntemini, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> özellikle <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> proje fabrikası uygulamayöntemini uygulayın veya uygulamaları proje fabrikası uygulamanızdan çağrılabilir hale getirin.  
  
2. Çözüm açmanın bir parçası olarak yerinde yükseltme yapmak istiyorsanız, bayrağı <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> uygulamanızda `VSPUVF_FLAGS` <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> parametre olarak tedarik edin.  
  
3. Çözüm açmanın bir parçası olarak yerinde yükseltme yapmak istiyorsanız, bayrağı <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> uygulamanızda `VSPUVF_FLAGS` <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> parametre olarak tedarik edin.  
  
4. Hem 2 hem de 3 adımları için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>gerçek dosya yükseltme adımları, kullanarak , `IVsProjectUpgade`aşağıdaki "Uygulama " bölümünde açıklandığı gibi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>uygulanabilir, ya da gerçek dosya yükseltme sini .  
  
5. Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> Geçiş Sihirbazı'nı kullanarak kullanıcı için yükseltme ile ilgili iletileri göndermek için yöntemleri kullanın.  
  
6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>arabirimi, proje yükseltmesinin bir parçası olarak gerçekleşmesi gereken her türlü dosya yükseltmesini uygulamak için kullanılır. Bu arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>proje sisteminin bir parçası olan dosyaları yükseltmek için bir mekanizma olarak verilir, ancak ana proje sistemi doğrudan farkında olmayabilir çağrılır. Örneğin, derleyiciile ilgili dosya ve özellikler proje sisteminin geri kalanını işleyen aynı geliştirme ekibi tarafından işlenmezse bu durum ortaya çıkabilir.  
  
## <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade Uygulaması  
 Proje sisteminiz yalnızca <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uygularsa, **Visual Studio Dönüşüm Sihirbazı'na**katılamaz. Ancak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi uygulasanız bile, dosya yükseltmesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uygulamaya yine de devredebilirsiniz.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade uygulamak için  
  
1. Bir kullanıcı projeyi açmaya çalıştığında, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> yöntem proje açıldıktan sonra ve proje üzerinde başka bir kullanıcı eylemi yapılmadan önce ortam tarafından çağrılır. Kullanıcıdan çözümü yükseltmesi istendiyse, <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> bayrak `grfUpgradeFlags` parametrede geçirilir. Kullanıcı, **Varolan Proje Ekle** komutunu kullanarak doğrudan bir proje <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> açarsa, bayrak geçirilir ve projenin kullanıcıdan yükseltme ye geçmesini ister.  
  
2. Çağrıya <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> yanıt olarak, projenin proje dosyasının yükseltilip yükseltilmediğini değerlendirmesi gerekir. Proje türünü yeni bir sürüme yükseltmesi gerekmiyorsa, bayrağı <xref:Microsoft.VisualStudio.VSConstants.S_OK> döndürebilir.  
  
3. Projenin proje türünü yeni bir sürüme yükseltmesi gerekiyorsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> yöntem çağırArak ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` parametre için bir değer geçirerek proje dosyasının değiştirilip değiştirilemeyeceğini belirlemesi gerekir. Proje daha sonra aşağıdakileri yapmak gerekir:  
  
   - Parametrede döndürülen `VSQueryEditResult` değer <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>ise, proje dosyası yazılabilir, çünkü yükseltme devam edebilir. `pfEditCanceled`  
  
   - `pfEditCanceled` Parametrede döndürülen `VSQueryEditResult` değer <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> ise `VSQueryEditResult` ve değer <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit kümesine sahipse, kullanıcıların izinler sorununu kendileri çözmeleri gerektiğinden, hata döndürmesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> gerekir. Proje daha sonra aşağıdakileri yapmalıdır:  
  
        Arayarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>hatayı kullanıcıya bildirin. ve <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> hata kodunu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>' ya döndürün.  
  
   - `VSQueryEditResult` Değer bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> kümesine `VSQueryEditResultFlags` sahipse, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> proje dosyası (, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...) çağırArak kullanıma alınmalıdır.  
  
4. Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> dosyasındaki arama, dosyanın kullanıma alınmasına ve en son sürümün alınmasına neden oluyorsa, proje boşaltılır ve yeniden yüklenir. Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> projenin başka bir örneği oluşturulduktan sonra yeniden çağrılır. Bu ikinci çağrıda, proje dosyası diske yazılabilir; proje dosyasının bir kopyasını önceki biçimde bir . ile kaydetmesi önerilir. ESKI uzantısı, gerekli yükseltme değişiklikleri yapmak ve yeni biçiminde proje dosyası kaydedin. Yine, yükseltme işleminin herhangi bir bölümü başarısız olursa, <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>yöntem döndürerek başarısızlığı göstermelidir. Bu, projenin Çözüm Gezgini'nde boşaltılmasına neden olur.  
  
    <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Yönteme çağrının (ReportOnly değerini belirterek) ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bayrakları döndürdeği <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> için ortamda oluşan tüm işlemi anlamak önemlidir.  
  
5. Kullanıcı proje dosyasını açmaya çalışır.  
  
6. Ortam uygulamanızı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> çağırır.  
  
7. İade <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> `true`edilirse, ortam uygulamanızı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> çağırır.  
  
8. Ortam, dosyayı açmak ve proje nesnesini (örneğin Project1) başlatması için uygulamanızı <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> çağırır.  
  
9. Ortam, proje `IVsProjectUpgrade::UpgradeProject` dosyasının yükseltilmesi gerekip gerekmediğini belirlemek için uygulamanızı çağırır.  
  
10. Parametre <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> için bir değer arar ve geçersiniz. `rgfQueryEdit`  
  
11. Ortam için <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> `VSQueryEditResult` geri <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> döner ve `VSQueryEditResultFlags`bit olarak ayarlanır.  
  
12. Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> `IVsQueryEditQuerySave::QueryEditFiles` çağrılarınız<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>( , ).  
  
    Bu arama, proje dosyanızın yeni bir kopyasının kullanıma alınmasına ve en son sürümün alınmasına ve proje dosyanızı yeniden yükleme gereksinimine neden olabilir. Bu noktada, iki şeyden biri olur:  
  
- Kendi proje yeniden işleyebilirseniz, o zaman <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> ortam (VSITEMID_ROOT) uygulama çağırır. Bu çağrıyı aldığınızda, projenizin ilk örneğini yeniden yükleyin (Project1) ve proje dosyanızı yükseltmeye devam edin. Çevre, geri döndüğünüzde `true` kendi projeyeniden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> işlemek<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>bilir ( ).  
  
- Kendi proje yeniden işlemek yoksa, o zaman `false` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> için<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>geri dönmek ( ). Bu durumda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>önce[(QEF_ForceEdit_NoPrompting](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags), [QEF_DisallowInMemoryEdits](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags),) döner, ortam başka bir yeni oluşturur, projenizin örneğin, Project2, aşağıdaki gibi:  
  
  1. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> ilk proje nesneniz olan Project1'i çağırır ve böylece bu nesneyi etkin olmayan duruma yerleştirilmesi ne kadar önemli.  
  
  2. Ortam, projenizin ikinci bir örneğini oluşturmak için uygulamanızı `IVsProjectFactory::CreateProject` çağırır, Project2.  
  
  3. Ortam, dosyayı açmak ve ikinci proje nesnesi Project2'yi başlatmak için uygulamanızı `IPersistFileFormat::Load` çağırır.  
  
  4. Ortam, `IVsProjectUpgrade::UpgradeProject` proje nesnesinin yükseltilip yükseltilmeyeceğini belirlemek için ikinci kez çağrıda bulunur. Ancak, bu arama yeni, ikinci, projenin örneği, Project2 yapılır. Bu çözüm de açılan projedir.  
  
      > [!NOTE]
      > İlk projeniz Olan Project1'in etkin olmayan duruma yerleştirildiğinde, ilk <xref:Microsoft.VisualStudio.VSConstants.S_OK> çağrıdan uygulamanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> için dönmeniz gerekir. Bir uygulama için Temel `IVsProjectUpgrade::UpgradeProject` [Proje'ye](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) bakın.  
  
  5. Parametre <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> için bir değer arar ve geçersiniz. `rgfQueryEdit`  
  
  6. Proje dosyası <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> yazılabilir, çünkü ortam döndürür ve yükseltme devam edebilir.  
  
  Yükseltmeyi başaramazsanız, <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> `IVsProjectUpgrade::UpgradeProject`'den dön' Yükseltme gerekli değilse veya yükseltmemeyi seçerseniz, `IVsProjectUpgrade::UpgradeProject` aramayı bir no-op olarak ele alabilirsiniz. Geri dönerseniz, <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>projenizin çözümüne bir yer tutucu düğümü eklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Dönüşüm Sihirbazı](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Proje Öğelerini Yükseltme](../misc/upgrading-project-items.md)   
 [Projeler](../extensibility/internals/projects.md)