---
title: Projeleri Yükseltme | Microsoft Docs
description: Visual Studio SDK'sı tarafından projelerinize yükseltme desteği uygulamak için sağladığı arabirimler hakkında bilgi edinebilirsiniz.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158612"
---
# <a name="upgrading-projects"></a>Projeleri Yükseltme

Proje modelinin bir sürümünden sonraki Visual Studio sonraki sürüme yapılan değişiklikler, projelerin ve çözümlerin yeni sürümde çalışması için yükseltillerini gerekli olabilir. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], kendi projelerinize yükseltme desteği uygulamak için kullanılan arabirimler sağlar.

## <a name="upgrade-strategies"></a>Yükseltme Stratejileri

Bir yükseltmeyi desteklemek için proje sistemi uygulamanız bir yükseltme stratejisi tanımlamalı ve uygulamalı. Stratejinizi belirlerken yan yana (SxS) yedeklemeyi, kopyalama yedeklemesini veya her ikisini birden desteklemeyi seçebilirsiniz.

- SxS yedeklemesi, bir projenin yalnızca yerinde yükseltilmesi gereken dosyaları kopyalayarak uygun bir dosya adı soneki (örneğin, ".old" ) ekley anlamına gelir.

- Yedeklemeyi kopyalama, projenin tüm proje öğelerini kullanıcı tarafından sağlanan bir yedekleme konuma kopyalayıp kopyalaması anlamına gelir. Ardından özgün proje konumuyla ilgili dosyalar yükseltilir.

## <a name="how-upgrade-works"></a>Yükseltme Nasıl Çalışır?

IDE, Visual Studio önceki bir sürümünde oluşturulan bir çözüm daha yeni bir sürümde açıldığında, yükseltilecek olup olmadığını belirlemek için çözüm dosyasını denetler. Yükseltme gerekirse, yükseltme işlemi **boyunca kullanıcıya** yol etmek için Yükseltme Sihirbazı otomatik olarak başlatılır.

Bir çözümün yükseltilmesi gerekirken, her proje fabrikasını yükseltme stratejisi için sorgular. Strateji, proje fabrikasının kopyalama yedeklemesini mi yoksa SxS yedeklemesini mi desteklediğini belirler. Bilgiler, yedekleme için **gereken bilgileri** toplayan ve kullanıcıya uygun seçenekleri sunan Yükseltme Sihirbazı'nda gönderilir.

### <a name="multi-project-solutions"></a>Çoklu Project Çözümleri

Bir çözüm birden çok proje içeriyorsa ve yükseltme stratejileri farklı ise, örneğin yalnızca SxS yedeklemesini destekleyen bir C++ projesi ve yalnızca kopyalama yedeklemesini destekleyen bir Web projesi varsa, proje fabrikalarının yükseltme stratejisi üzerinde anlaşması gerekir.

Çözüm, için her proje fabrikasını <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> sorgular. Ardından, genel <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> proje dosyalarının yükseltilmesi gerek olup olmadığını görmek ve desteklenen yükseltme stratejilerini belirlemek için çağrısında bulundu. Ardından **Yükseltme Sihirbazı** çağrılır.

Kullanıcı sihirbazı tamamlandıktan sonra, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> gerçek yükseltmeyi gerçekleştirmek için her proje fabrikasında çağrılır. Yedeklemeyi kolaylaştırmak için IVsProjectUpgradeViaFactory yöntemleri, yükseltme işleminin ayrıntılarını <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> günlüğe alan hizmeti sağlar. Bu hizmet önbelleğe alınamaz.

Tüm ilgili genel dosyalar güncelleştirildikten sonra, her proje fabrikası bir projenin örneğini seçebilir. Proje uygulaması desteklemesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> gerekir. Ardından, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> tüm ilgili proje öğelerini yükseltmek için yöntemi çağrılır.

> [!NOTE]
> yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> SVsUpgradeLogger hizmetini sağlamaz. Bu hizmet çağrılarak elde <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> edilir.

## <a name="best-practices"></a>En İyi Uygulamalar

Hizmeti kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> dosyayı düzenlemeden önce düzenleyemezsiniz ve kaydetmeden önce kaydedebilirsiniz. Bu, yedekleme ve yükseltme uygulamalarınızı kaynak denetimi altında proje dosyalarını, yetersiz izinlere sahip dosyaları vb. işlemenize yardımcı olur.

Yükseltme <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> işleminin başarısı veya başarısızlığı hakkında bilgi sağlamak için yedekleme ve yükseltmenin tüm aşamaları sırasında hizmeti kullanın.

