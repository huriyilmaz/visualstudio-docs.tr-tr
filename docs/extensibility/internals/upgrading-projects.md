---
title: Projeleri yükseltme | Microsoft Docs
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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848774"
---
# <a name="upgrading-projects"></a>Projeleri Yükseltme

Visual Studio 'nun bir sürümündeki proje modelinde yapılan değişiklikler, daha yeni sürümde çalıştırılabilmesi için projelerin ve çözümlerin yükseltilmesini gerektirebilir. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], kendi projelerinizde yükseltme desteğini uygulamak için kullanılabilen arabirimler sağlar.

## <a name="upgrade-strategies"></a>Yükseltme stratejileri

Bir yükseltmeyi desteklemek için, proje sistemi uygulamanızın bir yükseltme stratejisi tanımlayıp uygulaması gerekir. Stratejinizi belirlemek için yan yana (SxS) yedeklemeyi, kopya yedeklemesini veya her ikisini de desteklemeyi seçebilirsiniz.

- SxS yedekleme, bir projenin yalnızca yükseltilmesi gereken dosyaları, örneğin ". old" gibi uygun bir dosya adı sonekini ekleyerek kopyaladığını gösterir.

- Kopya yedekleme, bir projenin tüm proje öğelerini Kullanıcı tarafından belirtilen bir yedekleme konumuna kopyaladığı anlamına gelir. Özgün proje konumundaki ilgili dosyalar yükseltilir.

## <a name="how-upgrade-works"></a>Yükseltme nasıl Işe yarar?

Visual Studio 'nun önceki bir sürümünde oluşturulan bir çözüm daha yeni bir sürümde açıldığında IDE, yükseltilmesi gerekip gerekmediğini öğrenmek için çözüm dosyasını denetler. Yükseltme gerekliyse, yükseltme **Sihirbazı** , kullanıcıya yükseltme işlemi boyunca yol gösterecek şekilde otomatik olarak başlatılır.

Bir çözümün yükseltilmesi gerektiğinde, her proje fabrikasını yükseltme stratejisi için sorgular. Strateji, proje fabrikasının kopya yedeklemesini mi yoksa SxS yedeklemesini mi desteklediğini belirler. Bilgiler, yedekleme için gereken bilgileri toplayan ve Kullanıcı için geçerli seçenekleri sunan **Yükseltme Sihirbazına**gönderilir.

### <a name="multi-project-solutions"></a>Çoklu proje çözümleri

Bir çözüm birden çok proje içeriyorsa ve yükseltme stratejileri farklıysa (örneğin, yalnızca SxS yedeklemesini C++ destekleyen bir proje ve yalnızca kopya yedeklemesini destekleyen bir Web projesi gibi), proje fabrikaları yükseltme stratejisi üzerinde anlaşmalıdır.

Çözüm her proje fabrikasını <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>sorgular. Daha sonra, genel proje dosyalarının yükseltilmesi gerekip gerekmediğini görmek ve desteklenen yükseltme stratejilerini öğrenmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> çağırır. **Yükseltme Sihirbazı** daha sonra çağrılır.

Kullanıcı Sihirbazı tamamladıktan sonra, gerçek yükseltmeyi gerçekleştirmek için her proje fabrikası üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> çağırılır. Backup 'ı kolaylaştırmak için IVsProjectUpgradeViaFactory yöntemleri, yükseltme işleminin ayrıntılarını günlüğe kaydetmek için <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> hizmeti sağlar. Bu hizmet önbelleğe alınamaz.

Tüm ilgili genel dosyalar güncelleştirildikten sonra her proje fabrikası bir proje örneğini oluşturmayı seçebilirler. Proje uygulamasının <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>desteklemesi gerekir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> yöntemi daha sonra tüm ilgili proje öğelerini yükseltmek için çağırılır.

> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yöntemi Svsupgradegünlükçü hizmetini sağlamıyor. Bu hizmet <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>çağırarak elde edilebilir.

## <a name="best-practices"></a>En İyi Yöntemler

Düzenlemeden önce bir dosyayı düzenleyip düzenleyebiliyorsanız ve dosyayı kaydetmeden önce kaydetmek için <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> hizmetini kullanın. Bu, yedekleme ve yükseltme uygulamalarınızın, kaynak denetimi altındaki proje dosyalarını, yetersiz izinlere sahip dosyaları ve benzerlerini işlemesini yardımcı olur.

Tüm yedekleme aşamaları sırasında <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> hizmetini kullanın ve yükseltme işleminin başarısı veya başarısızlığı hakkında bilgi sağlamak için yükseltin.

