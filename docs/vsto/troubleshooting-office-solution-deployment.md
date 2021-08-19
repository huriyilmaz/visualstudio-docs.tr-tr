---
title: Çözüm Office sorunlarını giderme
description: Uygulama çözümleri dağıtırken karşılaş olabileceğiniz yaygın sorunları nasıl çöz Office öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 04b743d6d2a258bb117b01bc9f7d27bc7f4b7978
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147758"
---
# <a name="troubleshoot-office-solution-deployment"></a>Çözüm Office sorunlarını giderme
  Bu konu, dağıtım sırasında karşılaş olabileceğiniz yaygın sorunları çözme hakkında bilgi Office içerir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Olay Office kullanarak çözüm sorunlarını giderme
 çözümlerini yükley veya kaldırdığınız Windows tarafından yakalanan hata iletilerini görmek için olay görüntüleyicisini Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] kullanabilirsiniz. Yükleme ve dağıtım sorunlarını çözmek için olay günlükleyiciden bu iletileri kullanabilirsiniz. Daha fazla bilgi için [bkz. Çözüm için Office günlüğü.](../vsto/event-logging-for-office-solutions.md)

## <a name="change-the-assembly-name-causes-conflicts"></a>Derleme adını değiştirme çakışmalara neden oluyor
 Bir çözümü **dağıttıktan** sonra  **Project Tasarımcısı'nın** Uygulama sayfasında Derleme Adı değerini değiştirirsanız, yayımlama araçları Kurulum paketini tek birSetup.exedosyası ve iki dağıtım bildirimi *olacak şekilde* değiştirir. İki bildirim dosyası dağıtırsanız aşağıdaki koşullar oluşabilir:

- Son kullanıcı her iki sürümü de yüklemişse, uygulama her iki sürümü de VSTO yüklenir.

- Derleme VSTO önce eklenti yüklendiyse, son kullanıcı hiçbir zaman güncelleştirmeleri almaz.

  Bu koşulları önlemek için çözümü dağıtın sonra çözümün **Derleme** Adı değerini değiştirme.

## <a name="check-for-updates-takes-a-long-time"></a>Güncelleştirmeleri denetleme uzun zaman alır
 Visual Studio için 2010 Araçları Office çalışma zamanı, yöneticilerin bildirimleri ve çözümü indirmek için zaman out değerini ayarlamak üzere kullanabileceği bir kayıt defteri girdisi sağlar.

#### <a name="to-set-the-time-out-value"></a>Zaman out değerini ayarlamak için

