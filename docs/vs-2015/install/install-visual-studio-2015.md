---
title: Visual Studio 2015'i yükleyin | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: a31bc328c20aada21b05edeef61886d57e914165
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298054"
---
# <a name="install-visual-studio-2015"></a>Visual Studio 2015'i yükleyin

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu sayfada, geliştiricilere yönelik tümleşik üretkenlik araçları takımımız **Visual Studio 2015**' i yüklemenize yardımcı olacak ayrıntılı bilgiler yer almaktadır. [Özellikler](https://www.visualstudio.com/news/vs2015-vs.aspx), [sürümler](https://go.microsoft.com/fwlink/?LinkID=242142), [sistem gereksinimleri](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [indirmeler](https://go.microsoft.com/fwlink/?LinkId=517106)ve daha fazlası hakkında daha hızlı bilgi edinmek için de bağlantılar sunuyoruz.

## <a name="quick-links"></a>Hızlı bağlantılar

Biz ayrıntılara inmek önce en sık istenen bizim bağlantıların bir listesi aşağıda verilmiştir.

|||
|------------------|----------------|
|![Visual Studio 'Yu indirin](../install/media/downloads.png "İndirmeler") |**İndirmeler**: Visual Studio 2015 ' i yüklemek için [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) sayfasından (abonelik gerekir) bir ürün yürütülebilir dosyası indirebilir veya paketlenmiş üründen yükleme medyasını kullanabilirsiniz. [Visual Studio 'nun güncel veya önceki sürümlerini indirme hakkında daha fazla bilgi edinin](https://www.visualstudio.com/vs/older-downloads/).|
|![Özellikler hakkında daha fazla bilgi edinin](../install/media/features.png "Özellikler") |**Özellikler**: Visual Studio 2015 ' deki özellikler hakkında daha fazla bilgi edinmek için bkz. [RTM](https://www.visualstudio.com/news/vs2015-vs), [güncelleştirme 1](https://www.visualstudio.com/news/vs2015-update1-vs), [güncelleştirme 2](https://www.visualstudio.com/news/vs2015-update2-vs)ve [güncelleştirme 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs)için sürüm notları.|
|![Her SKU 'da neler olduğunu öğrenin](../install/media/sku.png "SKU") |**SKU 'lar**: her visual Studio 2015 sürümünde nelerin kullanılabildiğini öğrenmek için bkz. [Compare Visual Studio teklifleri](https://go.microsoft.com/fwlink/?LinkID=242142) sayfası.|
|![Sistem gereksinimlerini görüntüleme](../install/media/system-requirements.png "Sistem Gereksinimleri") |**Sistem gereksinimleri**: her visual Studio 2015 sürümü için sistem gereksinimlerini görüntülemek Için [Visual Studio 2015 Uyumluluk](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) sayfasına bakın.|
|![Ürün anahtarınızı bulun](../install/media/product-keys.png "Ürün anahtarları") |**Ürün anahtarları**: ürün anahtarınızı bulmak için bkz. [nasıl yapılır: Visual Studio ürün anahtarını bulma](../install/how-to-locate-the-visual-studio-product-key.md) konusu.|
|![Lisanslama hakkında bilgi edinin](../install/media/licensing.png "Lisans") |**Lisanslama**: hem bireyler hem de kurumsal müşterilerin lisanslama seçenekleri hakkında bilgi edinmek için bkz. [VISUAL Studio ve MSDN Lisanslama](https://www.microsoft.com/download/details.aspx?id=13350) teknik incelemesi.|

## <a name="custom"></a>Varsayılan ve özel kurulum karşılaştırması
 Visual Studio 2015'i yüklediğinizde dahil edebilir veya hariç, günlük olarak kullanacağınız bileşenleri. Bu varsayılan yükleme genellikle daha küçük bir özel yükleme daha hızlı yükleme anlamına gelir. Ayrıca, bu sürümde açıkça seçmelisiniz özel bileşenlerin önceki sürümlerinde varsayılan olarak artık yüklenmiş olan birçok bileşen olarak kabul edilir anlamına gelir.

 ![Visual Studio 2015 Kurulum Iletişim kutusu](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Özel bileşenler dahil Visual C++, Visual F#, SQL Server veri araçları, platformlar arası mobil araçları ve SDK'ları ve üçüncü taraf SDK'ları ve uzantıları. İlk kurulum sırasında seçmezseniz, özel bileşenleri daha sonra yükleyebilirsiniz.

> [!NOTE]
> Bir özel yükleme otomatik olarak varsayılan yüklemede olan bileşenleri içerir.

 Özel bileşenlerin tam listesi şu şekildedir:

|Özellik kümeleri|Bileşenler|
|------------------|----------------|
|**Güncelleştirmeler**|Visual Studio 2015 Güncelleştirme 3|
|**Programlama dilleri**|Visual C++<br />Visual F#<br />Visual Studio için Python Araçları|
|**Windows ve Web geliştirme**|ClickOnce yayımlama araçları<br />LightSwitch<br />Microsoft Office geliştirici araçları<br />Microsoft SQL Server veri araçları<br /> Microsoft Web geliştirici araçları<br />Visual Studio için PowerShell Araçları (3. taraf)<br />Silverlight Geliştirme Seti<br />Evrensel Windows uygulama geliştirme araçları<br />Windows 10 araçlarını ve Sdk'leri<br />Windows 8.1 ve Windows Phone 8.0/8.1 araçları<br />Windows 8.1 araçları ve SDK'lar|
|**Platformlar arası mobil geliştirme**|C# / .NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Visual C++ Mobil Geliştirme için iOS / Android<br />Microsoft CodeGen ile Clang|
|**Ortak Araçlar ve yazılım geliştirme setleri**|Android yerel Geliştirme Seti (3. taraf)<br /> Android SDK'sı [3. taraf]<br />Android SDK Kurulumu API'leri (3. taraf)<br />Apache Ant (3. taraf)<br /> Java SE Geliştirme Seti (3. taraf)<br /> Joyent Node.js (3. taraf)|
|**Ortak Araçlar**|Windows için Git (3. taraf)<br />Visual Studio için GitHub uzantısı (3. taraf)<br /> Visual Studio genişletilebilirlik araçları|

## <a name="installing"></a>Visual Studio 'Yu yükleme
 Visual Studio 'yu, [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) Web sitesinden Visual Studio abonelik hizmetinizi kullanarak, [Visual Studio İndirmeleri](https://go.microsoft.com/fwlink/?LinkId=517106) Web sitesinden bir web yükleyicisi indirerek ya da çevrimdışı bir yükleme düzeni oluşturarak (daha fazla ayrıntı Için [Visual Studio 'nun çevrimdışı yüklemesini oluşturma](../install/create-an-offline-installation-of-visual-studio.md) sayfasına bakın) kullanarak yükleme medyasını kullanarak yükleyebilirsiniz.

> [!IMPORTANT]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]yüklemek için yönetici kimlik bilgilerine sahip olmanız gerekir. Ancak, yükledikten sonra [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanmasına gerek yoktur.

 Yerel yönetici hesabınızın, etkin olan her şeyi Visual Studio'ya yüklemek için aşağıdaki ayrıcalıkları olmalıdır.

|Yerel ilke nesne görünen adı|Kullanıcı hakkı|
|--------------------------------------|----------------|
|Dosya ve dizinleri yedekle|SeBackupPrivilege|
|Program hata ayıklama|SeDebugPrivilege|
|Denetim ve güvenlik günlüğünü yönetme|SeSecurityPrivilege|

 Bu yerel yönetici hesabı gereksinimi hakkında daha fazla bilgi için bkz. Bilgi Bankası makalesi, [Kurulum hesabı belirli kullanıcı haklarına sahip değilse SQL Server yükleme başarısız olur](https://support.microsoft.com/kb/2000257).

### <a name="BKMK_Media"></a>Yükleme medyasını kullanma
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]yüklemek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yükleme ortamındaki kök dizinde, istediğiniz sürüm için yükleme dosyasını çalıştırın:

|Sürüm|Yükleme dosyası|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

### <a name="BKMK_Website"></a>Ürün web sitesinden indiriliyor
 [Visual Studio İndirmeleri](https://go.microsoft.com/fwlink/?LinkId=517106) sayfasını ziyaret edin ve Istediğiniz Visual Studio sürümünü seçin.

### <a name="downloading-from-your-subscription-service"></a>Abonelik hizmetinizden indiriliyor
 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) sayfasını ziyaret edin ve Istediğiniz Visual Studio sürümünü seçin.

### <a name="BKMK_Offline"></a>Çevrimdışı yükleme düzeni oluşturma
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yükleme medyası yoksa veya bir Visual Studio aboneliğiniz yoksa veya web yükleyicisini kullanarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklemek istemiyorsanız, çevrimdışı yükleme düzeni olarak bilineni oluşturarak "bağlantısı kesilmiş" bir yükleme gerçekleştirebilirsiniz. Daha fazla bilgi için [Visual Studio 'Nun çevrimdışı yüklemesini oluşturma](../install/create-an-offline-installation-of-visual-studio.md) sayfasına bakın.

## <a name="enterprise"></a>Visual Studio 'Yu bir kuruluşta dağıtma
 Bir ağ üzerinden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dağıtma hakkında daha fazla bilgi için bkz. [Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md).

### <a name="BKMK_Virtualized"></a>Sanallaştırılmış bir ortama Visual Studio yükleme
 **Hyper-V ile ilgili video sorunları**

 Hyper-V ve hızlandırılmış grafik bağdaştırıcısının etkin olduğu Windows Server 2008 R2 çalıştırıyorsanız, sistemde yavaşlamalarla karşılaşabilirsiniz.

 Daha fazla bilgi için Microsoft Web sitesindeki şu sayfaya bakın: [Windows server 2008 veya Windows server 2008 R2 tabanlı bir bilgisayarda Hyper-V rolü etkinleştirilmişse ve hızlandırılmış bir görüntü bağdaştırıcısı yüklüyse video performansı düşebilir](https://go.microsoft.com/fwlink/?LinkID=231084).

 **Hyper-V ile cihazları öykünmesi**

 Visual Studio 2015 gerçek donanım sanallaştırma olmaksızın yüklediğinizde, Windows ve Android cihazlarının Hyper-V kullanarak öykünme sağlayan özellikler seçebilirsiniz. Hyper-V yüklediğinizde, Windows veya Android cihazlarına benzetmek mümkün olmayacaktır. Öykünücüler kendilerini sanal makineler olduğundan ve şu anda bir sanal makine başka bir VM içinde barındıramaz budur. Geçici çözüm, gerçek Windows veya kendisine doğrudan dağıtabilir ve uygulamanızda hata ayıklamak Android cihazları sağlamaktır.

## <a name="optionalComponents"></a>İsteğe bağlı bileşenleri yükleme
 Özgün yükleme sırasında seçmiş olabilirsiniz bileşenleri yüklemek istiyorsanız, aşağıdaki yordamı kullanın.

#### <a name="to-install-optional-components"></a>İsteğe bağlı bileşenleri yüklemek için

1. **Denetim Masası**' nda, **Programlar ve Özellikler** sayfasında, bir veya daha fazla bileşen eklemek istediğiniz ürün sürümünü seçin ve ardından **Değiştir**' i seçin.

2. Kurulum sihirbazında, **Değiştir**' i seçin ve ardından yüklemek istediğiniz bileşenleri seçin.

3. **İleri**' yi seçin ve ardından kalan yönergeleri izleyin.

## <a name="helpContent"></a>Çevrimdışı Yardım içeriği yükleme
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]yükledikten sonra, çevrimdışı kullanılabilir hale getirmek için ek yardım içeriğini indirebilirsiniz.

#### <a name="to-install-or-uninstall-help-content"></a>Yardım içeriğini yüklemek veya kaldırmak için

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] menü çubuğunda **Yardım**' ı, **Yardım Içeriğini Ekle ve Kaldır**' ı seçin.

2. **Microsoft Yardım Görüntüleyicisi** **Içeriği Yönet** sekmesinde yardım içeriğiniz için yükleme kaynağını seçin.

3. Belirli bir yardım koleksiyonu arıyorsanız, **arama** metin kutusuna ad veya anahtar sözcüğü girin ve ardından **ENTER**tuşuna basın.

4. İstediğiniz yardım koleksiyonunun adının yanındaki **Ekle** veya **Kaldır** bağlantısını seçin.

5. **Güncelleştir** düğmesine tıklayın.

   Çevrimdışı yardım 'ı yüklemek veya dağıtmak hakkında daha fazla bilgi için [Yardım Görüntüleyici Yönetici Kılavuzu](../ide/help-viewer-administrator-guide.md)' na bakın.

## <a name="serviceReleases"></a>Hizmet sürümleri ve ürün güncelleştirmeleri denetleniyor
 Tüm uzantıları uyumlu olduğu için önceki sürümlerinden yükselttiğinizde, Visual Studio uzantıları otomatik olarak yükseltmez. Uzantıları [Visual Studio Market](https://marketplace.visualstudio.com/) veya yazılım yayımcısından yeniden yüklemeniz gerekir.

#### <a name="to-automatically-check-for-service-releases"></a>Hizmet sürümlerini otomatik olarak denetlemek için

1. Menü çubuğunda **Araçlar**, **Seçenekler**' i seçin.

2. **Seçenekler** Iletişim kutusunda **ortam**' ı genişletin ve ardından **Uzantılar ve güncelleştirmeler**' i seçin. **Güncelleştirmeleri otomatik olarak denetle** onay kutusunun seçili olduğundan emin olun ve ardından **Tamam**' ı seçin.

## <a name="registering-visual-studio"></a>Visual Studio'yu kayıt ettirme

1. Menü çubuğunda **Yardım**' ı ve **hakkında**' yı seçin.

     **Hakkında** iletişim kutusunda ürün kimlik numarası (PID) gösterilir. Ürün kayıt ettirin PID ve Windows hesabı kimlik bilgilerini (örneğin, Hotmail veya Outlook.com e-posta adresi ve parola) gerekir.

2. Menü çubuğunda **Yardım**, **ürünü kaydet**' i seçin.

## <a name="repair"></a>Visual Studio onarılıyor

#### <a name="to-repair-visual-studio"></a>Visual Studio'yu onarmak için

1. **Denetim Masası**' nda, **Programlar ve Özellikler** sayfasında, onarmak istediğiniz ürün sürümünü seçin ve ardından **Değiştir**' i seçin.

2. Kurulum sihirbazında, **Onar**' ı seçin, **İleri**' yi seçin ve ardından kalan yönergeleri izleyin.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Visual Studio'yu Sessiz ya da pasif modda onarmak için (diğer bir deyişle, kaynaktan onarım için)

1. Visual Studio'nun yüklü olduğu bilgisayarda Windows komut istemini açın.

2. Aşağıdaki parametreleri girin:

     *DVDRoot* \\< yükleme dosyası\> \</quiet&#124;/passive > [/norestart]/Repair

## <a name="troubleshooting"></a>Yükleme sorunlarını giderme
 Kurulum ve yükleme sorunları için Yardım almak için bu kaynakları kullanın:

- [Visual Studio Kurulumu ve yükleme](https://go.microsoft.com/fwlink/?LinkID=151190) Forumu. Visual Studio topluluğundaki diğer kişilerden gelen soruları ve yanıtları gözden geçirin. Aradığınızı bulamazsanız, kendi sorularınızı sorun.

- [Visual Studio Web sitesi için Microsoft desteği](https://go.microsoft.com/fwlink/?LinkID=251019) . Bilgi Bankası (BB) makalelerini okuyun ve Visual Studio yüklemesiyle ilgili sorunlar hakkında bilgi için Microsoft Destek birimi ile nasıl iletişim kurabileceğinizi öğrenin.

## <a name="relatedTopics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Visual Studio’nun Çevrimdışı Yüklemesini Oluşturma](../install/create-an-offline-installation-of-visual-studio.md)|Visual Studio, Internet'e bağlı olmadığınızda yüklemeyi açıklar.
|[Visual Studio Sürümlerini Yan Yana Yükleme](../install/install-visual-studio-versions-side-by-side.md)|Bir bilgisayara Visual Studio'nun birden fazla sürümünü yükleme hakkında bilgi sağlar.|
|[Komut Satırı Parametrelerini Kullanarak Visual Studio'yu Yükleme](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Visual Studio Komut İstemi'nden yüklediğinizde kullanabileceğiniz komut satırı parametrelerini listeler.|
|[Visual Studio'yu kaldırma](../install/uninstall-visual-studio.md)|Visual Studio kaldırmayı açıklar.|
|[Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md)|Visual Studio için dağıtım seçenekleri hakkında bilgi sağlar.|
|[Visual Studio Görüntü Kitaplığı](../designers/the-visual-studio-image-library.md)|Visual Studio uygulamalarında kullanabileceğiniz grafikleri yükleme hakkında bilgi sağlar.|
|[Visual Studio ile Geliştirmeye Başlama](../ide/get-started-developing-with-visual-studio.md)|Bilgi ve Visual Studio daha etkili bir şekilde kullanmanıza yardımcı olabilecek bağlantıları içerir.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio'da Oturum Açma](../ide/signing-in-to-visual-studio.md)