Projeleri yedekleme ve yükseltme hakkında daha fazla bilgi için, vsshell2. IDL içindeki IVsProjectUpgrade için açıklamalara bakın.

## <a name="upgrading-custom-projects"></a>Özel projeleri yükseltme

Proje dosyasında kalıcı olan bilgileri ürününüzün farklı Visual Studio sürümleri arasında değiştirirseniz, proje dosyanızı eski sürümden yeni sürüme yükseltmeyi desteklemeniz gerekir. **Visual Studio dönüştürme sihirbazına**katılımını sağlayan yükseltmeyi desteklemek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimini uygulayın. Bu arabirim, kopyalama yükseltme için kullanılabilen tek mekanizmayı içerir. Projenin yükseltilmesi, çözümün bir parçası olarak gerçekleşir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi proje fabrikası tarafından uygulanır veya en azından proje fabrikasından bilgiler kişilerden olmalıdır.

<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> arabirimini kullanan eski mekanizma hala desteklenmektedir, ancak kavramsal olarak proje sistemini projenin bir parçası olarak yükseltir. Bu nedenle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi çağrılıp uygulanmış olsa bile <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> arabirimi Visual Studio ortamı tarafından çağırılır. Bu yaklaşım, yalnızca yükseltmenin ve proje bölümlerinin kopyasını uygulamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> kullanmanıza ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> arabirimine göre yerinde (muhtemelen yeni konumda) yapılacak işin geri kalanını devredebilir.