Projelerin geri yükleme ve yükseltme hakkında daha fazla bilgi için vsshell2.idl'de IVsProjectUpgrade'a yönelik açıklamalara bakın.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a> Özel Projeleri Yükseltme

Proje dosyasında kalıcı olan bilgileri, ürün Visual Studio farklı sürümler arasında değiştirirsanız, proje dosyanızı eski sürümden yeni sürüme yükseltmeyi desteklemeniz gerekir. Uygulama Dönüştürme Sihirbazı'na katılmanız için **yükseltmeyi Visual Studio arabirimini** <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> kullanın. Bu arabirim, kopyalama yükseltmesi için kullanılabilen tek mekanizmayı içerir. Projenin yükseltilmesi, çözümün bir parçası olarak açılır. Arabirim proje fabrikası tarafından uygulanır veya en azından proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> fabrikasından edinilebilir olması gerekir.

Arabirimi kullanan eski mekanizma hala destekleniyor ancak proje sistemini kavramsal olarak projenin bir parçası <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> olarak yükseltmektedir. Bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> nedenle, arabirim çağrılsa Visual Studio uygulansa bile <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> bu arabirim ortam tarafından çağrılır. Bu yaklaşım, yükseltmenin yalnızca kopya ve proje bölümlerini uygulamak ve arabirimi tarafından yerinde (muhtemelen yeni konumda) yapılacak geri kalan işi temsilci olarak uygulamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> kullanmanızı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> sağlar.

