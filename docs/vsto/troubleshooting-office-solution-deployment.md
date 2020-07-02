---
title: Office çözüm dağıtımı sorunlarını giderme
ms.date: 02/02/2017
ms.topic: troubleshooting
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 679a6e753e61ecb1af9097692a741c35e531c7cc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545749"
---
# <a name="troubleshoot-office-solution-deployment"></a>Office çözüm dağıtımı sorunlarını giderme
  Bu konu, Office çözümlerini dağıtırken karşılaşabileceğiniz yaygın sorunları çözme hakkında bilgi içerir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Olay Görüntüleyicisi 'ni kullanarak Office çözümlerinde sorun giderme
 Office çözümlerini yüklerken veya kaldırırken tarafından yakalanan hata iletilerini görmek için Windows 'daki Olay Görüntüleyicisi 'ni kullanabilirsiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Bu iletileri, yükleme ve dağıtım sorunlarını çözmek için olay günlükçüsü ' nden kullanabilirsiniz. Daha fazla bilgi için bkz. [Office çözümleri Için olay günlüğü](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Derleme adı değişikliği çakışmalara neden oluyor
 Zaten bir çözüm dağıttıktan sonra **Proje Tasarımcısı** 'nın **uygulama** sayfasında **derleme adı** değerini değiştirirseniz, yayımlama araçları, kurulum paketini bir *Setup.exe* dosyası ve iki dağıtım bildirimi olacak şekilde değiştirir. İki bildirim dosyası dağıtırsanız aşağıdaki koşullar oluşabilir:

- Son Kullanıcı her iki sürümü de yüklerse, uygulama hem VSTO Eklentilerini yükler.

- VSTO eklentisi, derleme adı değiştirilmeden önce yüklendiyse, Son Kullanıcı hiçbir şekilde güncelleştirme almaz.

  Bu koşulları önlemek için, çözümü dağıttıktan sonra çözümün **derleme adı** değerini değiştirmeyin.

## <a name="check-for-updates-takes-a-long-time"></a>Güncelleştirmelerin denetlenmesi uzun zaman alır
 Office çalışma zamanı için Visual Studio 2010 araçları, yöneticilerin bildirimleri ve çözümü indirmek için zaman aşımı değerini ayarlamak üzere kullanabileceği bir kayıt defteri girişi sağlar.

#### <a name="to-set-the-time-out-value"></a>Zaman aşımı değerini ayarlamak için

1. Kayıt defterinde aşağıdaki anahtara gidin:

     **HKEY_CURRENT_USER \Software\Microsoft\VSTA**