1. Kayıt defterinde aşağıdaki anahtara gidin:

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. **AddInTimeout alt** anahtarında zaman aşımı değerini milisaniye cinsinden ayarlayın.

     **AddInTimeout** alt anahtarı yoksa DWORD olarak oluşturun.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Ağ dosya paylaşımı güncelleştirilamıyor veya yayımlanaamıyor
 Office dosya paylaşımında yer alan tüm çözüm çözümleri, güncelleştirme yayımlanırken çözümünSetup.exebir işlemde kilitlenirse güncelleştirmeler sırasında yanıltıcı bir ileti görüntüsüne neden olabilir.  İleti şöyle olabilir: "Web'e 'setup.exe' eksildi. 'setup.exe' dosyası bu Web'de zaten var."

 Dosya kilitlemeyi önlemeye yardımcı olmak için paylaşımı son kullanıcılara salt okunur hale ebilirsiniz. Ancak, belgeler paylaşımda ise son kullanıcılar için salt okunur hale de gelecektir.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Microsoft Office önkoşulları yüklü değil
 .NET Framework, ve Office birincil birlikte çalışma derlemelerini, Office çözümünüzle birlikte dağıtılan önkoşullar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] olarak Kurulum paketinize Office abilirsiniz. Birincil birlikte çalışma derlemelerini yükleme hakkında bilgi için, [bkz.](../vsto/configuring-a-computer-to-develop-office-solutions.md) Bir bilgisayarı Office geliştirmesi için yapılandırma ve Nasıl Office birlikte çalışma [derlemeleri yükleme.](../vsto/how-to-install-office-primary-interop-assemblies.md)

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Localhost kullanarak yayımlama yükleme sorunlarına neden olabilir
 Belge düzeyi çözümler için yayımlama veya yükleme konumu olarak kullanırsanız, Yayımlama Sihirbazı dizeyi `http://localhost` gerçek bilgisayar adına dönüştürmez.  Bu durumda, çözümün geliştirme bilgisayarına yüklenmiş olması gerekir. Dağıtılan çözümlerin geliştirme bilgisayarda IIS kullanmalarını yapmak için localhost yerine tüm HTTP/HTTPS/FTP konumlarının tam adını kullanın.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Önbelleğe alınan derlemeler güncelleştirilmiş derlemeler yerine yüklenir
 .NET Framework derleme yükleyicisi Fusion, proje çıkış yolu bir ağ dosya paylaşımında olduğunda, derlemenin güçlü bir adla imzalandı ve özelleştirmenin derleme sürümü değişmeden derlemelerin önbelleğe alınmış kopyasını yükler. Bu koşulları karşılayacak bir derlemeyi güncelleştirecek olursanız, önbelleğe alınmış kopya yüklendiğinden projeyi bir sonraki çalıştırmada güncelleştirme görünmez.

 Proje her Visual Studio Fusion'ın derlemeleri indirecek şekilde yapılandırmayı yapılandırabilirsiniz.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Önbelleğe alınmış kopyaları yüklemek yerine derlemeleri indirmek için

1. Menü çubuğunda , _ProjectName_ **Project** seçeneğini **belirleyin.**

2. Uygulama sayfasında **Derleme** **Bilgileri'ne tıklayın.**

3. Derleme Sürümünün üçüncü alanı olan düzeltme **numarasını joker** karakter ( ) olarak \* ayarlayın. Örneğin, "1.0.*".  Ardından Tamam **düğmesini** seçin.

   Derleme sürümünü değiştirdikten sonra derlemenizi güçlü bir adla imzalamaya devam edersiniz ve Fusion özelleştirmenin en son sürümünü yükler.

 [!NOTE]
> 2017'Visual Studio başlayarak Derleme Sürümünde joker karakter kullanmayı denersiniz derleme hatası oluşur.  Bunun nedeni, derleme sürümündeki joker kartların Belirleyici özelliği MSBuild bozmasıdır. Joker karakterleri derleme sürümünden kaldırmanız veya belirlenme özelliğini devre dışı bırakmanız gerekir.  Belirlenimci özellik hakkında daha fazla bilgi edinmek için bkz. [Ortak MSBuild proje özellikleri ve](../msbuild/common-msbuild-project-properties.md) [Derlemenizi özelleştirme](../msbuild/customize-your-build.md)

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>URI'de US-ASCII olmayan karakterler olduğunda yükleme başarısız oluyor
 Http/HTTPS/FTP Office bir çözüm yayımlarken, yol US-ASCII'de olmayan Unicode karakterlerine sahip olamaz. Bu tür karakterler Kurulum programında tutarsız davranışlara neden olabilir. Yükleme yolu için US-ASCII karakterlerini kullanın.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Geliştirme bilgisayarına bir çözüm yayımlar ve yüklenirken el ile kaldırma istemi görüntülenir
 Yeni bir çözüm Office, yerleşik sürüm otomatik olarak kaydedilir. Daha önce aynı çözümü geliştirme bilgisayarınıza yayımladıktan ve yükledikten sonra, çözüm bir sonraki oluşturulduktan, yeniden oluşturulduktan veya yayımlandıktan sonra yayımlanan sürüm ve yerleşik sürüm için yükleme yolunun farklı [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] olduğunu algılar. Hata iletisi "başka bir sürüm şu anda yüklü olduğundan ve bu konumdan yükseltilemediklerinden özelleştirme yükilemiyor". Bir çözüm yeniden güncelleştirilirken kayıt defteri anahtarları güncelleştirilir. Bu nedenle, yeni sürümü yayımlamadan, hata ayıklamadan veya çalıştırmadan önce önceki sürümü kaldırmanız gerekir.

 İletinin görünmesini önlemek için dağıtımınızı test etmek için geliştirme bilgisayarınızda başka bir kullanıcı hesabı oluşturun. Alternatif olarak, bir sonraki çözümü yayımlamadan, hata ayıklamadan veya yeniden oluşturmadan önce, sürümü bilgisayarda yüklü programlar listesinden kaldırabilirsiniz.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Çözüm yüklenirken yakalanmayan özel durum veya yöntem bulunamadı hatası
 Dağıtım bildirimini Office *(bir .vsto* dosyası), Office uygulaması, belgesi veya çalışma kitabı açarak bir çözüm ekleyebilirsiniz; aşağıdaki koşullar için hata iletileri görünebilir:

