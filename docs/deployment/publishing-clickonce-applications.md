---
title: ClickOnce Applications | Microsoft Docs
description: Yayımlama Sihirbazı'nı kullanarak bir ClickOnce uygulamayı ilk kez yayımlamayı öğrenin. Project Designer'daki Yayımla sayfasında daha sonra değişiklikler yapın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 4e4537670ef43ceb7379adb29390e316f74243c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035754"
---
# <a name="publish-clickonce-applications"></a>ClickOnce uygulamalarını yayımlama
Bir uygulamayı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ilk kez yayımlarken Yayımlama Sihirbazı kullanılarak yayımlama özellikleri ayarlanıyor. Sihirbazda yalnızca birkaç özellik mevcuttur; diğer tüm özellikler varsayılan değerlerine ayarlanır.

 Yayımlama özelliklerinde sonraki değişiklikler,  Project **Tasarımcısı'nda Yayımla sayfasında yapılır.**

## <a name="publish-wizard"></a>Yayımlama Sihirbazı
 Yayımla Sihirbazı'nı kullanarak, uygulamanızı yayımlamak için temel ayarları yapabilirsiniz. Bu, aşağıdaki yayımlama özelliklerini içerir:

- Yayımlama Klasörü Konumu - Visual Studio (yerel bilgisayar, ağ dosya paylaşımı, FTP sunucusu veya Web sitesi) kopyalayıp kopyalaymayacak

- Yükleme Klasörü Konumu - son kullanıcıların (ağ dosya paylaşımı, FTP sunucusu, Web sitesi, CD/DVD) yüklemesi

- Çevrimiçi veya Çevrimdışı kullanılabilirlik - son kullanıcılar bir ağ bağlantısıyla veya ağ bağlantısı olmadan uygulamaya erişe

