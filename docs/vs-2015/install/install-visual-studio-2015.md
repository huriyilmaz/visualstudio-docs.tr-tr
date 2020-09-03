---
title: Visual Studio 2015 'yi yükler | Microsoft Docs
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
ms.openlocfilehash: d593625985924d8c8076e1bdd361ce4d08c1dfbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548050"
---
# <a name="install-visual-studio-2015"></a>Visual Studio 2015'i Yükleme

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu sayfada, geliştiricilere yönelik tümleşik üretkenlik araçları takımımız **Visual Studio 2015**' i yüklemenize yardımcı olacak ayrıntılı bilgiler yer almaktadır. [Özellikler](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history), [sistem gereksinimleri](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs), [indirmeler](https://visualstudio.microsoft.com/vs/older-downloads/)ve daha fazlası hakkında daha hızlı bilgi edinmek için de bağlantılar sunuyoruz.

## <a name="quick-links"></a>Hızlı bağlantılar

Ayrıntılara tıklamadan önce, en sık istenen bağlantılarımızın bir listesi aşağıda verilmiştir.

|Başlık|Açıklama|
|------------------|----------------|
|![Visual Studio’yu indirin](../install/media/downloads.png "İndirmeler") |**İndirmeler**: Visual Studio 2015 ' i yüklemek için  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) sayfasından (abonelik gerekir) bir ürün yürütülebilir dosyası indirebilir veya paketlenmiş üründen yükleme medyasını kullanabilirsiniz. [Visual Studio 'nun güncel veya önceki sürümlerini indirme hakkında daha fazla bilgi edinin](https://www.visualstudio.com/vs/older-downloads/).|
|![Özellikler hakkında daha fazla bilgi edinin](../install/media/features.png "Özellikler") |**Özellikler**: Visual Studio 2015 ' deki özellikler hakkında daha fazla bilgi edinmek için bkz. [RTM](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [güncelleştirme 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), [güncelleştirme 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)ve [güncelleştirme 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs)için sürüm notları.|
|![Sistem gereksinimlerini görüntüleme](../install/media/system-requirements.png "Sistem Gereksinimleri") |**Sistem gereksinimleri**: her visual Studio 2015 sürümü için sistem gereksinimlerini görüntülemek üzere [Visual Studio 2015 Platform hedefleme ve uyumluluk](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) sayfasına bakın.|
|![Ürün anahtarınızı bulun](../install/media/product-keys.png "Ürün Anahtarları") |**Ürün anahtarları**: ürün anahtarınızı bulmak için bkz. [nasıl yapılır: Visual Studio ürün anahtarını bulma](../install/how-to-locate-the-visual-studio-product-key.md) konusu.|
|![Lisanslama hakkında bilgi edinin](../install/media/licensing.png "Lisanslama") |**Lisanslama**: hem bireyler hem de kurumsal müşterilerin lisanslama seçenekleri hakkında bilgi edinmek için bkz. [Visual Studio 2015 lisanslama teknik incelemesi](https://www.microsoft.com/download/details.aspx?id=13350).|

## <a name="default-vs-custom-setup"></a><a name="custom"></a> Varsayılan ve özel kurulum karşılaştırması
 Visual Studio 2015 ' i yüklerken, günlük olarak kullandığınız bileşenleri dahil edebilir veya dışlayabilirsiniz. Bu, varsayılan bir yüklemenin genellikle daha küçük olduğu ve özel bir yüklemeden daha hızlı yükleneceği anlamına gelir. Ayrıca, önceki sürümlerde varsayılan olarak yüklenen birçok bileşen, bu sürümde açıkça seçim yapmanız gereken özel bileşenler olarak değerlendirilir.

 ![Visual Studio 2015 Kurulum Iletişim kutusu](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Özel bileşenler Visual C++, Visual F#, SQL Server Veri Araçları, platformlar arası mobil araçlar ve SDK 'lar, üçüncü taraf SDK 'Ları ve uzantıları içerir. İlk kurulum sırasında bu bileşenleri seçmezseniz, daha sonra özel bileşenlerden herhangi birini yükleyebilirsiniz.

> [!NOTE]
> Özel bir yükleme, varsayılan yüklemede bulunan bileşenleri otomatik olarak içerir.

 Özel bileşenlerin tüm listesi aşağıdaki gibidir:

|Özellik kümeleri|Bileşenler|
|------------------|----------------|
|**Güncelleştirmeler**|Visual Studio 2015 Güncelleştirme 3|
|**Programlama dilleri**|Visual C++<br />Visual F#<br />Visual Studio için Python Araçları|
|**Windows ve Web geliştirme**|ClickOnce yayımlama araçları<br />LightSwitch<br />Microsoft Office Geliştirici Araçları<br />Microsoft SQL Server veri araçları<br /> Microsoft Web Geliştirici Araçları<br />PowerShell Tools for Visual Studio (3. taraf)<br />Silverlight geliştirme seti<br />Evrensel Windows uygulama geliştirme araçları<br />Windows 10 araçları ve SDK 'Ları<br />Windows 8.1 ve Windows Phone 8.0/8.1 araçları<br />Windows 8.1 araçları ve SDK 'lar|
|**Platformlar arası mobil geliştirme**|C#/.net (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />İOS/Android için mobil geliştirme Visual C++<br />Microsoft CodeGen ile Clang|
|**Ortak Araçlar ve yazılım geliştirme setleri**|Android yerel geliştirme seti (3. taraf)<br /> Android SDK [3. taraf]<br />Android SDK Kurulum API 'Leri (3. taraf)<br />Apache Ant (3. taraf)<br /> Java SE Development Kit (3. taraf)<br /> Joneent Node.js (3. taraf)|
|**Ortak Araçlar**|Windows için git (3. taraf)<br />Visual Studio için GitHub Uzantısı (3. taraf)<br /> Visual Studio Genişletilebilirlik Araçları|

## <a name="install-visual-studio"></a><a name="installing"></a> Visual Studio 'Yu yükler
 Visual Studio 'yu, [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) Web sitesinden Visual Studio abonelik hizmetinizi kullanarak, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/) Web sitesinden bir web yükleyicisi indirerek ya da çevrimdışı bir yükleme düzeni oluşturarak (daha fazla ayrıntı Için [Visual Studio 'nun çevrimdışı yüklemesini oluşturma](../install/create-an-offline-installation-of-visual-studio.md) sayfasına bakın) kullanarak yükleme medyasını kullanarak yükleyebilirsiniz.

> [!IMPORTANT]
> Yüklemek için yönetici kimlik bilgilerine ihtiyacınız vardır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Ancak, yükledikten sonra kullanmaları gerekmez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Yerel yönetici hesabınızda her şeyi Visual Studio 'ya yüklemek için aşağıdaki ayrıcalıklar etkinleştirilmiş olmalıdır.

|Yerel Ilke nesnesi görünen adı|Kullanıcı hakkı|
|--------------------------------------|----------------|
|Dosyaları ve dizinleri yedekleme|SeBackupPrivilege|
|Programların hatalarını ayıkla|SeDebugPrivilege|
|Denetim ve güvenlik günlüğünü yönetme|SeSecurityPrivilege|

 Bu yerel yönetici hesabı gereksinimi hakkında daha fazla bilgi için bkz. Bilgi Bankası makalesi, [Kurulum hesabı belirli kullanıcı haklarına sahip değilse SQL Server yükleme başarısız olur](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a> Yükleme medyasını kullanma
 Yükleme ortamındaki kök dizine yüklemek için, istediğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sürüm için yükleme dosyasını çalıştırın:

|Sürüm|Yükleme dosyası|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a> Ürün web sitesinden indir
 [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/) sayfasını ziyaret edin ve Istediğiniz Visual Studio sürümünü seçin.

### <a name="download-from-your-subscription-service"></a>Abonelik hizmetinizden indirin
 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) sayfasını ziyaret edin ve Istediğiniz Visual Studio sürümünü seçin.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a> Çevrimdışı yükleme düzeni oluşturma
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Yükleme medyanız yoksa veya bir Visual Studio aboneliğiniz yoksa veya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] web yükleyicisini kullanarak yüklemek istemiyorsanız, çevrimdışı yükleme düzeni olarak bilineni oluşturarak "bağlantısı kesilmiş" bir yükleme gerçekleştirebilirsiniz. Daha fazla bilgi için [Visual Studio 'Nun çevrimdışı yüklemesini oluşturma](../install/create-an-offline-installation-of-visual-studio.md) sayfasına bakın.

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a> Visual Studio 'Yu bir kuruluşta dağıtma
 Bir ağ üzerinden dağıtma hakkında daha [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fazla bilgi için bkz. [Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md).

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a> Visual Studio 'Yu sanallaştırılmış bir ortama yükler
 **Hyper-V ile ilgili video sorunları**

 Hyper-V ve hızlandırılmış grafik bağdaştırıcısının etkin olduğu Windows Server 2008 R2 çalıştırıyorsanız, sistemde yavaşlamalarla karşılaşabilirsiniz.

 Daha fazla bilgi için bkz. [Windows server 2008 veya Windows server 2008 R2 tabanlı bir bilgisayarda Hyper-V rolü etkinleştirilmişse ve hızlandırılmış bir görüntü bağdaştırıcısı yüklü olduğunda video performansı düşebilir](https://support.microsoft.com/kb/961661).

 **Hyper-V ile cihazları öykünmesi**

 Sanallaştırma olmadan Visual Studio 2015 ' i gerçek donanıma yüklediğinizde, Hyper-V ' n i kullanarak Windows ve Android cihazların öykünmesine olanak sağlayan Özellikler ' i seçebilirsiniz. Hyper-V ' d e yüklediğinizde, Windows veya Android cihazlarına öykünemeyeceksiniz. Bunun nedeni, öykünücülerin kendi sanal makinelerinden ve şu anda başka bir VM 'nin içinde bir VM barındırmanıza yönelik olur. Geçici çözüm, uygulamanızda doğrudan dağıtabileceğiniz ve hata ayıklayacağınız gerçek Windows veya Android cihazlara sahip olur.

## <a name="install-optional-components"></a><a name="optionalComponents"></a> İsteğe bağlı bileşenleri yükler
 Özgün yükleme sırasında seçmiş olabileceğiniz bileşenleri yüklemek istiyorsanız aşağıdaki yordamı kullanın.

#### <a name="to-install-optional-components"></a>İsteğe bağlı bileşenleri yüklemek için

1. **Denetim Masası**' nda, **Programlar ve Özellikler** sayfasında, bir veya daha fazla bileşen eklemek istediğiniz ürün sürümünü seçin ve ardından **Değiştir**' i seçin.

2. Kurulum sihirbazında, **Değiştir**' i seçin ve ardından yüklemek istediğiniz bileşenleri seçin.

3. **İleri**' yi seçin ve ardından kalan yönergeleri izleyin.

## <a name="install-offline-help-content"></a><a name="helpContent"></a> Çevrimdışı Yardım içeriğini yükler
 Yükledikten sonra [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , çevrimdışı kullanılabilir hale getirmek için ek yardım içeriğini indirebilirsiniz.

#### <a name="to-install-or-uninstall-help-content"></a>Yardım içeriğini yüklemek veya kaldırmak için

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Menü çubuğunda **Yardım**' ı, **Yardım içeriğini ekle ve Kaldır**' ı seçin.

2. **Microsoft Yardım Görüntüleyicisi** **Içeriği Yönet** sekmesinde yardım içeriğiniz için yükleme kaynağını seçin.

3. Belirli bir yardım koleksiyonu arıyorsanız, **arama** metin kutusuna ad veya anahtar sözcüğü girin ve ardından **ENTER**tuşuna basın.

4. İstediğiniz yardım koleksiyonunun adının yanındaki **Ekle** veya **Kaldır** bağlantısını seçin.

5. **Güncelleştir** düğmesine tıklayın.

   Çevrimdışı yardım 'ı yüklemek veya dağıtmak hakkında daha fazla bilgi için [Yardım Görüntüleyici Yönetici Kılavuzu](../ide/help-viewer-administrator-guide.md)' na bakın.

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a> Hizmet sürümlerini ve ürün güncelleştirmelerini denetleme
 Tüm uzantılar uyumlu olmadığından, önceki sürümlerden yükselttiğinizde Visual Studio uzantıları otomatik olarak yükseltmez. Uzantıları [Visual Studio Market](https://marketplace.visualstudio.com/) veya yazılım yayımcısından yeniden yüklemeniz gerekir.

#### <a name="to-automatically-check-for-service-releases"></a>Hizmet sürümlerini otomatik olarak denetlemek için

1. Menü çubuğunda **Araçlar**, **Seçenekler**' i seçin.

2. **Seçenekler** Iletişim kutusunda **ortam**' ı genişletin ve ardından **Uzantılar ve güncelleştirmeler**' i seçin. **Güncelleştirmeleri otomatik olarak denetle** onay kutusunun seçili olduğundan emin olun ve ardından **Tamam**' ı seçin.

## <a name="register-visual-studio"></a>Visual Studio 'Yu kaydetme

1. Menü çubuğunda **Yardım**' ı ve **hakkında**' yı seçin.

     **Hakkında** iletişim kutusunda ürün kimlik numarası (PID) gösterilir. Ürünün kaydedileceği PID ve Windows hesabı kimlik bilgileri (örneğin, hotmail veya Outlook.com e-posta adresi ve parola) gerekir.

2. Menü çubuğunda **Yardım**, **ürünü kaydet**' i seçin.

## <a name="repair-visual-studio"></a><a name="repair"></a> Visual Studio 'Yu onarma

#### <a name="to-repair-visual-studio"></a>Visual Studio'yu onarmak için

1. **Denetim Masası**' nda, **Programlar ve Özellikler** sayfasında, onarmak istediğiniz ürün sürümünü seçin ve ardından **Değiştir**' i seçin.

2. Kurulum sihirbazında, **Onar**' ı seçin, **İleri**' yi seçin ve ardından kalan yönergeleri izleyin.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Visual Studio 'Yu sessiz veya pasif modlarda onarmak için (diğer bir deyişle, kaynaktan onarmak için)

1. Visual Studio'nun yüklü olduğu bilgisayarda Windows komut istemini açın.

2. Aşağıdaki parametreleri girin:

     *DVDRoot* \\ < *Yükleme dosyası* \> \<`/quiet|/passive`> [/`norestart`]/`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a> Yükleme sorunlarını giderme
 Kurulum ve yükleme sorunları için yardım almak üzere bu kaynakları kullanın:

- [Visual Studio Kurulumu ve yükleme](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) Forumu. Visual Studio topluluğundaki diğer kişilerden gelen soruları ve yanıtları gözden geçirin. Aradığınızı bulamazsanız, kendi sorularınızı sorun.

- [Visual Studio ile ilgili yardım alın](https://visualstudio.microsoft.com/vs/support/vs2015/). Bilgi Bankası (KB) makalelerini bulun ve Visual Studio yüklemesiyle ilgili sorunlar hakkında bilgi edinmek için Microsoft Desteği nasıl başvureceğinizi öğrenin.

## <a name="related-topics"></a><a name="relatedTopics"></a> İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Çevrimdışı Visual Studio yüklemesi oluşturma](../install/create-an-offline-installation-of-visual-studio.md)|Internet 'e bağlı değilseniz, Visual Studio 'Nun nasıl yükleneceğini açıklar.
|[Visual Studio sürümlerini yan yana yükler](../install/install-visual-studio-versions-side-by-side.md)|Bir bilgisayara Visual Studio'nun birden fazla sürümünü yükleme hakkında bilgi sağlar.|
|[Visual Studio 'Yu yüklemek için komut satırı parametrelerini kullanma](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Visual Studio 'Yu bir komut isteminden yüklerken kullanabileceğiniz komut satırı parametrelerini listeler.|
|[Visual Studio'yu kaldırma](../install/uninstall-visual-studio.md)|Visual Studio 'Nun nasıl kaldırılacağını açıklar.|
|[Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md)|Visual Studio için dağıtım seçenekleri hakkında bilgi sağlar.|
|[Visual Studio Görüntü Kitaplığı](../designers/the-visual-studio-image-library.md)|Visual Studio uygulamalarında kullanabileceğiniz grafikleri yükleme hakkında bilgi sağlar.|
|[Visual Studio ile Geliştirmeye Başlama](../ide/get-started-developing-with-visual-studio.md)|Visual Studio 'Yu daha verimli bir şekilde kullanmanıza yardımcı olabilecek bilgiler ve bağlantılar içerir.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio'da Oturum Açma](../ide/signing-in-to-visual-studio.md)