örnek uygulaması için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> bkz. [VSSDK Örnekleri.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

Aşağıdaki senaryolar proje yükseltmeleriyle ortaya çıkar:

- Dosya projenin destekleyeneden daha yeni bir biçimde ise, bunu belirten bir hata döndürür. Bu, ürününüzle ilgili eski sürümün, sürümü denetlemeye uygun kodlar içerir.

- yönteminde <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> bayrağı belirtilirse, yükseltme proje açılmadan önce yerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> yükseltme olarak uygulanır.

- yönteminde <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> bayrağı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> belirtilirse, yükseltme bir kopyalama yükseltmesi olarak uygulanır.

- Çağrıda bayrağı belirtilirse, proje açıldıktan sonra kullanıcıdan proje dosyasını yerinde yükseltmesi <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> istenir. Örneğin, kullanıcı çözümün eski bir sürümünü açtığında ortam kullanıcıdan yükseltmesi istenir.

- Çağrıda <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> bayrağı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> belirtilmemişse, kullanıcıdan proje dosyasını yükseltmesini girmeniz gerekir.

     Aşağıdaki örnek bir yükseltme istemi iletisidir:

     "'%1' projesi, '%1' projesinin eski bir sürümüyle Visual Studio. Bu sürümle açarsanız Visual Studio eski sürümlerle aça Visual Studio. Devam etmek ve bu projeyi açmak istiyor musunuz?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory uygulamak için

1. Arabirimin yöntemini, özellikle de proje fabrikası uygulamanıza yöntemini uygulama veya uygulamaları proje fabrika <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> uygulamanıza çağrılabilir hale getirdiniz.

2. Çözüm açma işleminin bir parçası olarak yerinde yükseltme yapmak için, uygulamanıza parametresi <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> olarak `VSPUVF_FLAGS` bayrağını <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> girin.

3. Çözüm açma işleminin bir parçası olarak yerinde yükseltme yapmak için, uygulamanıza parametresi <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> olarak `VSPUVF_FLAGS` bayrağını <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> girin.

4. 2. ve 3. adımlarda, kullanılarak gerçek dosya yükseltme adımları, aşağıdaki "Uygulama" bölümünde açıklandığı gibi gerçek dosya yükseltmesi için geçerli <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> `IVsProjectUpgade` <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> olabilir.

5. Geçiş Sihirbazı'nı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> kullanarak kullanıcıya yönelik yükseltmeyle ilgili iletileri göndermek için Visual Studio kullanın.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> arabirimi, proje yükseltmesi kapsamında yapılması gereken her tür dosya yükseltmesini uygulamak için kullanılır. Bu arabirim, 'den çağrılmasa da, proje sisteminin parçası olan dosyaları yükseltmek için bir mekanizma olarak sağlanır, ancak ana proje sistemi doğrudan <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> farkında değildir. Örneğin, derleyiciyle ilgili dosyalar ve özellikler proje sisteminin geri kalanını ele alan geliştirme ekibi tarafından işlanmazsa bu durum ortaya çıkabilir.

### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade Uygulaması

Proje sisteminiz yalnızca <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> uygulayıyorsa, Uygulama Dönüştürme **Sihirbazı'na Visual Studio kat değildir.** Ancak, arabirimini uygulaysanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> bile, dosya yükseltmeyi uygulamaya temsilci olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> devredebilirsiniz.

#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade uygulamak için

1. Kullanıcı bir projeyi açmayı denemesi, proje açıldıktan sonra ve proje üzerinde başka bir kullanıcı eylemi öncesinde ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> tarafından çağrılır. Kullanıcıdan çözümü yükseltmesi istenirse <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> parametresinde bayrağı `grfUpgradeFlags` geçirilebilir. Kullanıcı bir projeyi doğrudan açarsa (örneğin, Mevcut Project Ekle komutunu kullanarak) bayrağı geçirlanmaz ve projenin kullanıcıdan  <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> yükseltmesini istemsi gerekir.

2. Çağrıya yanıt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> olarak proje, proje dosyasının yükseltilip yükseltil olmadığını değerlendirmeli. Projenin proje türünü yeni bir sürüme yükseltmesi gerek yoksa, yalnızca bayrağını <xref:Microsoft.VisualStudio.VSConstants.S_OK> iade ediyor olabilir.

3. Projenin proje türünü yeni bir sürüme yükseltmesi gerekirse, yöntem çağrılarak ve parametresi için değeri geçerek proje dosyasının değiştirilebilir olup <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> olmadığını `rgfQueryEdit` belirlemesi gerekir. Projenin daha sonra şunları yapmaları gerekir:

    - parametresinde `VSQueryEditResult` döndürülen değer `pfEditCanceled` ise, proje dosyası <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> yazıldığı için yükseltme devam eder.

    - parametresinde döndürülen değer ise ve değer bit kümesine sahipse, kullanıcıların izin sorununu kendileri çözmesi gerektiği için başarısız `VSQueryEditResult` `pfEditCanceled` olması <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> `VSQueryEditResult` <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> gerekir. Proje daha sonra şunları gerçekleştirin:

         çağrısıyla hatayı kullanıcıya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> bildirin ve hata <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> kodunu 'a geri <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> döndürür.

    - Değer `VSQueryEditResult` ise ve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> değer bit `VSQueryEditResultFlags` ayarlanmışsa, proje dosyası ( , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ,...) <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits> çağrılarak kullanıma ,....

4. Proje dosyasındaki çağrı, dosyanın kullanıma alınıp en son sürümün alınıp alınıp alınmaysa proje kaldırılmış <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ve yeniden yüklenmiş olur. Projenin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> başka bir örneği oluşturulduktan sonra yöntemi yeniden çağrılır. Bu ikinci çağrıda proje dosyası diske yazabilirsiniz; Projenin, proje dosyasının bir kopyasını önceki biçimde bir ile kaydetmesi önerilir. OLD uzantısını kullanın, gerekli yükseltme değişikliklerini yapın ve proje dosyasını yeni biçimde kaydedin. Yeniden, yükseltme işleminin herhangi bir bölümü başarısız olursa, yöntemi döndürerek başarısız olduğunu <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> belirtmektedir. Bu, projenin yükleme sırasında kaldırılmış Çözüm Gezgini.

     yöntemine yapılan çağrının (ReportOnly değeri belirterek) ve bayraklarını döndüren durum için ortamda oluşan tüm işlemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> anlamak <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> önemlidir.

5. Kullanıcı proje dosyasını açmaya çalışır.

6. Ortam, uygulamanıza <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> çağrılar.

7. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> `true` döndürürse, ortam uygulamanızı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> arar.

8. Ortam, dosyayı <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> açmak ve proje nesnesini (örneğin, Project1) başlatmak için uygulamanızı arar.

9. Ortam, proje `IVsProjectUpgrade::UpgradeProject` dosyasının yükseltilecek olup olmadığını belirlemek için uygulamanızı arar.

10. çağrısında <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> bulundurarak parametresi için değerini <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> `rgfQueryEdit` iletirsiniz.

11. ortamı için <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> döndürür ve bit içinde `VSQueryEditResult` <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> `VSQueryEditResultFlags` ayarlanır.

12. Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> çağrıları ( , `IVsQueryEditQuerySave::QueryEditFiles` <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits> ).

Bu çağrı, proje dosyanızı yeni bir kopyasının kullanıma alınarak en son sürümün alınarak proje dosyanızı yeniden yükleme ihtiyacıyla sonuçlansa da olabilir. Bu noktada iki durumdan biri olur:

- Kendi proje yeniden yüklemenizi ele aldıysanız, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) uygulamanızı arar. Bu çağrıyı alırsanız projenizin ilk örneğini (Project1) yeniden yükleyin ve proje dosyanızı yükseltmeye devam eder. ortamı, () için geri dönersiniz kendi proje yeniden yüklemenizi `true` işleyebli <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> olduğunu <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload> bilir.