- Güncelleştirme sıklığı - uygulamanın yeni güncelleştirmeleri ne sıklıkta kontrol ediyor?

  Daha fazla bilgi için [bkz. Yayımlama Sihirbazı'nı ClickOnce uygulama yayımlama.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

## <a name="publish-page"></a>Yayımla Sayfası
 Project  **Tasarımcısı'nın Yayımla sayfası,** dağıtım için ClickOnce kullanılır. Aşağıdaki tabloda konu başlıkları listele devam ediyor.

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl kullanılır: Dosyaların Visual Studio olduğunu belirtme](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Uygulama dosyalarını ve bildirimlerini Visual Studio ayarlamayı açıklar.|
|[Nasıl kurulur: Son kullanıcıların yükleyecekleri konumu belirtme](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Kullanıcıların uygulamayı indirmeye ve yüklemeye gideceği konumu ayarlamayı açıklar.|
|[Nasıl kurulur: ClickOnce veya çevrimiçi yükleme modunu belirtme](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Uygulamanın çevrimdışı veya çevrimiçi olarak kullanılabilir olup olmadığının nasıl ayar olacağını açıklar.|
|[Nasıl ClickOnce: ClickOnce ayarlama](../deployment/how-to-set-the-clickonce-publish-version.md)|Yayımlamakta ClickOnce **bir** güncelleştirme olarak kabul edilir olup olmadığını belirleyen Yayımlama Sürümü özelliğinin nasıl ayarlandırılarak ayarlanmayacaklarını açıklar.|
|[Nasıl yapılır: Yayımlama sürümünü ClickOnce olarak artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Uygulamayı her yayımlarken **PublishVersion'ın Düzeltme** numarasını otomatik olarak artırmayı açıklar.|

 Daha fazla bilgi için [bkz. Sayfa yayımlama, Project Tasarımcısı](../ide/reference/publish-page-project-designer.md)

### <a name="application-files-dialog-box"></a>Uygulama Dosyaları iletişim kutusu
 Bu iletişim kutusu, projenizin dosyaları yayımlama, dinamik indirme ve güncelleştirme için nasıl kategorilere ayrılmış olduğunu belirtmenize olanak sağlar. Varsayılan olarak dışlanmayacak veya indirme grubu olan proje dosyalarını listeleye bir kılavuz içerir.

 Dosyaları hariç tutmak, dosyaları veri dosyaları veya önkoşullar olarak işaretlemek ve Visual Studio kullanıcı arabiriminde koşullu yükleme için dosya grupları oluşturmak için bkz. Nasıl kullanılır: Hangi dosyaların [ClickOnce.](../deployment/how-to-specify-which-files-are-published-by-clickonce.md) Ayrıca, veri dosyalarını işaretlemek için Mage.exe. Daha fazla bilgi için [bkz. Nasıl kullanılır: Bir veri dosyasını ClickOnce.](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)

### <a name="prerequisites-dialog-box"></a>Önkoşullar iletişim kutusu
 Bu iletişim kutusu, hangi önkoşul bileşenlerinin yüklü olduğunu ve nasıl yük olduklarını belirtir. Daha fazla bilgi için, [bkz. Nasıl](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) 2012: ClickOnce önkoşulları [yükleme ve Önkoşullar iletişim kutusu.](../ide/reference/prerequisites-dialog-box.md)

### <a name="application-updates-dialog-box"></a>Uygulama Güncelleştirmeleri iletişim kutusu
 Bu iletişim kutusu, uygulama yüklemenin güncelleştirmeleri nasıl denetlemesi gerektiğini belirtir. Daha fazla bilgi için, [bkz. How to: Manage updates for a ClickOnce application](../deployment/how-to-manage-updates-for-a-clickonce-application.md).

### <a name="publish-options-dialog-box"></a>Yayımlama Seçenekleri iletişim kutusu
 Yayımlama Seçenekleri iletişim kutusu bir uygulamanın dağıtım seçeneklerini belirtir.

|Başlık|Açıklama|
|-|-|
|[Nasıl ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Yerelleştirilmiş sürümle eşleşmesi için dil ve kültür belirtmeyi açıklar.|
|[Nasıl ClickOnce: Başlat menüsü uygulama için ClickOnce belirtme](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|Bir uygulamanın görünen adının nasıl değiştir ClickOnce açıklar.|
|[Nasıllı: Teknik Destek için bağlantı belirtme](../deployment/how-to-specify-a-link-for-technical-support.md)|Kullanıcıların uygulama hakkında bilgi almak için gidebilirleri bir Web sayfasını veya dosya paylaşımını tanımlayan Destek **URL'si** özelliğinin nasıl ayarlandır açıklar.|
|[Nasıllı: Bir dağıtımda tek tek önkoşullar için destek URL'ClickOnce belirtme](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|Her önkoşul için tek tek destek URL'lerini eklemek için uygulama bildirimini el ile değiştirmenin nasıl açıklandı.|
|[Nasıl ClickOnce: Uygulama için yayımlama sayfası belirtme](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Uygulamayla birlikte varsayılan bir Web sayfası (publish.htm) oluşturma ve yayımlamayı açıklar|
|[Nasıl ClickOnce: ClickOnce Web sayfasını özelleştirme](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Uygulamayla birlikte otomatik olarak oluşturulan ve yayımlanan Web sayfasının nasıl özelleştirebileceğiniz açıklanmaktadır.|
|[Nasıl olur: CD yüklemeleri için AutoStart'i etkinleştirme](../deployment/how-to-enable-autostart-for-cd-installations.md)|Medya eklenirken otomatik olarak ClickOnce için AutoStart'ın nasıl etkinleştirildiğinden emin olun.|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl kurulur: Bir uygulama için dosya ClickOnce oluşturma](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|Bir uygulama için dosya adı uzantısı desteğinin nasıl ClickOnce açıklar.|
|[Nasıl yapılan: Çevrimiçi bir uygulamanın sorgu dizesi ClickOnce alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Bir uygulama çalıştırmak için kullanılan URL'ye geçirilen parametrelerin nasıl ClickOnce gösterir.|
|[Nasıl ClickOnce: Tasarımcıyı kullanarak ClickOnce URL etkinleştirmeyi devre dışı bırakma](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Tasarımcıyı kullanarak kullanıcıları Başlat menüsünden uygulamayı **başlatmaya nasıl** zorlayabilirsiniz?|
|[Nasıl kullanılır: Uygulama uygulamalarının URL etkinleştirmesini ClickOnce devre dışı bırakma](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Kullanıcıları Başlat menüsünden uygulamayı başlatmaya nasıl **zorlayacaklarını** açıklar.|
|[Adım adım kılavuz: Tasarımcı kullanarak ClickOnce dağıtım API'si ile isteğe bağlı derlemeleri indirme](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Uygulama derlemelerinin yalnızca tasarımcı kullanılarak uygulama tarafından ilk kez kullanıldıkları zaman nasıl indirildiklerini açıklar.|
|[Adım adım kılavuz: Derlemeleri isteğe bağlı olarak ClickOnce API'si ile indirme](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Uygulama derlemelerinin yalnızca uygulama tarafından ilk kez kullanıldıkları zaman nasıl indirildiklerini açıklar.|
|[Kılavuz: ClickOnce dağıtım API'si ile isteğe bağlı uydu derlemelerini indirme](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Uydu derlemelerinizi isteğe bağlı olarak işaretlemeyi ve yalnızca bir istemci makinesinin geçerli kültür ayarları için ihtiyacı olan derlemeyi indirmeyi açıklar.|
|[İzlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|Uygulamanızı dağıtmak için .NET Framework yardımcı programlarının nasıl ClickOnce açıklar.|
|[Adım adım kılavuz: Yeniden ClickOnce gerektirmeyen ve marka bilgilerini koruyan bir uygulamanın el ile dağıtımı](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)|Bildirimleri yeniden imzalamadan .NET Framework uygulamanızı dağıtmak için ClickOnce yardımcı programlarını nasıl kullanabileceğinizi açıklar.|
|[Nasıl yapılandırılır: Projeleri platformları hedef olarak yapılandırma](../ide/how-to-configure-projects-to-target-platforms.md)|Projenizin Hedef **CPU** veya Platform hedef özelliğini değiştirerek 64 bit işlemci için **yayımlamayı** açıklar.|
|[Adım adım kılavuz: ClickOnce uygulamanın birden çok sürümde .NET Framework etkinleştirme](/previous-versions/dd996998(v=vs.100))|Net Framework'ClickOnce sürümleri yüklemek ve çalıştırmak için bir uygulamanın nasıl etkinleştirildiklerini açıklar.|
|[Adım adım kılavuz: Bir uygulama için özel ClickOnce oluşturma](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Özel bir uygulama yüklemek için özel bir yükleyicinin nasıl ClickOnce açıklar.|
|[Nasıl yapabilirsiniz: Görsel stiller etkinleştirilmiş bir WPF uygulaması yayımlama](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Görsel stillerin etkin kıldığı bir WPF uygulamasını yayımlamak istediğinizde görüntülenen bir hatayı gidermek için adım adım yönergeler sağlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce başvurusu](../deployment/clickonce-reference.md)