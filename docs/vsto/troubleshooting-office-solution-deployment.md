---
title: Sorun giderme Office çözüm dağıtımı
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: de036ce9b0b566a6028b0ccfe45cfe5f2ac49da9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444940"
---
# <a name="troubleshoot-office-solution-deployment"></a>Sorun giderme Office çözüm dağıtımı
  Bu konu, Office çözümlerini dağıtırken karşılaşabileceğiniz sık karşılaşılan sorunları nasıl çözeceğiniz hakkında bilgiler içerir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Olay görüntüleyicisi kullanarak Office çözümlerini sorun giderme
 Office çözümlerini [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yüklediğinizde veya kaldırdığınızda yakalanan hata iletilerini görmek için Windows'daki olay görüntüleyicisini kullanabilirsiniz. Yükleme ve dağıtım sorunlarını çözmek için olay kaydedicisinden gelen bu iletileri kullanabilirsiniz. Daha fazla bilgi için [Office çözümleri için Etkinlik günlüğe bakın.](../vsto/event-logging-for-office-solutions.md)

## <a name="change-the-assembly-name-causes-conflicts"></a>Derleme adını değiştirme çakışmalara neden olur
 Bir çözüm dağıttıktan sonra **Proje Tasarımcısı'nın** **Uygulama** sayfasındaki **Derleme Adı** değerini değiştirirseniz, yayımlama araçları Kurulum paketini bir *Setup.exe* dosyası ve iki dağıtım bildirimi olacak şekilde değiştirir. İki bildirim dosyası dağıtırsanız, aşağıdaki koşullar oluşabilir:

- Son kullanıcı her iki sürümü de yüklerse, uygulama her iki VSTO Eklentisini de yükler.

- Derleme adı değiştirilmeden önce VSTO Eklentisi yüklenmişse, son kullanıcı hiçbir zaman güncelleştirme almaz.

  Bu koşullardan kaçınmak için, çözümü dağıttıktan sonra çözümün **Derleme Adı** değerini değiştirmeyin.

## <a name="check-for-updates-takes-a-long-time"></a>Güncelleştirmeleri denetleme uzun zaman alır
 Visual Studio 2010 Tools for Office çalışma zamanı, yöneticilerin bildirimleri ve çözümü indirmek için zaman çıkış değerini ayarlamak için kullanabilecekleri bir kayıt defteri girişi sağlar.

#### <a name="to-set-the-time-out-value"></a>Zaman çıkış değerini ayarlamak için

1. Kayıt defterinde aşağıdaki tuşa gidin:

     **HKEY_CURRENT_USER\Yazılım\Microsoft\VSTA**

2. **AddInTimeout** alt anahtarında, zaman çıkış değerini milisaniye cinsinden ayarlayın.

     **AddInTimeout** alt anahtarı yoksa, dword olarak oluşturun.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Ağ dosyası paylaşımını güncelleştiremez veya yayımlayamaz
 Bir ağ dosyası paylaşımında bulunan Office çözümleri, güncelleştirme yayımlanırken çözümün *Setup.exe* dosyası bir işlemde kilitliyse, güncelleştirmeler sırasında yanıltıcı bir ileti görüntüleyebilir. İleti şöyle olabilir: "Web'e 'setup.exe' ekleneme. 'setup.exe' dosyası bu Web'de zaten var."

 Dosya kilidini önlemeye yardımcı olmak için, paylaşımı son kullanıcılara salt okunur hale getirebilirsiniz. Ancak, belgeler paylaşımda varsa, son kullanıcılariçin salt okunur hale gelir.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Microsoft Office için ön koşullar yüklenmiyor
 .NET Framework, ve [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Office birincil interop derlemelerini Kurulum paketinize Office çözümünüzle birlikte dağıtılan ön koşullar olarak ekleyebilirsiniz. Birincil interop derlemelerinin nasıl yüklenir hakkında bilgi için bkz: [Office çözümleri geliştirmek için bir bilgisayarı yapılandırın](../vsto/configuring-a-computer-to-develop-office-solutions.md) ve Nasıl [Yüklenir: Office birincil interop derlemelerini yükleyin.](../vsto/how-to-install-office-primary-interop-assemblies.md)

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Localhost kullanarak yayımlama yükleme sorunlarına neden olabilir
 Belge düzeyindeki çözümler için yayımlama veya yükleme konumu olarak kullandığınızda, `http://localhost` **Yayımlama Sihirbazı** dizeyi gerçek bilgisayar adına dönüştürmez. Bu durumda, çözüm geliştirme bilgisayarına yüklenmesi gerekir. Dağıtılan çözümlerin geliştirme bilgisayarında IIS'yi kullanmasını sağlamak için, localhost yerine tüm HTTP/HTTPS/FTP konumları için tam nitelikli adı kullanın.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Önbelleğe alınmış derlemeler güncelleştirilmiş derlemeler yerine yüklenir
 Fusion, .NET Framework montaj yükleyici, proje çıktı yolu bir ağ dosyası paylaşımı üzerinde olduğunda derlemelerin önbelleğe alınmış kopyasını yükler, derleme güçlü bir adla imzalanır ve özelleştirme derleme sürümü değişmez. Bu koşulları karşılayan bir derlemeyi güncellerseniz, önbelleğe alınmış kopya yüklendiğinden, güncelleştirme projeyi çalıştırdığınızda görünmez.

 Visual Studio'yu, Fusion'ın proje her çalıştırıldığında derlemeleri karşıdan yükleyeceği şekilde yapılandırabilirsiniz.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Önbelleğe alınmış kopyaları yüklemek yerine derlemeleri indirmek için

1. Menü çubuğunda **Project**, _ProjectName_**Properties**'i seçin.

2. **Uygulama** **sayfasında, Montaj Bilgileri'ni**seçin.

3. **Derleme Sürümü'nün**revizyon numarasını, üçüncü alanını joker karaktere\*() ayarlayın. Örneğin, "1.0.*".  Ardından **Tamam** düğmesini seçin.

   Montaj sürümünü değiştirdikten sonra, derlemenizi güçlü bir adla imzalamaya devam edebilirsiniz ve Fusion özelleştirmenin en son sürümünü yükler.

 [!NOTE]
> Visual Studio 2017'den başlayarak, Assembly Version'da joker kartları kullanmayı denerseniz bir yapı hatası oluşur.  Bunun nedeni, montaj sürümündeki joker kartların MSBuild Deterministic özelliğini kıracak olmasıdır. Joker karakterleri montaj sürümünden kaldırmanız veya determinizmi devre dışı kaldırmanız talimatı verilir.  Deterministic özelliği hakkında daha fazla bilgi için bkz: [Ortak MSBuild proje özellikleri](../msbuild/common-msbuild-project-properties.md) ve [yapınızı özelleştirin](../msbuild/customize-your-build.md)

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>URI US-ASCII olmayan karakterlere sahip olduğunda yükleme başarısız olur
 Bir HTTP/HTTPS/FTP konumuna Office çözümü yayımladığınızda, yol US-ASCII'de olmayan Unicode karaktere sahip olamaz. Bu tür karakterler Kurulum programında tutarsız davranışlara neden olabilir. Yükleme yolu için US-ASCII karakterlerini kullanın.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Geliştirme bilgisayarında bir çözüm yayımladığınızda ve yüklediğinizde el ile kaldırma istemi görüntülenir
 Bir Office çözümü oluşturduğunuzda, yerleşik sürüm otomatik olarak kaydedilir. Aynı çözümü geliştirme bilgisayarınıza daha önce yayımladıysanız [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ve yüklediyseniz, çözüm bir sonraki oluşturulduktan, yeniden oluşturulduktan veya yayımlandıktan sonra yayımlanan sürümün ve yerleşik sürümün yükleme yolunun farklı olduğunu algılar. Hata iletisi diyor ki "özelleştirme yüklenemez, çünkü başka bir sürüm şu anda yüklü ve bu konumdan yükseltilemez." Bir çözüm yeniden oluşturulunca kayıt defteri anahtarları güncelleştirilir. Bu nedenle, yayımlamadan, hata ayıklamadan veya yeni sürümü çalıştırmadan önce önceki sürümü kaldırmanız gerekir.

 İletinin görünmesini önlemek için, dağıtımınızı sınamak için geliştirme bilgisayarınızda başka bir kullanıcı hesabı oluşturun. Alternatif olarak, çözümü yayımlamadan, hata ayıklamadan veya yeniden oluşturmadan önce sürümü bilgisayardaki yüklü programlar listesinden kaldırabilirsiniz.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Bir çözüm yüklediğinizde yakalanmayan özel durum veya yöntem bulunamadı hatası
 Dağıtım bildirimini *(.vsto* dosyası) açarak Office çözümlerini yüklediğinizde, Office uygulaması, belge veya çalışma kitabı, aşağıdaki koşullariçin hata iletileri görünebilir:

- Yöntem bulunamadı.

- Missingmethodexception.

- Yakalanmamış istisna.

  Bu hata iletilerini önlemek için Kurulum programını çalıştırarak çözümü yükleyin.

  Çözümü Kurulum programını çalıştırmadan yüklediğinizde, yükleyici ön koşulları denetlemez veya yüklemez. Kurulum programı önkoşulların doğru sürümünü denetler ve gerektiğinde yükler.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>InstallShield Limited Edition projesi yapıldıktan sonra Eklentiler için bildirim kayıt anahtarları değişir
 Bir VSTO Eklenti Kurulum programının parçası olan bildirim kayıt defteri anahtarı bazen installShield Limited Edition projesi oluşturduğunuzda *.vsto'dan* *.dll.manifest'e* değişir.

 Bu sorunu çözmek için InstallShield Limited Edition projesini farklı bir çözümde oluşturun veya VSTO Eklentisi'nin adını içeren kayıt defteri anahtarının değeri olarak CompanyName.AddinName'i kullanın.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Office çözümünüz için ClickOnce Installer birincil interop derlemelerini yüklemez
 Office çözümünüz için ClickOnce'nin oluşturduğu Kurulum programını çalıştırdığınızda, Office birincil interop derlemeleri (PI'ler) için yükleyici yalnızca hiçbir PiA zaten yüklü değilse çalışır.

 Kurulum programı PIA'ları doğru şekilde yüklemiyorsa, yükleme dizininden *o2007pia.msi* adlı yükleyici dosyasını çalıştırarak bunları el ile yükleyin.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Office çözümlerini yeniden yükleme, kapsama alanı dışında bir bağımsız değişkene neden olur
 Office çözümünün yeniden yüklendiğinde, aşağıdaki hata iletisiyle bir <xref:System.ArgumentOutOfRangeException> özel durum görünebilir: Belirtilen bağımsız değişken geçerli değerler aralığının dışındaydı.

 Yükleme konumu için URL'nin kasası farklıysa bu durum oluşur. Örneğin, bir Office `http://fabrikam.com/ExcelSolution.vsto` çözümlerini ilk kez yükledikten sonra ikinci `http://fabrikam.com/excelsolution.vsto` kez kullandıysanız, bu hata görüntülenir.

 İletinin görünmesini önlemek için Office çözümlerini yüklerken aynı kılıfı kullanın.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Web'den dağıtım bildirimini açarak ClickOnce çözümlerini yükleyemiyorum
 Kullanıcılar, dağıtım bildirimini web'den açarak Office çözümlerini yükleyebilir. Ancak, Internet Information Services (IIS) bazı yüklemeleri *.vsto* dosya adı uzantısını engeller. Office çözümlerini dağıtmak için kullanmadan önce IIS'deki MIME türünü tanımlamanız gerekir.

 IIS 7'de MIME türünü nasıl tanımlayacağım hakkında bilgi [için](https://technet.microsoft.com/library/cc725608(WS.10).aspx)bkz.

 Uzantıyı **.vsto** ve MIME türüne **uygulama/x-ms-vsto**olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Sorun Giderme ClickOnce dağıtımları](../deployment/troubleshooting-clickonce-deployments.md)
- [Office çözümlerini dağıtma](../vsto/deploying-an-office-solution.md)