- Kendi projenizi yeniden yükleyebiliyorsanız () için `false` geri <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload> dönersiniz. Bu durumda , (QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) geri gelmeden önce, ortam projenizin başka bir yeni örneğini <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (örneğin, Project2) aşağıdaki gibi oluşturur:

    1. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> ilk proje nesneniz Olan Project1'i çağırarak bu nesneyi etkin olmayan durumuna yerleştirmenizi sağlar.

    2. Ortam, `IVsProjectFactory::CreateProject` projenizin ikinci bir örneğini (Project2) oluşturmak için uygulamanızı çağırmaktadır.

    3. Ortam, dosyayı `IPersistFileFormat::Load` açmak ve ikinci proje nesnesi Olan Project2'i başlatmak için uygulamanızı arar.

    4. Ortam, `IVsProjectUpgrade::UpgradeProject` proje nesnesinin yükseltilecek olup olmadığını belirlemek için ikinci kez çağrır. Ancak, bu çağrı projenin yeni, ikinci örneğinde (Project2) yapılır. Bu, çözümde açılan projedir.

        > [!NOTE]
        > İlk projenizin (Project1) etkin olmayan durumuna yerleştiril olduğu örnekte, uygulamanıza yapılan ilk <xref:Microsoft.VisualStudio.VSConstants.S_OK> çağrıdan dönmeniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> gerekir.

    5. çağrısında <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> bulundurarak parametresi için değerini <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> `rgfQueryEdit` iletirsiniz.

    6. Ortam geri <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> döner ve proje dosyası yazıldığı için yükseltme devam eder.

Yükseltme başarısız olursa, 'den <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> geri `IVsProjectUpgrade::UpgradeProject` dönersiniz. Yükseltme gerekli yoksa veya yükseltmeyi seçmezsiniz, `IVsProjectUpgrade::UpgradeProject` çağrıya bir no-op olarak davranın. geri <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> dönersiniz, projeniz için çözüme bir yer tutucu düğümü eklenir.

## <a name="upgrading-project-items"></a>Project Öğelerini Yükseltme

Uygulamadığınız proje sistemlerine öğe ekler veya yönetirsiniz, proje yükseltme sürecine katılmanız gerekir. Crystal Reports, proje sistemine eklen bir öğe örneğidir.

Genellikle, proje öğesi uygulayanlar yükseltme kararı almak için proje başvurularının ne olduğunu ve diğer proje özelliklerini bilmek zorunda olduğundan, zaten tamamen örneklenmiş ve yükseltilmiş bir projeden faydalanmalarını ister.

### <a name="to-get-the-project-upgrade-notification"></a>Proje yükseltme bildirimini almak için

1. Proje öğesi <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> uygulamanıza bayrağını (vsshell80.idl içinde tanımlanır) ayarlayın. Bu, Visual Studio kabuğu bir proje sisteminin yükseltme sürecinde olduğunu belirlerken proje öğenizin VSPackage'ın otomatik olarak yüklemesine neden olur.

2. yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> aracılığıyla arabirimini <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> önerin.

3. Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> proje sistemi uygulaması yükseltme işlemlerini tamamlandıktan ve yeni yükseltilen proje oluşturulduktan sonra oluşturulur. Senaryoya bağlı olarak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> arabirimi , <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> yöntemden sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> işten olur.

### <a name="to-upgrade-the-project-item-files"></a>Proje öğesi dosyalarını yükseltmek için

1. Proje öğesi uygulamanıza dosya yedekleme işlemini dikkatle yönetmeniz gerekir. Bu durum özellikle yöntemin parametresinin yedeklene dosyaların `fUpgradeFlag` <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> ".old" olarak belirlenen dosyaların yan yana yerleştiril olduğu olarak ayarlandırarak yan yana yedekleme <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> için geçerlidir. Projenin yükseltildikten sonra sistem zamanından daha eski yedekli dosyalar eski olarak belirlenilebilir. Ayrıca, bunu önlemek için belirli adımlar atmadıkça bunların üzerine yazılabilir.

2. Proje öğeniz proje yükseltme bildirimini alırken, Visual Studio **Dönüştürme Sihirbazı** görüntülenmeye devam ediyor. Bu nedenle, sihirbaz kullanıcı arabirimine yükseltme <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> iletileri sağlamak için arabiriminin yöntemlerini kullansanız iyi olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler](../../extensibility/internals/projects.md)