2. **AddInTimeout** alt anahtarında, zaman aşımı değerini milisaniye cinsinden ayarlayın.

     **AddInTimeout** alt anahtarı yoksa DWORD olarak oluşturun.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Bir ağ dosya paylaşımında güncelleştirilemez veya yayımlanamıyor
 Bir ağ dosya paylaşımında bulunan Office çözümleri, güncelleştirme yayımlandığında çözümün *Setup.exe* dosyası kilitliyse, güncelleştirmeler sırasında yanıltıcı bir ileti görüntüleyebilir. İleti şu şekilde görüntülenebilir: "' setup.exe ' Web 'e eklenemiyor. ' setup.exe ' dosyası bu Web 'de zaten var. "

 Dosya kilitlemeyi önlemeye yardımcı olmak için, paylaşımdan son kullanıcılara salt okunurdur. Ancak, belgeler paylaşımındaysa, son kullanıcılara da Salt okunabilir hale gelir.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Microsoft Office önkoşulları yüklenmedi
 .NET Framework, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ve Office birincil birlikte çalışma derlemelerini, Office çözümünüz ile dağıtılan ön koşullar olarak Kurulum paketinize ekleyebilirsiniz. Birincil birlikte çalışma derlemelerini nasıl yükleyeceğiniz hakkında bilgi için bkz. [Office çözümleri geliştirmek için bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md) ve [nasıl yapılır: Office birincil birlikte çalışma derlemelerini yüklemek](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Localhost kullanarak yayımla yükleme sorunlarına neden olabilir
 `http://localhost`Belge düzeyi çözümler için yayımlama veya yükleme konumu olarak kullandığınızda, **Yayımlama Sihirbazı** dizeyi gerçek bilgisayar adına dönüştürmez. Bu durumda, çözümün geliştirme bilgisayarında yüklü olması gerekir. Dağıtılan çözümlerin geliştirme bilgisayarında IIS kullanmasını sağlamak için, localhost yerine tüm HTTP/HTTPS/FTP konumları için tam nitelikli adı kullanın.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Güncelleştirilmiş derlemeler yerine önbelleğe alınmış derlemeler yüklenir
 Fusion, .NET Framework derleme yükleyicisi, proje çıkış yolu bir ağ dosya paylaşımında olduğunda, derleme bir tanımlayıcı ad ile imzalanmışsa ve özelleştirmenin derleme sürümü değişmezse, derlemelerin önbelleğe alınmış kopyasını yükler. Bu koşulları karşılayan bir derlemeyi güncelleştirirseniz, önbelleğe alınan kopya yüklendiği için projeyi bir sonraki çalıştırışınızda güncelleştirme görünmez.

 Visual Studio 'Yu Fusion 'un, projenin her çalıştırılışında derlemeleri indirecek şekilde yapılandırabilirsiniz.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Önbelleğe alınmış kopyaları yüklemek yerine derlemeleri indirmek için

1. Menü çubuğunda **Proje**, _ProjectName_**Özellikler**' i seçin.

2. **Uygulama** sayfasında, **derleme bilgileri**' ni seçin.

3. **Derleme sürümünün**Düzeltme numarasını, üçüncü alanını bir joker karakter () olarak ayarlayın \* . Örneğin, "1,0. *".  Ardından **Tamam** düğmesini seçin.

   Derleme sürümünü değiştirdikten sonra, derlemenizi tanımlayıcı bir adla imzalamaya devam edebilir ve Fusion özelleştirmenin en son sürümünü yükler.

 [!NOTE]
> Visual Studio 2017 ile başlayarak, derleme sürümünde joker karakter kullanmayı denerseniz bir yapı hatası oluşur.  Bunun nedeni, derleme sürümündeki joker kartların MSBuild belirleyici özelliğini bozacaktır. Bütünleştirilmiş kodu derleme sürümünden kaldırmanız veya determinronizi devre dışı bırakmanız istenir.  Belirleyici özelliği hakkında daha fazla bilgi edinmek için bkz. [Ortak MSBuild proje özellikleri](../msbuild/common-msbuild-project-properties.md) ve [yapınızı özelleştirme](../msbuild/customize-your-build.md)

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>URI, US-ASCII olmayan karakterler olduğunda yükleme başarısız olur
 Bir Office çözümünü bir HTTP/HTTPS/FTP konumuna yayımladığınızda, yolun US-ASCII içinde olmayan Unicode karakterleri olamaz. Bu karakterler, Kurulum programında tutarsız davranışa neden olabilir. Yükleme yolu için US-ASCII karakterlerini kullanın.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Geliştirme bilgisayarında bir çözüm yayımladığınızda ve yüklediğinizde el ile kaldırma istemi görüntülenir
 Office çözümü oluşturduğunuzda, oluşturulan sürüm otomatik olarak kaydedilir. Daha önce geliştirme bilgisayarınızda aynı çözümü yayımladıysanız ve yüklediyseniz, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yayımlanan sürüm ve yerleşik sürümün yükleme yolunun, çözümün bir sonraki derlenme, yeniden oluşturulması veya yayımlandıktan sonra farklı olduğunu algılar. Hata iletisi "Şu anda başka bir sürüm yüklü olduğundan ve bu konumdan yükseltilemediğinden özelleştirme yüklenemiyor." ifadesini belirtir. Kayıt defteri anahtarları her bir çözüm yeniden oluşturulduğunda güncelleştirilir. Bu nedenle, yeni sürümü yayımlamadan, ayıklamadan veya çalıştırmadan önce önceki sürümü kaldırmanız gerekir.

 İletinin görünmesini engellemek için, dağıtımınızı test etmek üzere geliştirme bilgisayarınızda başka bir kullanıcı hesabı oluşturun. Alternatif olarak, çözümü bir sonraki yayımlamadan, hata ayıklamanıza veya yeniden oluşturmadan önce bilgisayardaki yüklü programlar listesinden kaldırabilirsiniz.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Bir çözüm yüklerken yakalanamayan özel durum veya yöntem bulunamadı hatası
 Dağıtım bildirimini (bir *. VSTO* dosyası), Office uygulamasını, belgeyi veya çalışma kitabını açarak Office çözümlerini yüklediğinizde aşağıdaki koşullara ilişkin hata iletileri görünebilir:

- Yöntem bulunamadı.

- MissingMethodException.

- Yakalanamayan özel durum.

  Bu hata iletilerini engellemek için Kurulum programını çalıştırarak çözümü yükleme.

  Çözümü, Kurulum programını çalıştırmadan yüklediğinizde, yükleyici önkoşulları denetlemez veya yüklemez. Kurulum programı, önkoşulların doğru sürümünü denetler ve gerektiğinde bunları kurar.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Bir InstallShield Limited Edition projesi derlendikten sonra eklenti için bildirim kayıt defteri anahtarları değişir
 Bir bir InstallShield Limited Edition projesi oluşturduğunuzda, bir VSTO eklentisi kurulum programının parçası olan bildirim kayıt defteri anahtarı bazen *. VSTO* 'dan *. dll. manifest* ' den değişir.

 Bu sorunu geçici olarak çözmek için, farklı bir çözümde InstallShield Limited Edition projesini oluşturun veya VSTO eklentisinin adını içeren kayıt defteri anahtarının değeri olarak CompanyName. AddInName ' i kullanın.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Office çözümünüz için ClickOnce yükleyicisi, birincil birlikte çalışma derlemelerini yüklemez
 Office çözümünüz için ClickOnce tarafından oluşturulan Kurulum programını çalıştırdığınızda, Office birincil birlikte çalışma derlemeleri (PIA 'lar) için yükleyici yalnızca bir PIA yüklü değilse çalışır.

 Kurulum programı PIA 'Ları doğru şekilde yüklememezse, yükleme dizininden *o2007pia.msi* adlı yükleyici dosyasını çalıştırarak onları el ile yükleyebilirsiniz.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Office çözümlerini yeniden yükleme, bağımsız değişkenin Aralık dışında olmasına neden olur
 Bir Office çözümünü yeniden yüklediğinizde, <xref:System.ArgumentOutOfRangeException> Şu hata iletisiyle bir özel durum görünebilir: belirtilen bağımsız değişken geçerli değerler aralığının dışındaydı.

 Bu durum, yükleme konumunun URL 'sinin büyük küçük harfleri farklıysa oluşur. Örneğin, bir Office çözümünü `http://fabrikam.com/ExcelSolution.vsto` ilk kez yüklediyseniz ve sonra ikinci kez kullandıysanız bu hata görüntülenir `http://fabrikam.com/excelsolution.vsto` .

 İletinin görünmesini engellemek için, Office çözümlerini yüklerken aynı büyük küçük harf kullanın.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Web 'den dağıtım bildirimini açarak bir ClickOnce çözümü yüklenemez
 Kullanıcılar, Web 'den dağıtım bildirimini açarak Office çözümlerini yükleyebilir. Ancak, bazı Internet Information Services yüklemeleri (IIS) *. VSTO* dosya adı uzantısını engeller. Bir Office çözümünü dağıtmak üzere kullanmadan önce MIME türünü IIS 'de tanımlamanız gerekir.

 IIS 7 ' de MIME türü tanımlama hakkında daha fazla bilgi için bkz. [MIME türü ekleme (IIS7)](https://technet.microsoft.com/library/cc725608(WS.10).aspx).

 Uzantıyı **. VSTO** ve MIME türü olarak **Application/x-MS-VSTO**olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
