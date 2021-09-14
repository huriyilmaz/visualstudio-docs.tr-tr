---
title: Projeleri yükseltme | Microsoft Docs
description: Visual Studio SDK 'nın projelerinizde yükseltme desteğini uygulamak için sağladığı arabirimler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 426fb7499e9c6ce9fa5fc5c9e212f30b6a73a0f4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627308"
---
# <a name="upgrading-projects"></a>Projeleri Yükseltme

bir Visual Studio sürümden bir sonrakine proje modelinde yapılan değişiklikler, daha yeni sürümde çalıştırılabilmesi için projelerin ve çözümlerin yükseltilmesini gerektirebilir. , [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Kendi projelerinizde yükseltme desteğini uygulamak için kullanılabilen arabirimler sağlar.

## <a name="upgrade-strategies"></a>Yükseltme stratejileri

Bir yükseltmeyi desteklemek için, proje sistemi uygulamanızın bir yükseltme stratejisi tanımlayıp uygulaması gerekir. Stratejinizi belirlemek için yan yana (SxS) yedeklemeyi, kopya yedeklemesini veya her ikisini de desteklemeyi seçebilirsiniz.

- SxS yedekleme, bir projenin yalnızca yükseltilmesi gereken dosyaları, örneğin ". old" gibi uygun bir dosya adı sonekini ekleyerek kopyaladığını gösterir.

- Kopya yedekleme, bir projenin tüm proje öğelerini Kullanıcı tarafından belirtilen bir yedekleme konumuna kopyaladığı anlamına gelir. Özgün proje konumundaki ilgili dosyalar yükseltilir.

## <a name="how-upgrade-works"></a>Yükseltme nasıl Işe yarar?

Visual Studio önceki bir sürümünde oluşturulan bir çözüm daha yeni bir sürümde açıldığında ıde, yükseltilmesi gerekip gerekmediğini öğrenmek için çözüm dosyasını denetler. Yükseltme gerekliyse, yükseltme **Sihirbazı** , kullanıcıya yükseltme işlemi boyunca yol gösterecek şekilde otomatik olarak başlatılır.

Bir çözümün yükseltilmesi gerektiğinde, her proje fabrikasını yükseltme stratejisi için sorgular. Strateji, proje fabrikasının kopya yedeklemesini mi yoksa SxS yedeklemesini mi desteklediğini belirler. Bilgiler, yedekleme için gereken bilgileri toplayan ve Kullanıcı için geçerli seçenekleri sunan **Yükseltme Sihirbazına** gönderilir.

### <a name="multi-project-solutions"></a>çoklu Project çözümleri

Bir çözüm birden çok proje içeriyorsa ve yükseltme stratejileri farklıysa (örneğin, yalnızca SxS yedeklemesini destekleyen bir C++ projesi ve yalnızca kopya yedeklemesini destekleyen bir Web projesi gibi), proje fabrikaları yükseltme stratejisi üzerinde anlaşmalıdır.

Çözüm her proje fabrikasını sorgular <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Daha sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> , genel proje dosyalarının yükseltilmesi gerekip gerekmediğini ve desteklenen yükseltme stratejilerini belirlemesini sağlamak için çağırır. **Yükseltme Sihirbazı** daha sonra çağrılır.

Kullanıcı Sihirbazı tamamladıktan sonra, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> gerçek yükseltmeyi gerçekleştirmek için her proje fabrikası üzerinde çağırılır. Backup 'ı kolaylaştırmak için IVsProjectUpgradeViaFactory yöntemleri, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> yükseltme işleminin ayrıntılarını günlüğe kaydetmek için hizmeti sağlar. Bu hizmet önbelleğe alınamaz.

Tüm ilgili genel dosyalar güncelleştirildikten sonra her proje fabrikası bir proje örneğini oluşturmayı seçebilirler. Proje uygulamasının desteklemesi gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Daha sonra tüm ilgili proje öğelerini yükseltmek için yöntemi çağırılır.

> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>Yöntemi, Svsupgradegünlükçü hizmetini sağlamaz. Bu hizmet çağırarak elde edilebilir <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .

## <a name="best-practices"></a>En İyi Uygulamalar

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>Düzenlemeden önce bir dosyayı düzenleyip düzenleyebiliyorsanız ve kaydetmeden önce bu hizmeti kaydedebilir. Bu, yedekleme ve yükseltme uygulamalarınızın, kaynak denetimi altındaki proje dosyalarını, yetersiz izinlere sahip dosyaları ve benzerlerini işlemesini yardımcı olur.

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>Yükseltme işleminin başarısı veya başarısızlığı hakkında bilgi sağlamak için yedekleme ve yükseltme aşamaları sırasında hizmeti kullanın.

Projeleri yedekleme ve yükseltme hakkında daha fazla bilgi için, vsshell2. IDL içindeki IVsProjectUpgrade için açıklamalara bakın.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a> Özel projeleri yükseltme

proje dosyasında kalıcı olan bilgileri ürününüzün farklı Visual Studio sürümleri arasında değiştirirseniz, proje dosyanızı eski sürümden yeni sürüme yükseltmeniz gerekir. **Visual Studio dönüştürme sihirbazına** katılımını sağlayan yükseltmeyi desteklemek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimini uygulayın. Bu arabirim, kopyalama yükseltme için kullanılabilen tek mekanizmayı içerir. Projenin yükseltilmesi, çözümün bir parçası olarak gerçekleşir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>Arabirim, proje fabrikası tarafından uygulanır veya en azından proje fabrikasında bilgiler kişilerden olmalıdır.

Arabirimi kullanan eski mekanizma <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> hala desteklenmektedir, ancak kavramsal olarak proje sistemini projenin bir parçası olarak yükseltir. arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> bu nedenle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirim çağrılıp uygulansa bile Visual Studio ortamı tarafından çağırılır. Bu yaklaşım <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , yalnızca yükseltmenin ve projenin yalnızca bir kısmını kopyalamak için ' i kullanmanıza olanak sağlar ve bu işlemi, arabirime göre (muhtemelen yeni konumda) yapılacak işin geri kalanını devredebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .

Örnek bir uygulama için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> bkz. [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Aşağıdaki senaryolar proje yükseltmeleri ile ortaya çıkar:

- Dosya projenin destekleyebileceğinden daha yeni bir biçimde ise, bunu belirten bir hata döndürmelidir. Bu, ürününüzün eski sürümünün sürümü denetlemek için kod içerdiğini varsayar.

- Bu <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> yöntemde bayrak belirtilmişse <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> , yükseltme, proje açılmadan önce yerinde bir yükseltme olarak uygulanır.

- Bu <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> yöntemde bayrak belirtilmişse <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> , yükseltme bir kopya yükseltme olarak uygulanır.

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>Çağrıda bayrak belirtilmişse <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> , proje açıldıktan sonra, Kullanıcı ortam tarafından proje dosyasını yerinde yükseltme olarak yükseltmek için bir kullanıcı tarafından istenir. Örneğin, ortam, Kullanıcı çözümün eski bir sürümünü açtığında kullanıcıdan yükseltme yapmanızı ister.

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>Çağrıda bayrak belirtilmemişse <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> , kullanıcıdan proje dosyasını yükseltmesini istemelidir.

     Aşağıda örnek bir yükseltme istemi iletisi verilmiştir:

     "' %1 ' projesi Visual Studio eski bir sürümüyle oluşturuldu. bu Visual Studio bu sürümü ile açarsanız, Visual Studio daha eski sürümleriyle açabilmeyebilirsiniz. Devam etmek ve bu projeyi açmak istiyor musunuz? "

### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory uygulamak için

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>Arabirim yöntemini, özellikle de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> proje fabrikası uygulamanızdaki yöntemi uygulayın veya uygulamaları proje fabrikası uygulamanızdan çağrılabilir hale getirin.

2. Çözümün açılması kapsamında bir yerinde yükseltme yapmak istiyorsanız, bayrağını <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> `VSPUVF_FLAGS` uygulamanızda parametre olarak belirtin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> .

3. Çözümün açılması kapsamında bir yerinde yükseltme yapmak istiyorsanız, bayrağını <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> `VSPUVF_FLAGS` uygulamanızda parametre olarak belirtin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> .

4. 2 ve 3. adımlarda, kullanarak gerçek dosya yükseltme adımları <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> aşağıdaki "uygulama" bölümünde açıklandığı gibi uygulanabilir `IVsProjectUpgade` veya gerçek dosya yükseltmeyi sürümüne atayabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .

5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>Visual Studio geçiş sihirbazı 'nı kullanarak kullanıcı için yükseltme ile ilgili ileti gönderme yöntemlerini kullanın.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> arabirim, proje yükseltmesinin bir parçası olarak gerçekleşmesi gereken herhangi bir tür dosya yükseltmesini uygulamak için kullanılır. Bu arabirim öğesinden çağrılmaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , ancak proje sisteminin bir parçası olan dosyaları yükseltmek için bir mekanizma olarak sağlanır, ancak ana proje sistemi doğrudan farkında olmayabilir. Örneğin, derleyici ile ilgili dosyalar ve özellikler proje sisteminin geri kalanını işleyen geliştirme ekibi tarafından işlenmezse bu durum ortaya çıkabilir.

### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade uygulaması

proje sisteminiz yalnızca uygularsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , **Visual Studio dönüştürme sihirbazına** katılamaz. Ancak, arabirimini uygulasanız bile <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , uygulamaya dosya yükseltmeyi de atayabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .

#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade 'i uygulamak için

1. Bir Kullanıcı bir projeyi açmayı denediğinde, proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> açıldıktan sonra ve proje üzerinde diğer herhangi bir kullanıcı eylemi alınmadan önce, yöntemi ortam tarafından çağrılır. Kullanıcının çözümü yükseltmesi zaten istenirse, <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrak `grfUpgradeFlags` parametreye geçirilir. kullanıcı bir projeyi doğrudan açarsa (örneğin, **var olan Project ekle** komutunu kullanarak), <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrak geçirilir ve projenin kullanıcıdan yükseltme yapması istenir.

2. Çağrıya yanıt olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Proje, proje dosyasının yükseltilip yükseltilmediğini değerlendirmelidir. Projenin proje türünü yeni bir sürüme yükseltmesi gerekmiyorsa, yalnızca <xref:Microsoft.VisualStudio.VSConstants.S_OK> bayrağı döndürebilir.

3. Projenin proje türünü yeni bir sürüme yükseltmesi gerekiyorsa, bu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> yöntemi çağırarak ve parametresi için değerini geçirerek proje dosyasının değiştirilip değiştirilemeyeceğini belirlemelidir <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` . Ardından projenin aşağıdakileri yapması gerekir:

    - `VSQueryEditResult`Parametresinde döndürülen değer `pfEditCanceled` ise <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> , proje dosyası yazılabildiğinden yükseltme devam edebilir.

    - `VSQueryEditResult`Parametresinde döndürülen değer `pfEditCanceled` ise <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> ve `VSQueryEditResult` değer <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> bit kümesine sahipse, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> kullanıcıların izinleri sorunu çözmesi için hata döndürmemelidir. Projenin ardından şunları yapması gerekir:

         Hata <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> kodunu çağırarak ve geri döndüren hatayı kullanıcıya bildirin <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .

    - `VSQueryEditResult`Değer ise <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> ve `VSQueryEditResultFlags` değer <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit kümesine sahipse, proje dosyası <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting> ,,...) çağırarak kullanıma alınmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits> .

4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>Proje dosyasındaki çağrı dosyanın kullanıma alınmasına ve alınacak en son sürüme neden oluyorsa, proje kaldırılır ve yeniden yüklenir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Yöntemi, projenin başka bir örneği oluşturulduktan sonra yeniden çağrılır. Bu ikinci çağrıda, proje dosyası diske yazılabilir; Projenin bir önceki biçimde proje dosyasının bir kopyasını ile kaydetmesi önerilir. ESKI uzantı, gerekli yükseltme değişikliklerini yapın ve proje dosyasını yeni biçimde kaydedin. Yine, yükseltme işleminin herhangi bir bölümü başarısız olursa, yöntemi dönerek hata olduğunu belirtmelidir <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> . Bu, projenin Çözüm Gezgini bellekten kaldırılmasına neden olur.

     Yöntemine yapılan çağrının <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (ReportOnly değerini belirtmek) ve bayraklarını döndürdüğü durum için ortamda oluşan tamamlanmış işlemi anlamak önemlidir <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> .

5. Kullanıcı proje dosyasını açmaya çalışır.

6. Ortam, uygulamanızı çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> .

7. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>Dönerse `true` , ortam uygulamanızı çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> .

8. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> dosyayı açmak ve proje nesnesini başlatmak için uygulamanızı çağırır, örneğin, Project1.

9. Ortam, `IVsProjectUpgrade::UpgradeProject` Proje dosyasının yükseltilmesi gerekip gerekmediğini öğrenmek için uygulamanızı çağırır.

10. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>Parametresi için bir değerini çağırır ve geçirin <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> `rgfQueryEdit` .

11. Ortamı için döner <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> `VSQueryEditResult` ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit ' de ayarlanır `VSQueryEditResultFlags` .

12. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>Uygulamanızın çağrısı `IVsQueryEditQuerySave::QueryEditFiles` ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting> , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits> ).

Bu çağrı, proje dosyanızın yeni bir kopyasının kullanıma alınması ve en son sürümün alınması ve ayrıca proje dosyanızı yeniden yüklenmesi gereksinimini ortadan çıkarabilir. Bu noktada, iki işlemlerden biri gerçekleşir:

- Kendi proje yeniden yükleme uygulamanızı işlebiliyorsanız, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) uygulamanızı çağırır. Bu çağrıyı aldığınızda, projenizin ilk örneğini yeniden yükleyin (Project1) ve proje dosyanızı yükseltmeye devam edin. ortamı, () için geri dönersiniz kendi proje yeniden yüklemenizi `true` işleyebli <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> olduğunu <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload> bilir.

- Kendi projenizi yeniden yükleyebiliyorsanız () için `false` geri <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload> dönersiniz. Bu durumda , (QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) geri gelmeden önce, ortam projenizin başka bir yeni örneğini (örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Project2) aşağıdaki gibi oluşturur:

    1. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> ilk proje nesneniz olan Project1'i çağırarak bu nesneyi etkin olmayan durumuna yerleştirmenizi sağlar.

    2. Ortam, `IVsProjectFactory::CreateProject` projenizin ikinci bir örneğini (Project2) oluşturmak için uygulamanızı çağırmaktadır.

    3. Ortam, dosyayı `IPersistFileFormat::Load` açmak ve ikinci proje nesnesi Olan Project2'i başlatmak için uygulamanızı arar.

    4. Ortam, `IVsProjectUpgrade::UpgradeProject` proje nesnesinin yükseltilecek olup olmadığını belirlemek için ikinci kez çağrısında bulundu. Ancak, bu çağrı projenin yeni, ikinci örneğinde (Project2) yapılır. Bu, çözümde açılan projedir.

        > [!NOTE]
        > İlk projenizin (Project1) etkin olmayan durumuna yerleştiril olduğu örnekte, uygulamanıza yapılan ilk <xref:Microsoft.VisualStudio.VSConstants.S_OK> çağrıdan dönmeniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> gerekir.

    5. çağrısında <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> bulundurarak parametresi için değerini <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> `rgfQueryEdit` iletirsiniz.

    6. Ortam geri <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> döner ve proje dosyası yazıldığı için yükseltme devam eder.

Yükseltme başarısız olursa, 'den <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> geri `IVsProjectUpgrade::UpgradeProject` dönersiniz. Yükseltme gerekli yoksa veya yükseltmeyi seçmezsiniz, `IVsProjectUpgrade::UpgradeProject` çağrıya bir no-op olarak davranın. geri <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> dönersiniz, projeniz için çözüme bir yer tutucu düğümü eklenir.

## <a name="upgrading-project-items"></a>Project Yükseltme

Uygulamadığını proje sistemlerine öğe ekler veya yönetirsiniz, proje yükseltme sürecine katılmanız gerekir. Crystal Reports, proje sistemine eklen bir öğe örneğidir.

Genellikle, proje öğesi uygulayanlar, yükseltme kararı almak için proje başvurularının ne olduğunu ve diğer proje özelliklerini bilmek zorunda olduğundan, zaten tamamen örneklenmiş ve yükseltilmiş bir projeden faydalanmalarını ister.

### <a name="to-get-the-project-upgrade-notification"></a>Proje yükseltme bildirimini almak için

1. Proje öğesi <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> uygulamanıza bayrağını (vsshell80.idl içinde tanımlanır) ayarlayın. Bu, Visual Studio kabuğu bir proje sisteminin yükseltme sürecinde olduğunu belirlerken proje öğenizin VSPackage'ın otomatik olarak yüklemesine neden olur.

2. yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> aracılığıyla arabirimini <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> önerin.

3. Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> proje sistemi uygulaması yükseltme işlemlerini tamamlandıktan ve yeni yükseltilen proje oluşturulduktan sonra oluşturulur. Senaryoya bağlı olarak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> arabirimi , <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> yöntemden sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> işten olur.

### <a name="to-upgrade-the-project-item-files"></a>Proje öğesi dosyalarını yükseltmek için

1. Proje öğesi uygulamanıza dosya yedekleme işlemini dikkatle yönetmeniz gerekir. Bu durum özellikle, yöntemin parametresinin yedeklene dosyaların `fUpgradeFlag` <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> ".old" olarak belirlenen dosyaların yan yana yerleştiril olduğu olarak ayarlan bir yan yana yedekleme <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> için geçerlidir. Projenin yükseltildikten sonra sistem zamanından daha eski yedekli dosyalar eski olarak belirlenilebilir. Ayrıca, bunu önlemek için belirli adımlar atmadıkça bunların üzerine yazılabilir.

2. Proje öğeniz proje yükseltme bildirimini alırken, Visual Studio **Dönüştürme Sihirbazı** görüntülenmeye devam ediyor. Bu nedenle, sihirbaz kullanıcı arabirimine yükseltme <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> iletileri sağlamak için arabiriminin yöntemlerini kullansanız iyi olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler](../../extensibility/internals/projects.md)
