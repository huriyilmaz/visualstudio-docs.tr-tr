---
title: Visual Studio 2015 Yükle | Microsoft Dokümanlar
titleSuffix: ''
ms.date: 04/15/2020
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bfc573c30281e5bc976ee25ea3a80a2f874ab25
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445083"
---
# <a name="install-visual-studio-2015"></a>Visual Studio 2015'i Yükleme

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu sayfa, geliştiriciler için entegre üretkenlik araç paketimiz olan **Visual Studio 2015'i**yüklemenize yardımcı olacak ayrıntılı bilgiler içermektedir. Ayrıca, [özellikler,](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history) [sistem gereksinimleri,](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs) [indirmeler](https://visualstudio.microsoft.com/vs/older-downloads/)ve daha fazlası hakkında hızlı bir şekilde bilgi edinmeniz için bağlantılar da dahil ettik.

## <a name="quick-links"></a>Hızlı Linkler

Detaylara girmeden önce, en sık talep edilen bağlantılarımızın bir listesi aşağıda veda edebilirsiniz.

|||
|------------------|----------------|
|![Visual Studio’yu İndir](../install/media/downloads.png "İndirmeler") |**İndirmeler**: Visual Studio 2015'i yüklemek için [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) sayfasından bir ürün çalıştırılabilir dosya indirebilir (abonelik gereklidir) veya kutulu üründen yükleme ortamını kullanabilirsiniz. [Visual Studio'nun güncel veya önceki sürümlerini nasıl indirebilirsiniz hakkında daha fazla bilgi edinin.](https://www.visualstudio.com/vs/older-downloads/)|
|![Özellikler hakkında daha fazla bilgi edinin](../install/media/features.png "Özellikler") |**Özellikler**: Visual Studio 2015'teki özellikler hakkında daha fazla bilgi edinmek için [RTM,](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs) [Update 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), [Update 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)ve [Update 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs)için sürüm notlarına bakın.|
|![Sistem gereksinimlerini görüntüleme](../install/media/system-requirements.png "Sistem Gereksinimleri") |**Sistem Gereksinimleri**: Visual Studio 2015'in her sürümü için sistem gereksinimlerini görüntülemek için [Visual Studio 2015 Platform Hedefleme ve Uyumluluk](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) sayfasına bakın.|
|![Ürün Anahtarınızı Bulun](../install/media/product-keys.png "Ürün Anahtarları") |**Ürün Anahtarları**: Ürün anahtarınızı bulmak için [Nasıl Bulunur: Visual Studio Ürün Anahtarı](../install/how-to-locate-the-visual-studio-product-key.md) konusunu bulun.|
|![Lisanslama hakkında bilgi edinin](../install/media/licensing.png "Lisanslama") |**Lisanslama**: Hem bireyler hem de kurumsal müşteriler için lisans lama seçenekleri hakkında bilgi edinmek için [Visual Studio 2015 Lisanslama Teknik Raporu'na](https://www.microsoft.com/download/details.aspx?id=13350)bakın.|

## <a name="default-vs-custom-setup"></a><a name="custom"></a>Varsayılan ve Özel Kurulum
 Visual Studio 2015'i yüklediğinizde, günlük olarak kullanacağınız bileşenleri dahil edebilir veya hariç tutabilirsiniz. Bu, Varsayılan yüklemenin genellikle Özel yüklemeden daha küçük olacağı ve daha hızlı yüklenmesi anlamına gelir. Ayrıca, önceki sürümlerde varsayılan olarak yüklenen birçok bileşenin bu sürümde açıkça seçmeniz gereken Özel bileşenler olarak kabul edildiği anlamına gelir.

 ![Visual Studio 2015 Kurulum İletişim](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Özel bileşenler arasında Visual C++, Visual F#, SQL Server Data Tools, çapraz platform mobil araçları ve SDK'lar ile üçüncü taraf SDK'lar ve uzantılar yer almaktadır. İlk kurulum sırasında seçmezseniz, özel bileşenlerden herhangi birini daha sonra yükleyebilirsiniz.

> [!NOTE]
> Özel yükleme, Varsayılan yüklemede bulunan bileşenleri otomatik olarak içerir.

 Özel bileşenlerin tam listesi aşağıdaki gibidir:

|Özellik Setleri|Bileşenler|
|------------------|----------------|
|**Güncelleştirmeler**|Visual Studio 2015 Güncelleştirme 3|
|**Programlama Dilleri**|Visual C++<br />Visual F#<br />Visual Studio için Python Araçları|
|**Windows ve Web Geliştirme**|ClickOnce Yayımlama Araçları<br />LightSwitch<br />Microsoft Office Geliştirici Araçları<br />Microsoft SQL Server Veri Araçları<br /> Microsoft Web Geliştirici Araçları<br />Visual Studio için PowerShell Araçları (3. Parti)<br />Silverlight Geliştirme Kiti<br />Evrensel Windows Uygulama Geliştirme Araçları<br />Windows 10 Araçlar ve SDK'lar<br />Windows 8.1 ve Windows Phone 8.0/8.1 Araçları<br />Windows 8.1 Araçlar ve SDK'lar|
|**Çapraz Platform Mobil Geliştirme**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />iOS / Android için Görsel C++ Mobil Geliştirme<br />Microsoft CodeGen ile Clang|
|**Ortak Araçlar ve Yazılım Geliştirme Kitleri**|Android Yerli Geliştirme Kiti (3. Parti)<br /> Android SDK [3 Parti]<br />Android SDK Kurulum API'leri (3. Taraf)<br />Apaçi Karınca (3. Parti)<br /> Java SE Geliştirme Kiti (3. Parti)<br /> Joyent Node.js (3. Parti)|
|**Ortak Araçlar**|Windows için Git (3. Parti)<br />Visual Studio için GitHub Uzantısı (3. Parti)<br /> Visual Studio Genişletilebilirlik Araçları|

## <a name="install-visual-studio"></a><a name="installing"></a>Visual Studio'u Yükleyin
 Visual Studio'yu yükleme ortamını (DVD'ler) kullanarak, [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) web sitesinden Visual Studio abonelik hizmetinizi kullanarak, [Visual Studio İndirme web](https://visualstudio.microsoft.com/vs/older-downloads/) sitesinden bir web yükleyiciindirerek veya çevrimdışı yükleme düzeni oluşturarak (daha fazla ayrıntı için Çevrimdışı Görsel Stüdyo Kurulumu [Oluştur](../install/create-an-offline-installation-of-visual-studio.md) sayfasına bakın) yükleyebilirsiniz.

> [!IMPORTANT]
> Yüklemek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]için yönetici kimlik bilgilerine ihtiyacınız var. Ancak, yükledikten sonra bunları [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanmanız gerekmez.

 Yerel yönetici hesabınız, Visual Studio'da her şeyi yüklemek için aşağıdaki ayrıcalıklara sahip olmalıdır.

|Yerel İlke Nesne Görüntü Adı|Kullanıcı Hakkı|
|--------------------------------------|----------------|
|Yedekleme Dosyaları ve dizinleri|SeBackupAyrıcalık|
|Programların hatalarını ayıkla|SeDebugPrivilege|
|Denetim ve güvenlik günlüğünü yönetme|Sesecurityprivilege|

 Bu yerel yönetici hesap gereksinimi hakkında daha fazla bilgi için, Bilgi Bankası makalesine bakın, [Kurulum hesabı belirli kullanıcı haklarına sahip değilse SQL Server yüklemesi başarısız olur.](https://support.microsoft.com/kb/2000257)

### <a name="use-installation-media"></a><a name="BKMK_Media"></a>Yükleme ortamını kullanma
 Yükleme [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ortamının kök dizinine yüklemek için, yükleme dosyasını istediğiniz sürümün çalıştırın: [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

|Sürüm|Kurulum Dosyası|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a>Ürün web sitesinden indirin
 Visual [Studio İndirmeler](https://visualstudio.microsoft.com/vs/older-downloads/) sayfasını ziyaret edin ve Visual Studio'nun istediğiniz sürümünü seçin.

### <a name="download-from-your-subscription-service"></a>Abonelik hizmetinizden indirin
 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) sayfasını ziyaret edin ve Visual Studio'nun istediğiniz sürümünü seçin.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a>Çevrimdışı yükleme düzeni oluşturma
 Yükleme ortamınız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yoksa veya Visual Studio aboneliğiniz yoksa veya web yükleyicisini [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanarak yüklemek istemiyorsanız, çevrimdışı yükleme düzeni olarak bilinen düzeni oluşturarak "bağlantısıkesilmiş" bir yükleme gerçekleştirebilirsiniz. Daha fazla bilgi için [Visual Studio'nun Çevrimdışı Yüklemesi Oluştur](../install/create-an-offline-installation-of-visual-studio.md) sayfasına bakın.

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a>Visual Studio'yi bir kuruluşta dağıtın
 Ağ üzerinden nasıl [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dağıtılanın caydırığı hakkında bilgi için [Visual Studio Administrator Guide'a](../install/visual-studio-administrator-guide.md)bakın.

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a>Visual Studio'u sanallaştırılmış bir ortamda kurun
 **Hyper-V ile Video Sorunları**

 Hyper-V ve hızlandırılmış grafik bağdaştırıcısının etkin olduğu Windows Server 2008 R2 çalıştırıyorsanız, sistemde yavaşlamalarla karşılaşabilirsiniz.

 Daha fazla bilgi için bkz. Windows [Server 2008 veya Windows Server 2008 R2 tabanlı bir bilgisayarhyper-v rolünü etkinleştirdiğinde ve hızlandırılmış bir ekran bağdaştırıcısı yüklendiğinde Video performansı düşebilir.](https://support.microsoft.com/kb/961661)

 **Hyper-V'li Taklit Cihazlar**

 Visual Studio 2015'i sanallaştırma olmadan gerçek donanıma yüklediğinizde, Hyper-V kullanarak Windows ve Android cihazlarının öykünmesini sağlayan özellikleri seçebilirsiniz. Hyper-V'ye yüklediğinizde, Windows veya Android aygıtlarını taklit edemeyeceksiniz. Bunun nedeni, emülatöratörlerin kendilerinin sanal makineler olması ve şu anda başka bir VM'nin içinde vm barındıramaz olmasıdır. Geçici çözüm, uygulamanızı doğrudan dağıtabileceğiniz ve hata ayıklaabileceğiniz gerçek Windows veya Android aygıtlara sahip olmaktır.

## <a name="install-optional-components"></a><a name="optionalComponents"></a>İsteğe bağlı bileşenler yükleme
 Özgün yüklemeniz sırasında seçmediğiniz bileşenleri yüklemek istiyorsanız, aşağıdaki yordamı kullanın.

#### <a name="to-install-optional-components"></a>İsteğe bağlı bileşenleri yüklemek için

1. **Denetim Masası'nda,** Programlar ve **Özellikler** sayfasında, bir veya daha fazla bileşen eklemek istediğiniz ürün sürümünü seçin ve sonra **Değiştir'i**seçin.

2. Kurulum sihirbazında **Değiştir'i**seçin ve ardından yüklemek istediğiniz bileşenleri seçin.

3. **İleri'yi**seçin ve ardından kalan yönergeleri izleyin.

## <a name="install-offline-help-content"></a><a name="helpContent"></a>Çevrimdışı Yardım içeriğini yükleme
 Yükledikten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]sonra, çevrimdışı olarak kullanılabilecek şekilde ek Yardım içeriği indirebilirsiniz.

#### <a name="to-install-or-uninstall-help-content"></a>Yardım içeriğini yüklemek veya kaldırmak için

1. Menü [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çubuğunda **Yardım**, **Ekle ve Kaldır İçeriği'ni**seçin.

2. **Microsoft Yardım Görüntüleyicisi'nin** **İçeriği Yönet** sekmesinde, Yardım içeriğiniz için yükleme kaynağını seçin.

3. Belirli bir Yardım koleksiyonu arıyorsanız, **Arama** metin kutusuna adı veya anahtar kelimeyi girin ve ardından **Enter**tuşuna basın.

4. İstediğiniz Yardım koleksiyonunun adının yanında **Ekle** veya **Kaldır** bağlantısını seçin.

5. **Güncelleştir** düğmesini tıklatın.

   Çevrimdışı Yardım'ı yükleme veya dağıtma hakkında daha fazla bilgi için [Yardım Görüntüleyicisi Yönetici Kılavuzu'na](../ide/help-viewer-administrator-guide.md)bakın.

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a>Hizmet Bültenleri ve Ürün Güncelleştirmeleri için kontrol edin
 Tüm uzantılar uyumlu olmadığından, Önceki sürümlerden yükseltme yaptığınızda Visual Studio uzantıları otomatik olarak yükseltmez. [Visual Studio Marketplace'teki](https://marketplace.visualstudio.com/) veya yazılım yayıncısındaki uzantıları yeniden yüklemeniz gerekir.

#### <a name="to-automatically-check-for-service-releases"></a>Hizmet sürümlerini otomatik olarak denetlemek için

1. Menü çubuğunda **Araçlar**, **Seçenekler'i**seçin.

2. **Seçenekler** iletişim kutusunda, **Çevre'yi**genişletin ve ardından **Uzantılar ve Güncelleştirmeler'i**seçin. **Güncelleştirmeleri otomatik olarak onayla** onay kutusunun seçildiğinden emin olun ve ardından **Tamam'ı**seçin.

## <a name="register-visual-studio"></a>Kayıt Görsel Stüdyo

1. Menü çubuğunda **Yardım**, **Hakkında'yı**seçin.

     **Hakkında** iletişim kutusu ürün kimlik numarasını (PID) gösterir. Ürünü kaydetmek için PID ve Windows Hesabı kimlik bilgilerine (Hotmail veya Outlook.com e-posta adresi ve parola gibi) ihtiyacınız vardır.

2. Menü çubuğunda, **Ürüne Yardım**, **Ürün Kaydet'i**seçin.

## <a name="repair-visual-studio"></a><a name="repair"></a>Onarım Görsel Stüdyo

#### <a name="to-repair-visual-studio"></a>Visual Studio'yu onarmak için

1. **Denetim Masası'nda,** Programlar ve **Özellikler** sayfasında, onarmak istediğiniz ürün sürümünü seçin ve sonra **Değiştir'i**seçin.

2. Kurulum sihirbazında, **Onarım'ı**seçin, **İleri'yi**seçin ve ardından kalan yönergeleri izleyin.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Visual Studio'u sessiz veya pasif modlarda onarmak için (diğer bir deyişle kaynaktan onarmak için)

1. Visual Studio'nun yüklü olduğu bilgisayarda Windows komut istemini açın.

2. Aşağıdaki parametreleri girin:

     *DVDRoot* \\ < *Yükleme Dosyası* \> \< `/quiet|/passive` `norestart`> [/ ]/`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a>Yüklemenin sorun giderme
 Kurulum ve yükleme sorunları için yardım almak için bu kaynakları kullanın:

- [Visual Studio Kurulum ve Kurulum](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) forumu. Visual Studio topluluğundaki diğer kişilerden gelen soruları ve yanıtları gözden geçirin. Aradığınızı bulamazsanız, kendi sorularınızı sorun.

- [Visual Studio ile ilgili yardım alın.](https://visualstudio.microsoft.com/vs/support/vs2015/) Bilgi bankası (KB) makalelerini bulun ve Visual Studio yüklemesiyle ilgili sorunlar hakkında bilgi almak için Microsoft Destek'e nasıl başvurabileceğinizi öğrenin.

## <a name="related-topics"></a><a name="relatedTopics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Visual Studio'nun Çevrimdışı Yüklemesini Oluşturma](../install/create-an-offline-installation-of-visual-studio.md)|Internet'e bağlı değilken Visual Studio'nun nasıl yüklenirolduğunu açıklar.
|[Görsel Stüdyo Sürümlerini Yan Yana Yükleyin](../install/install-visual-studio-versions-side-by-side.md)|Bir bilgisayara Visual Studio'nun birden fazla sürümünü yükleme hakkında bilgi sağlar.|
|[Visual Studio'u Kurmak için Komut Satırı Parametrelerini Kullanın](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Visual Studio'yu komut isteminden yüklerken kullanabileceğiniz komut satırı parametrelerini listeler.|
|[Visual Studio'yu kaldırma](../install/uninstall-visual-studio.md)|Visual Studio'nun nasıl kaldırılabildiğini açıklar.|
|[Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md)|Visual Studio için dağıtım seçenekleri hakkında bilgi sağlar.|
|[The Visual Studio Image Library](../designers/the-visual-studio-image-library.md)|Visual Studio uygulamalarında kullanabileceğiniz grafikleri yükleme hakkında bilgi sağlar.|
|[Visual Studio ile Geliştirmeye Başlama](../ide/get-started-developing-with-visual-studio.md)|Visual Studio'u daha etkili kullanmanıza yardımcı olabilecek bilgiler ve bağlantılar içerir.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio'da Oturum Açma](../ide/signing-in-to-visual-studio.md)
