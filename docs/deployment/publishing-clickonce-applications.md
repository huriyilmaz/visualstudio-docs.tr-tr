---
title: ClickOnce uygulamalarını yayımlama | Microsoft Docs
description: Yayımlama Sihirbazı 'nı kullanarak bir ClickOnce uygulamasını ilk kez nasıl yayımlayacağınızı öğrenin. Proje Tasarımcısı 'nda Yayımla sayfasında daha sonra değişiklikler yapın.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 737e1092d88c48227183a32072502cb833ebcd37
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349496"
---
# <a name="publish-clickonce-applications"></a>ClickOnce uygulamalarını yayımlama
Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayı ilk kez yayımlarken yayımlama özellikleri, Yayımlama Sihirbazı kullanılarak ayarlanabilir. Sihirbazda yalnızca birkaç özellik mevcuttur; diğer tüm özellikler varsayılan değerlerine ayarlanır.

 Yayımla özelliklerinde sonraki değişiklikler, **Proje Tasarımcısı** 'nda **Yayımla** sayfasında yapılır.

## <a name="publish-wizard"></a>Yayımlama Sihirbazı
 Uygulamanızı yayımlamak için temel ayarları ayarlamak üzere Yayımla sihirbazını kullanabilirsiniz. Bu, aşağıdaki yayımlama özelliklerini içerir:

- Yayımlama klasörü konumu-Visual Studio dosyaları (yerel bilgisayar, ağ dosya paylaşma, FTP sunucusu veya Web sitesi) kopyalayacaktır

- Yükleme klasörü konumu-son kullanıcıların yükleneceği konum (ağ dosya paylaşma, FTP sunucusu, Web sitesi, CD/DVD)

- Çevrimiçi veya çevrimdışı kullanılabilirlik-son kullanıcılar uygulamaya ağ bağlantısı olmadan veya bu bağlantıyla erişebil,