<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>örnek bir uygulama için bkz. [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Aşağıdaki senaryolar proje yükseltmeleri ile ortaya çıkar:

- Dosya projenin destekleyebileceğinden daha yeni bir biçimde ise, bunu belirten bir hata döndürmelidir. Bu, ürününüzün eski sürümünün sürümü denetlemek için kod içerdiğini varsayar.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yönteminde <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> bayrağı belirtilmişse, yükseltme, proje açılmadan önce yerinde yükseltme olarak uygulanır...

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yönteminde <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> bayrağı belirtilmişse, yükseltme bir kopya yükseltme olarak uygulanır.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> çağrısında <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrağı belirtilmişse, proje açıldıktan sonra, Kullanıcı ortam tarafından proje dosyasını yerinde yükseltme olarak yükseltmek için bir kullanıcı tarafından istenir. Örneğin, ortam, Kullanıcı çözümün eski bir sürümünü açtığında kullanıcıdan yükseltme yapmanızı ister.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> çağrısında <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrağı belirtilmemişse, kullanıcıdan proje dosyasını yükseltmesini istemelidir.

     Aşağıda örnek bir yükseltme istemi iletisi verilmiştir:

     "' %1 ' projesi, Visual Studio 'nun daha eski bir sürümüyle oluşturulmuş. Visual Studio 'nun bu sürümüyle açarsanız, Visual Studio 'nun eski sürümleriyle açamazsınız. Devam etmek ve bu projeyi açmak istiyor musunuz? "

### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory uygulamak için

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimi yöntemini, özellikle de proje fabrikası uygulamanızda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yöntemini uygulayın veya uygulamaları proje fabrikası uygulamanızdan çağrılabilir hale getirin.

2. Çözümün açılması kapsamında bir yerinde yükseltme yapmak istiyorsanız, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> uygulamanızda `VSPUVF_FLAGS` parametresi olarak bayrağını <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> sağlayın.

3. Çözümün açılması kapsamında bir yerinde yükseltme yapmak istiyorsanız, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> uygulamanızda `VSPUVF_FLAGS` parametresi olarak bayrağını <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> sağlayın.

4. 2 ve 3. adımlarda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>kullanarak gerçek dosya yükseltme adımları aşağıdaki "uygulama `IVsProjectUpgade`" bölümünde açıklandığı gibi uygulanabilir veya gerçek dosya yükseltmesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>atayabilirsiniz.

5. Visual Studio Geçiş Sihirbazı 'Nı kullanarak Kullanıcı için yükseltme ile ilgili iletileri göndermek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> yöntemlerini kullanın.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> arabirimi, proje yükseltmesinin bir parçası olarak gerçekleşmesi gereken her türlü dosya yükseltmesini uygulamak için kullanılır. Bu arabirim <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>'tan çağrılmaz, ancak proje sisteminin bir parçası olan dosyaları yükseltmek için bir mekanizma olarak sağlanır, ancak ana proje sistemi doğrudan farkında olmayabilir. Örneğin, derleyici ile ilgili dosyalar ve özellikler proje sisteminin geri kalanını işleyen geliştirme ekibi tarafından işlenmezse bu durum ortaya çıkabilir.

### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade uygulaması

Proje sisteminiz yalnızca <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uygularsa, **Visual Studio dönüştürme sihirbazına**katılamaz. Ancak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> arabirimini uygulasanız bile, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uygulamasına dosya yükseltmeyi de atayabilirsiniz.

#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade 'i uygulamak için

1. Bir Kullanıcı bir projeyi açmaya çalıştığında, proje açıldıktan sonra ve proje üzerinde diğer herhangi bir kullanıcı eylemi alınmadan önce <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> yöntemi ortam tarafından çağrılır. Kullanıcının çözümü yükseltmesi zaten isteniyorsa, <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrağı `grfUpgradeFlags` parametresine geçirilir. Kullanıcı bir projeyi doğrudan açarsa (örneğin, **var olan proje Ekle** komutunu kullanarak), <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrağı geçirilir ve projenin kullanıcıdan yükseltmesini istemek gerekir.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> çağrısına yanıt olarak proje, proje dosyasının yükseltilip yükseltilmediğini değerlendirmelidir. Projenin proje türünü yeni bir sürüme yükseltmesi gerekmiyorsa, yalnızca <xref:Microsoft.VisualStudio.VSConstants.S_OK> bayrağını döndürebilir.

3. Projenin proje türünü yeni bir sürüme yükseltmesi gerekiyorsa, proje dosyasının <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> yöntemi çağırarak ve `rgfQueryEdit` parametresi için bir <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> değeri geçirerek değiştirilip değiştirilemeyeceğini belirlemesi gerekir. Ardından projenin aşağıdakileri yapması gerekir:

    - `pfEditCanceled` parametresinde döndürülen `VSQueryEditResult` değeri <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>ise, proje dosyası yazılabildiğinden yükseltme devam edebilir.

    - `pfEditCanceled` parametresinde döndürülen `VSQueryEditResult` değeri <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> ve `VSQueryEditResult` değeri <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> bit kümesine sahipse, kullanıcıların izinleri sorunu çözmesi için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> hata döndürmelidir. Projenin ardından şunları yapması gerekir:

         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> çağırarak hatayı kullanıcıya bildirin ve <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> hata kodunu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>döndürün.

    - `VSQueryEditResult` değeri <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> ve `VSQueryEditResultFlags` değeri <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit kümesine sahipse, proje dosyası <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> çağırarak (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...) kullanıma alınmalıdır.

4. Proje dosyasındaki <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> çağrısı, dosyanın kullanıma alınmasını ve en son sürümü elde edilmesine neden olursa, proje kaldırılır ve yeniden yüklenir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> yöntemi, projenin başka bir örneği oluşturulduktan sonra yeniden çağrılır. Bu ikinci çağrıda, proje dosyası diske yazılabilir; Projenin bir önceki biçimde proje dosyasının bir kopyasını ile kaydetmesi önerilir. ESKI uzantı, gerekli yükseltme değişikliklerini yapın ve proje dosyasını yeni biçimde kaydedin. Yine, yükseltme işleminin herhangi bir bölümü başarısız olursa, yöntem <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>döndürerek hata olduğunu göstermelidir. Bu, projenin Çözüm Gezgini bellekten kaldırılmasına neden olur.

     <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> yöntemine yapılan çağrının (ReportOnly değerini belirterek) <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bayraklarını döndürdüğü durum için ortamda oluşan tamamlanmış işlemi anlamak önemlidir.

5. Kullanıcı proje dosyasını açmaya çalışır.

6. Ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> uygulamanızı çağırır.

7. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> `true`döndürürse, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> uygulamanızı çağırır.

8. Ortam, dosyayı açmak ve proje nesnesini başlatmak için <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> uygulamanızı çağırır, örneğin, Project1.

9. Ortam, proje dosyasının yükseltilmesi gerekip gerekmediğini öğrenmek için `IVsProjectUpgrade::UpgradeProject` uygulamanızı çağırır.

10. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> çağırın ve `rgfQueryEdit` parametresi için <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> değerini geçirin.

11. Ortam, `VSQueryEditResult` için <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> döndürür ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit `VSQueryEditResultFlags`olarak ayarlanır.

12. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uygulamanız `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>) çağırır.

Bu çağrı, proje dosyanızın yeni bir kopyasının kullanıma alınması ve en son sürümün alınması ve ayrıca proje dosyanızı yeniden yüklenmesi gereksinimini ortadan çıkarabilir. Bu noktada, iki işlemlerden biri gerçekleşir:

- Kendi proje yeniden yükleme uygulamanızı işlebiliyorsanız, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) uygulamanızı çağırır. Bu çağrıyı aldığınızda, projenizin ilk örneğini yeniden yükleyin (Project1) ve proje dosyanızı yükseltmeye devam edin. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) için `true` döndürürler, kendi proje yeniden yükleme uygulamanızı işleeceğinizi bilir.

- Kendi proje geri yüklemeyi işlemeyin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> için `false` (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) döndürün. Bu durumda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) önce, ortam projenizin yeni bir örneğini oluşturur, örneğin, Project2, aşağıdaki gibi.

    1. Ortam, Project1 ilk proje nesnesi üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> çağırır, bu nedenle bu nesneyi etkin olmayan duruma yerleştirir.

    2. Ortam, projenizin ikinci bir örneğini oluşturmak için `IVsProjectFactory::CreateProject` uygulamanızı çağırır, Project2.

    3. Ortam, dosyayı açmak ve Project2 ikinci proje nesnesini başlatmak için `IPersistFileFormat::Load` uygulamanızı çağırır.

    4. Ortam, proje nesnesinin yükseltilmesi gerekip gerekmediğini belirleyebilmek için ikinci bir kez `IVsProjectUpgrade::UpgradeProject` çağırır. Ancak bu çağrı, Project2 projesinin yeni, ikinci bir örneğinde yapılır. Bu, çözümde açılan projem.

        > [!NOTE]
        > İlk projenizin, Project1, etkin olmayan duruma yerleştirilmesi durumunda, ilk çağrıdan <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> uygulamanıza geri dönüş yapmanız gerekir.

    5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> çağırın ve `rgfQueryEdit` parametresi için <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> değerini geçirin.

    6. Ortam <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> döndürür ve proje dosyası yazılabildiğinden yükseltme devam edebilir.

Yükseltme işlemi başarısız olursa, `IVsProjectUpgrade::UpgradeProject`<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> döndürün. Yükseltme gerekmez veya yükseltmeyin ' i seçerseniz, `IVsProjectUpgrade::UpgradeProject` çağrısını op olarak değerlendirin. <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>döndürdüğünüzde projeniz için çözüme bir yer tutucu düğüm eklenir.

## <a name="upgrading-project-items"></a>Proje öğeleri yükseltiliyor

Uygulamadıysanız proje sistemleri içine öğe ekler veya bunları yönetiyorsanız, proje yükseltme işlemine katılmanız gerekebilir. Crystal Reports, proje sistemine eklenebilecek bir öğe örneğidir.

Genellikle proje öğesi uygulayıcıları, proje başvurularının ne olduğunu ve başka proje özelliklerinin yükseltme kararı vermek için ne olduğunu bilmeleri gerektiğinden, zaten tam olarak örneklenen ve yükseltilen bir projeden yararlanmak istiyor.

### <a name="to-get-the-project-upgrade-notification"></a>Proje yükseltme bildirimini almak için

1. Proje öğesi uygulamanızda <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> bayrağını ayarlayın (vsshell80. IDL içinde tanımlanmıştır). Bu, Visual Studio Kabuğu bir proje sisteminin yükseltme sürecinde olduğunu belirlediğinde, proje öğesi VSPackage 'ın otomatik olarak yüklenmesine neden olur.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> yöntemi aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> arabirimine tavsiye edin.

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> arabirimi, proje sistemi uygulamasının yükseltme işlemlerini tamamladıktan sonra yeni yükseltilen proje oluşturulduktan sonra tetiklenir. Senaryoya bağlı olarak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> yöntemlerinden sonra tetiklenir.

### <a name="to-upgrade-the-project-item-files"></a>Proje öğesi dosyalarını yükseltmek için

1. Dosya yedekleme sürecini proje öğesi uygulamanızda dikkatle yönetmeniz gerekir. Bu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yönteminin `fUpgradeFlag` parametresi <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>olarak ayarlandığı ve yedeklenen dosyaların ". old" olarak belirlenmiş olan arka dosyalar üzerinde yerleştirildiği bir yan yana yedekleme için özel olarak geçerlidir. Projenin yükseltilme sırasında sistem saatinden daha eski olan yedeklenen dosyalar eski olarak belirlenebilir. Ayrıca, bunu engellemek için özel adımlar yapmadığınız takdirde bunların üzerine yazılabilir.

2. Proje öğesi proje yükseltmesinin bir bildirimini aldığında, **Visual Studio Dönüştürme Sihirbazı** yine de görüntülenir. Bu nedenle, sihirbaz Kullanıcı arabirimine yükseltme iletileri sağlamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> arabiriminin yöntemlerini kullanmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler](../../extensibility/internals/projects.md)
