---
title: Projeleri Yükseltme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9170532746dfc61cdec6636fb669676a94535de1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303234"
---
# <a name="upgrading-projects"></a>Projeleri Yükseltme

Visual Studio'nun bir sürümünden diğerine proje modelinde yapılan değişiklikler, projelerin ve çözümlerin yeni sürümde çalıştırılabilmeleri için yükseltilmesigerektirebilir. Kendi [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] projelerinizde yükseltme desteği uygulamak için kullanılabilecek arabirimler sağlar.

## <a name="upgrade-strategies"></a>Yükseltme Stratejileri

Yükseltmeyi desteklemek için proje sistem uygulamanızın bir yükseltme stratejisi tanımlaması ve uygulaması gerekir. Stratejinizi belirlerken, yan yana (SxS) yedeklemeyi, yedeklemekopyalamayı veya her ikisini birden desteklemeyi seçebilirsiniz.

- SxS yedekleme, bir projenin yalnızca yerinde yükseltmesi gereken dosyaları kopyalayarak uygun bir dosya adı eki (örneğin,.eski" anlamına gelir) anlamına gelir.

- Yedeklemeyi kopyala, projenin tüm proje öğelerini kullanıcı tarafından sağlanan yedekleme konumuna kopyalandığı anlamına gelir. Özgün proje konumundaki ilgili dosyalar daha sonra yükseltilir.

## <a name="how-upgrade-works"></a>Yükseltme Nasıl Çalışır?

Visual Studio'nun önceki bir sürümünde oluşturulan bir çözüm daha yeni bir sürümde açıldığında, IDE yükseltmesi gerekip gerekmeden gerekip gerekolmadığını belirlemek için çözüm dosyasını denetler. Yükseltme gerekiyorsa, **Yükseltme Sihirbazı** kullanıcıyı yükseltme işleminde yürümek için otomatik olarak başlatılır.

Bir çözümün yükseltmesi gerektiğinde, yükseltme stratejisi için her proje fabrikasını sorgular. Strateji, proje fabrikasının kopya yedeklemesini mi yoksa SxS yedeklemesini mi desteklediğini belirler. Bilgiler, yedekleme için gerekli bilgileri toplayan ve geçerli seçenekleri kullanıcıya sunan **Yükseltme Sihirbazı'na**gönderilir.

### <a name="multi-project-solutions"></a>Çoklu Proje Çözümleri

Bir çözüm birden çok proje içeriyorsa ve yalnızca SxS yedeklemesini destekleyen bir C++ projesi ve yalnızca kopya yedeklemesini destekleyen bir Web projesi gibi yükseltme stratejileri farklıysa, proje fabrikalarının yükseltme stratejisini müzakere etmesi gerekir.

Çözüm, her proje fabrikasını <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Daha sonra, genel proje dosyalarının yükseltmeye ihtiyacı olup olmadığını görmek ve desteklenen yükseltme stratejilerini belirlemek için çağrıda bulunur. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> **Yükseltme Sihirbazı** daha sonra çağrılır.

Kullanıcı sihirbazı tamamladıktan <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> sonra, gerçek yükseltme gerçekleştirmek için her proje fabrikasında çağrılır. Yedeklemeyi kolaylaştırmak için, IVsProjectUpgradeViaFactory yöntemleri yükseltme işleminin ayrıntılarını günlüğe kaydetmek için <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> hizmeti sağlar. Bu hizmet önbelleğe alınamaz.

İlgili tüm genel dosyaları güncelledikten sonra, her proje fabrikası bir projeyi anında kullanmayı seçebilir. Proje uygulaması desteklemelidir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Yöntem <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> daha sonra ilgili tüm proje öğelerini yükseltmek için çağrılır.

> [!NOTE]
> Yöntem <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> SVsUpgradeLogger hizmetini sağlamaz. Bu hizmet arayarak <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>elde edilebilir.

## <a name="best-practices"></a>En İyi Uygulamalar

Bir <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> dosyayı düzenlemeden önce düzenleyip düzenleyip düzenleyip düzenleyip düzenleyip düzenleyip düzenlemediğinizi kontrol etmek için hizmeti kullanın ve kaydetmeden önce kaydedebilirsiniz. Bu, yedekleme ve yükseltme uygulamalarınızın proje dosyalarını kaynak denetimi altında, yetersiz izinlere sahip dosyaları vb. işlemesine yardımcı olur.

Yükseltme <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> işleminin başarısı veya başarısızlığı hakkında bilgi sağlamak için yedekleme ve yükseltmenin tüm aşamalarında hizmeti kullanın.

Projeleri yedekleme ve yükseltme hakkında daha fazla bilgi için vsshell2.idl'deki IVsProjectUpgrade yorumlarına bakın.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a>Özel Projeleri Yükseltme

Proje dosyasında kalıcı bilgileri ürününüzün farklı Visual Studio sürümleri arasında değiştirirseniz, proje dosyanızın eski sürümden yeni sürüme yükseltilmesine destek olmanız gerekir. **Visual Studio Dönüşüm Sihirbazı'na**katılmanızı sağlayan yükseltmeyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> desteklemek için arabirimi uygulayın. Bu arabirim, kopya yükseltme için kullanılabilen tek mekanizmayı içerir. Projenin yükseltme süreçi, çözümün bir bir araçı açılışının bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Arabirim proje fabrikası tarafından uygulanır veya en azından proje fabrikasından elde edilmelidir.

<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Arabirimi kullanan eski mekanizma hala desteklenir, ancak proje açık bir parçası olarak proje sistemini kavramsal olarak yükseltir. Bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> nedenle arabirim çağrılsa veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> uygulansa bile, arabirim Visual Studio ortamı tarafından çağrılır. Bu yaklaşım, kopyave proje yalnızca yükseltme bölümlerini uygulamak için kullanmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> ve yerinde yapılacak işin geri kalanını (büyük olasılıkla yeni <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> konumda) arabirim tarafından temsilci sağlar.

Örnek bir uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>için [VSSDK Örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples)bölümüne bakın.

Proje yükseltmeleri ile ilgili aşağıdaki senaryolar ortaya çıkar:

- Dosya, projenin destekedebileceğinden daha yeni bir biçimdeyse, bunu belirten bir hata döndürmesi gerekir. Bu, ürününüzün eski sürümünün sürümü denetlemek için kod içerdiğini varsayar.

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> Bayrak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yöntemde belirtilirse, yükseltme, projenin açılışından önce yerinde yükseltme olarak uygulanacaktır.

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> Bayrak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yöntemde belirtilirse, yükseltme kopya yükseltmesi olarak uygulanır.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Aramada <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrak belirtilirse, proje açıldıktan sonra kullanıcıdan proje dosyasını yerinde yükseltme olarak yükseltmesi istenir. Örneğin, ortam, kullanıcı çözümün eski bir sürümünü açtığında kullanıcıdan yükseltmesini ister.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Aramada <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrak belirtilmemişse, kullanıcıdan proje dosyasını yükseltmesini isteminiz gerekir.

     Aşağıda bir örnek yükseltme istemi iletisi verilmiştir:

     "Proje '%1' Visual Studio eski bir sürümü ile oluşturuldu. Visual Studio'nun bu sürümüyle açarsanız, Visual Studio'nun eski sürümleriyle açamayabilirsiniz. Bu projeye devam etmek ve açmak istiyor musunuz?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory uygulamak için

1. Arabirim yöntemini, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> özellikle <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> proje fabrikası uygulamayöntemini uygulayın veya uygulamaları proje fabrikası uygulamanızdan çağrılabilir hale getirin.

2. Çözüm açmanın bir parçası olarak yerinde yükseltme yapmak istiyorsanız, bayrağı <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> uygulamanızda `VSPUVF_FLAGS` <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> parametre olarak tedarik edin.

3. Çözüm açmanın bir parçası olarak yerinde yükseltme yapmak istiyorsanız, bayrağı <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> uygulamanızda `VSPUVF_FLAGS` <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> parametre olarak tedarik edin.

4. Hem 2 hem de 3 adımları için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>gerçek dosya yükseltme adımları, kullanarak , `IVsProjectUpgade`aşağıdaki "Uygulama " bölümünde açıklandığı gibi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>uygulanabilir, ya da gerçek dosya yükseltme sini .

5. Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> Geçiş Sihirbazı'nı kullanarak kullanıcı için yükseltme ile ilgili iletileri göndermek için yöntemleri kullanın.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>arabirimi, proje yükseltmesinin bir parçası olarak gerçekleşmesi gereken her türlü dosya yükseltmesini uygulamak için kullanılır. Bu arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>proje sisteminin bir parçası olan dosyaları yükseltmek için bir mekanizma olarak verilir, ancak ana proje sistemi doğrudan farkında olmayabilir çağrılır. Örneğin, derleyiciile ilgili dosya ve özellikler proje sisteminin geri kalanını işleyen aynı geliştirme ekibi tarafından işlenmezse bu durum ortaya çıkabilir.

### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade Uygulaması

Proje sisteminiz yalnızca <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uygularsa, **Visual Studio Dönüşüm Sihirbazı'na**katılamaz. Ancak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi uygulasanız bile, dosya yükseltmesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uygulamaya yine de devredebilirsiniz.

#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade uygulamak için

1. Bir kullanıcı projeyi açmaya çalıştığında, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> yöntem proje açıldıktan sonra ve proje üzerinde başka bir kullanıcı eylemi yapılmadan önce ortam tarafından çağrılır. Kullanıcıdan çözümü yükseltmesi istendiyse, <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrak `grfUpgradeFlags` parametrede geçirilir. Kullanıcı, **Varolan Proje Ekle** komutunu kullanarak doğrudan bir proje <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> açarsa, bayrak geçirilir ve projenin kullanıcıdan yükseltme ye geçmesini ister.

2. Çağrıya <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> yanıt olarak, projenin proje dosyasının yükseltilip yükseltilmediğini değerlendirmesi gerekir. Proje türünü yeni bir sürüme yükseltmesi gerekmiyorsa, bayrağı <xref:Microsoft.VisualStudio.VSConstants.S_OK> döndürebilir.

3. Projenin proje türünü yeni bir sürüme yükseltmesi gerekiyorsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> yöntem çağırArak ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` parametre için bir değer geçirerek proje dosyasının değiştirilip değiştirilemeyeceğini belirlemesi gerekir. Proje daha sonra aşağıdakileri yapmak gerekir:

    - Parametrede döndürülen `VSQueryEditResult` değer <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>ise, proje dosyası yazılabilir, çünkü yükseltme devam edebilir. `pfEditCanceled`

    - `pfEditCanceled` Parametrede döndürülen `VSQueryEditResult` değer <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> ise `VSQueryEditResult` ve değer <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> bit kümesine sahipse, kullanıcıların izinler sorununu kendileri çözmeleri gerektiğinden, hata döndürmesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> gerekir. Proje daha sonra aşağıdakileri yapmalıdır:

         Arayarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> hatayı kullanıcıya bildirin <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> ve hata <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>kodunu ' ya döndürün.

    - `VSQueryEditResult` Değer bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> kümesine `VSQueryEditResultFlags` sahipse, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> proje dosyası (, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...) çağırArak kullanıma alınmalıdır.

4. Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> dosyasındaki arama, dosyanın kullanıma alınmasına ve en son sürümün alınmasına neden oluyorsa, proje boşaltılır ve yeniden yüklenir. Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> projenin başka bir örneği oluşturulduktan sonra yeniden çağrılır. Bu ikinci çağrıda, proje dosyası diske yazılabilir; proje dosyasının bir kopyasını önceki biçimde bir . ile kaydetmesi önerilir. ESKI uzantısı, gerekli yükseltme değişiklikleri yapmak ve yeni biçiminde proje dosyası kaydedin. Yine, yükseltme işleminin herhangi bir bölümü başarısız olursa, <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>yöntem döndürerek başarısızlığı göstermelidir. Bu, projenin Çözüm Gezgini'nde boşaltılmasına neden olur.

     <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Yönteme çağrının (ReportOnly değerini belirterek) ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bayrakları döndürdeği <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> için ortamda oluşan tüm işlemi anlamak önemlidir.

5. Kullanıcı proje dosyasını açmaya çalışır.

6. Ortam uygulamanızı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> çağırır.

7. İade <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> `true`edilirse, ortam uygulamanızı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> çağırır.

8. Ortam, dosyayı açmak ve proje nesnesini (örneğin Project1) başlatması için uygulamanızı <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> çağırır.

9. Ortam, proje `IVsProjectUpgrade::UpgradeProject` dosyasının yükseltilmesi gerekip gerekmediğini belirlemek için uygulamanızı çağırır.

10. Parametre <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> için bir değer arar ve geçersiniz. `rgfQueryEdit`

11. Ortam için <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> `VSQueryEditResult` geri <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> döner ve `VSQueryEditResultFlags`bit olarak ayarlanır.

12. Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> `IVsQueryEditQuerySave::QueryEditFiles` çağrılarınız<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>( , ).

Bu arama, proje dosyanızın yeni bir kopyasının kullanıma alınmasına ve en son sürümün alınmasına ve proje dosyanızı yeniden yükleme gereksinimine neden olabilir. Bu noktada, iki şeyden biri olur:

- Kendi proje yeniden işleyebilirseniz, o zaman <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> ortam (VSITEMID_ROOT) uygulama çağırır. Bu çağrıyı aldığınızda, projenizin ilk örneğini yeniden yükleyin (Project1) ve proje dosyanızı yükseltmeye devam edin. Çevre, geri döndüğünüzde `true` kendi projeyeniden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> işlemek<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>bilir ( ).

- Kendi proje yeniden işlemek yoksa, o zaman `false` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> için<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>geri dönmek ( ). Bu durumda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) dönmeden önce, ortam projenizin project2 gibi yeni bir örneğini aşağıdaki gibi oluşturur:

    1. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> ilk proje nesneniz olan Project1'i çağırır ve böylece bu nesneyi etkin olmayan duruma yerleştirilmesi ne kadar önemli.

    2. Ortam, projenizin ikinci bir örneğini oluşturmak için uygulamanızı `IVsProjectFactory::CreateProject` çağırır, Project2.

    3. Ortam, dosyayı açmak ve ikinci proje nesnesi Project2'yi başlatmak için uygulamanızı `IPersistFileFormat::Load` çağırır.

    4. Ortam, `IVsProjectUpgrade::UpgradeProject` proje nesnesinin yükseltilip yükseltilmeyeceğini belirlemek için ikinci kez çağrıda bulunur. Ancak, bu arama yeni, ikinci, projenin örneği, Project2 yapılır. Bu çözüm de açılan projedir.

        > [!NOTE]
        > İlk projeniz Olan Project1'in etkin olmayan duruma yerleştirildiğinde, ilk <xref:Microsoft.VisualStudio.VSConstants.S_OK> çağrıdan uygulamanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> için dönmeniz gerekir.

    5. Parametre <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> için bir değer arar ve geçersiniz. `rgfQueryEdit`

    6. Proje dosyası <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> yazılabilir, çünkü ortam döndürür ve yükseltme devam edebilir.

Yükseltmeyi başaramazsanız, <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> `IVsProjectUpgrade::UpgradeProject`'den dön' Yükseltme gerekli değilse veya yükseltmemeyi seçerseniz, `IVsProjectUpgrade::UpgradeProject` aramayı bir no-op olarak ele alabilirsiniz. Geri dönerseniz, <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>projenizin çözümüne bir yer tutucu düğümü eklenir.

## <a name="upgrading-project-items"></a>Proje Öğelerini Yükseltme

Uygulamadığınız proje sistemlerine öğe ekler veya yönetirseniz, proje yükseltme işlemine katılmanız gerekebilir. Kristal Raporlar, proje sistemine eklenebilecek bir öğeörneğidir.

Genellikle, proje öğesi uygulayıcıları, proje başvurularının ne olduğunu ve yükseltme kararı almak için diğer proje özelliklerinin ne olduğunu bilmeleri gerektiğinden, zaten tamamen anında ve yükseltilmiş bir projeden yararlanmak isterler.

### <a name="to-get-the-project-upgrade-notification"></a>Proje yükseltme bildirimini almak için

1. Proje <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> öğesi uygulamanızda bayrağı (vsshell80.idl'de tanımlanan) ayarlayın. Bu, Visual Studio kabuğu bir proje sisteminin yükseltme sürecinde olduğunu belirlediğinde proje öğesi VSPackage'ın otomatik yüklenmesine neden olur.

2. Yöntem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> aracılığıyla arayüz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> tavsiye.

3. Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> proje sistemi uygulaması yükseltme işlemlerini tamamladıktan ve yeni yükseltilmiş proje oluşturulduktan sonra ateşlenir. Senaryoya bağlı olarak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> arabirim <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, , <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> yöntemleri sonra ateşlenir.

### <a name="to-upgrade-the-project-item-files"></a>Proje öğesi dosyalarını yükseltmek için

1. Proje öğesi uygulamanızda dosya yedekleme işlemini dikkatle yönetmeniz gerekir. Bu, özellikle `fUpgradeFlag` <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yöntemin parametresi olarak ayarlandığı <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>yan yana yedekleme için geçerlidir , yedeklenmiş olan dosyalar ".eski" olarak belirlenmiş yan dosyaların yanına yerleştirilir. Projenin yükseltilmesinde sistem süresinden daha eski yedeklenmiş dosyalar eski olarak atanabilir. Ayrıca, bunu önlemek için belirli adımlar atmadığınız sürece bunlar üzerine yazılabilir.

2. Proje öğeniz proje yükseltmesi hakkında bir bildirim aldığında, **Visual Studio Dönüşüm Sihirbazı** hala görüntülenir. Bu nedenle, sihirbaz UI <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> yükseltme iletileri sağlamak için arabirim yöntemlerini kullanmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler](../../extensibility/internals/projects.md)