- Yöntem bulunamadı.

- Missingmethodexception.

- Yakalanmayan özel durum.

  Bu hata iletilerini önlemek için Kurulum programını çalıştırarak çözümü yükleyin.

  Kurulum programını çalıştırmadan çözümü yükleyebilirsiniz, yükleyici önkoşulları denetlemez veya yüklemez. Kurulum programı, önkoşulların doğru sürümünü denetler ve gerektiğinde bunları yüklür.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>InstallShield Limited Edition projesi hazır olduktan sonra Eklentiler için bildirim kayıt defteri anahtarları değişir
 VSTO Eklenti Kurulum programının parçası olan bildirim kayıt defteri anahtarı, bir InstallShield Limited Edition projesi derlemeniz sırasında *bazen .vsto'dan* *.dll.manifest'a* değişir.

 Bu sorunu gidermek için farklı bir çözümde InstallShield Limited Edition projesini oluşturun veya VSTO Eklentisini içeren kayıt defteri anahtarının değeri olarak CompanyName.AddinName kullanın.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>ClickOnce çözümünüz için Office Yükleyicisi birincil birlikte çalışma derlemelerini yüklemez
 Office çözümünüz için ClickOnce Kurulum programını çalıştırırken, Office birincil birlikte çalışma derlemeleri (PIA) yükleyicisi yalnızca piA'lar zaten yüklüyse çalışır.

 Kurulum programı PIA'ları doğru yüklemezse, yükleme dizinindeno2007pia.msiyükleyici dosyasını *çalıştırarak* el ile yükleyin.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Çözüm Office yeniden yüklemek, bağımsız değişkenin aralık dışında özel durumuna neden oluyor
 Bir çözüm Office, şu hata iletisiyle birlikte bir özel durum görünebilir: Belirtilen bağımsız değişken geçerli <xref:System.ArgumentOutOfRangeException> değer aralığının dışındaydı.

 Bu durum, yükleme konumunun URL'sinin büyük/ Örneğin, ilk kez bir Office ve ardından ikinci kez `http://fabrikam.com/ExcelSolution.vsto` kullandıysanız bu `http://fabrikam.com/excelsolution.vsto` hata görüntülenir.

 İletinin görünmesini önlemek için, aşağıdaki çözümleri yükleyen aynı büyük/Office kullanın.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Web'den ClickOnce bildirimi açarak bir çözüm yük ola
 Kullanıcılar, Office bildirimini web'den açarak farklı çözümler yükleyebilir. Ancak, bazı Internet Information Services (IIS) *yüklemeleri .vsto dosya adı* uzantısını engelleyebilir. MiME türünü bir çözüm dağıtmak için kullanmadan önce IIS'de tanımlamanız Office gerekir.

 IIS 7'de MIME türünü tanımlama hakkında bilgi için bkz. [MIME Türü Ekleme (IIS7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725608(v=ws.10)).

 Uzantıyı **.vsto ve** MIME türünü **application/x-ms-vsto olarak ayarlayın.**

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
- [Visual Studio giderme](/troubleshoot/visualstudio/welcome-visual-studio/)