- Güncelleştirme sıklığı-uygulamanın yeni güncelleştirmeleri ne sıklıkta denetleyeceğini.

  Daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="publish-page"></a>Yayımla Sayfası
 **Proje Tasarımcısı** ' nın **Yayımla** sayfası ClickOnce dağıtımı için özellikleri yapılandırmak üzere kullanılır. Aşağıdaki tabloda konular listelenmektedir.

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: Visual Studio 'Nun dosyaları nereye kopyaladığını belirtme](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Visual Studio 'Nun uygulama dosyalarını ve bildirimlerini nereye yerleştirçalıştığını nasıl ayarlayabileceğinizi açıklar.|
|[Nasıl yapılır: son kullanıcıların yükleneceği konumu belirtme](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Kullanıcıların uygulamayı indirip yüklemek için gideceği konumun nasıl ayarlanacağını açıklar.|
|[Nasıl yapılır: ClickOnce Çevrimdışı veya çevrimiçi yüklemesi modunu belirtme](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Uygulamanın çevrimdışı veya çevrimiçi olarak kullanılabilir olup olmayacağını nasıl ayarlayabileceğinizi açıklar.|
|[Nasıl yapılır: ClickOnce yayımlama sürümünü ayarlama](../deployment/how-to-set-the-clickonce-publish-version.md)|Yayımlamakta olduğunuz uygulamanın güncelleştirme olarak değerlendirilip değerlendirilmeyeceğini belirleyen ClickOnce **Publish Version** özelliğinin nasıl ayarlanacağını açıklar.|
|[Nasıl yapılır: ClickOnce Yayım sürümünü otomatik olarak artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Uygulamayı yayımladığınızda **Publishversion** öğesinin Düzeltme numarasının otomatik olarak nasıl arttırılacağını açıklar.|

 Daha fazla bilgi için bkz. [Yayımlama sayfası, proje Tasarımcısı](../ide/reference/publish-page-project-designer.md)

### <a name="application-files-dialog-box"></a>Uygulama dosyaları iletişim kutusu
 Bu iletişim kutusu, projenizdeki dosyaların yayımlama, dinamik indirme ve güncelleştirme için nasıl kategorilere ayrıldığınızı belirtmenize olanak tanır. Varsayılan olarak Dışlanmayan veya bir indirme grubuna sahip proje dosyalarını listeleyen bir kılavuz içerir.

 Dosyaları dışlamak, dosyaları veri dosyaları veya önkoşulları olarak işaretlemek ve Visual Studio Kullanıcı arabiriminde koşullu yükleme için dosya grupları oluşturmak için bkz. [nasıl yapılır: ClickOnce tarafından hangi dosyaların yayımlandığını belirleme](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). Ayrıca, Mage.exe kullanarak veri dosyalarını işaretleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulamasına veri dosyası ekleme](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

### <a name="prerequisites-dialog-box"></a>Önkoşullar iletişim kutusu
 Bu iletişim kutusu, hangi önkoşul bileşenlerinin yüklendiğini ve bunların nasıl yüklendiğini belirtir. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce uygulaması ve önkoşulları ile önkoşulları yüklemek](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) [iletişim kutusu](../ide/reference/prerequisites-dialog-box.md).

### <a name="application-updates-dialog-box"></a>Uygulama güncelleştirmeleri iletişim kutusu
 Bu iletişim kutusu, uygulama yüklemesinin güncelleştirmeleri nasıl denetlemesi gerektiğini belirtir. Daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulaması için güncelleştirmeleri yönetme](../deployment/how-to-manage-updates-for-a-clickonce-application.md).

### <a name="publish-options-dialog-box"></a>Yayımlama Seçenekleri iletişim kutusu
 Yayımlama Seçenekleri iletişim kutusu, bir uygulamanın dağıtım seçeneklerini belirtir.

|Başlık|Açıklama|
|-|-|
|[Nasıl yapılır: ClickOnce uygulaması için yayımlama dilini değiştirme](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Yerelleştirilmiş sürümle eşleşecek bir dilin ve kültürün nasıl belirtileceğini açıklar.|
|[Nasıl yapılır: ClickOnce uygulaması için Başlat menüsü adı belirtme](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|ClickOnce uygulamasının görünen adının nasıl değiştirileceğini açıklar.|
|[Nasıl yapılır: teknik destek için bir bağlantı belirtme](../deployment/how-to-specify-a-link-for-technical-support.md)|Kullanıcıların uygulama hakkında bilgi almak için gidebileceği bir Web sayfası veya dosya paylaşma tanımlayan **Destek URL** özelliğinin nasıl ayarlanacağını açıklar.|
|[Nasıl yapılır: bir ClickOnce dağıtımında tek Önkoşullar için destek URL 'SI belirtme](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|Uygulama bildiriminin her bir önkoşul için ayrı destek URL 'Leri içermesi için el ile nasıl değiştirileceği gösterilmiştir.|
|[Nasıl yapılır: ClickOnce uygulaması için bir yayımlama sayfası belirtme](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Uygulama ile birlikte varsayılan bir Web sayfası (publish.htm) oluşturmayı ve yayımlamayı açıklar|
|[Nasıl yapılır: ClickOnce varsayılan Web sayfasını özelleştirme](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Otomatik olarak oluşturulan ve uygulamayla birlikte yayımlanan Web sayfasının nasıl özelleştirileceğini açıklar.|
|[Nasıl yapılır: CD yüklemeleri için AutoStart 'ı etkinleştirme](../deployment/how-to-enable-autostart-for-cd-installations.md)|Medya takıldığında ClickOnce uygulamasının otomatik olarak başlatılması için AutoStart 'ın nasıl etkinleştirileceğini açıklar.|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: ClickOnce uygulaması Için dosya ilişkilendirmeleri oluşturma](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|ClickOnce uygulamasına dosya adı uzantısı desteğinin nasıl ekleneceğini açıklar.|
|[Nasıl yapılır: çevrimiçi bir ClickOnce uygulamasında sorgu dize bilgilerini alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|ClickOnce uygulamasını çalıştırmak için kullanılan URL 'ye geçirilen parametrelerin nasıl alınacağını gösterir.|
|[Nasıl yapılır: Tasarımcıyı kullanarak ClickOnce uygulamalarında URL etkinleştirmeyi devre dışı bırakma](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Tasarımcı kullanarak, kullanıcıların uygulamayı **Başlat** menüsünden başlatmaya nasıl zorlanacağı açıklanmaktadır.|
|[Nasıl yapılır: ClickOnce uygulamalarında URL etkinleştirmeyi devre dışı bırakma](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Kullanıcıların uygulamayı **Başlat** menüsünden başlatmaya nasıl zorlanacağı açıklanmaktadır.|
|[İzlenecek yol: Tasarımcıyı kullanarak ClickOnce dağıtım API 'SI ile isteğe bağlı derlemeleri Indirme](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Uygulama derlemelerinin yalnızca Tasarımcı kullanılarak uygulama tarafından ilk kez kullanıldıklarında nasıl indirileceği açıklanır.|
|[İzlenecek yol: ClickOnce dağıtım API 'SI ile isteğe bağlı derlemeleri Indirme](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Uygulama derlemelerinin yalnızca uygulama tarafından ilk kez kullanıldıklarında nasıl indirileceği açıklanır.|
|[İzlenecek yol: ClickOnce dağıtım API 'SI ile isteğe bağlı uydu derlemelerini Indirme](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Uydu derlemelerinizi isteğe bağlı olarak nasıl işaretleneceğini ve yalnızca geçerli kültür ayarlarına yönelik bir istemci makinesi için gereken derlemeyi nasıl indirecek açıklanmaktadır.|
|[İzlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|ClickOnce uygulamanızı dağıtmak için .NET Framework yardımcı programlarının nasıl kullanılacağını açıklar.|
|[İzlenecek yol: yeniden imzalama gerektirmeyen ve marka bilgilerini koruyan bir ClickOnce uygulamasını El Ile dağıtın](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)|Bildirimleri yeniden imzalamadan ClickOnce uygulamanızı dağıtmak için .NET Framework yardımcı programlarının nasıl kullanılacağını açıklar.|
|[Nasıl yapılır: projeleri hedef platformlar için yapılandırma](../ide/how-to-configure-projects-to-target-platforms.md)|Projenizdeki **hedef CPU** veya **Platform hedefi** özelliğini değiştirerek 64 bitlik bir işlemcinin nasıl yayımlanacağını açıklar.|
|[İzlenecek yol: ClickOnce uygulamasını birden çok .NET Framework sürümünde çalışacak şekilde etkinleştirme](/previous-versions/dd996998(v=vs.100))|Bir ClickOnce uygulamasının, NET Framework 'ün birden çok sürümünü yüklemek ve çalıştırmak için nasıl etkinleştirileceğini açıklar.|
|[İzlenecek yol: ClickOnce uygulaması için özel bir yükleyici oluşturma](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|ClickOnce uygulamasını yüklemek için özel bir yükleyicinin nasıl oluşturulacağını açıklar.|
|[Nasıl yapılır: görsel stiller etkinken WPF uygulaması yayımlama](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Görsel stillerin etkin kıldığı bir WPF uygulamasını yayımlamak istediğinizde görüntülenen bir hatayı gidermek için adım adım yönergeler sağlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce Başvurusu](../deployment/clickonce-reference.md)