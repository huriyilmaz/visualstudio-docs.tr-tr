---
title: ClickOnce uygulamalarını yayımlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 209aac56f4648554ce619cbe31cef19a8ab1fed7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531800"
---
# <a name="publishing-clickonce-applications"></a>ClickOnce Uygulamalarını Yayımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamayı ilk kez yayımlarken yayımlama özellikleri, Yayımlama Sihirbazı kullanılarak ayarlanabilir. Sihirbazda yalnızca birkaç özellik mevcuttur; diğer tüm özellikler varsayılan değerlerine ayarlanır.  
  
 Yayımla özelliklerinde sonraki değişiklikler, **Proje Tasarımcısı**'nda **Yayımla** sayfasında yapılır.  
  
## <a name="publish-wizard"></a>Yayımlama Sihirbazı  
 Uygulamanızı yayımlamak için temel ayarları ayarlamak üzere Yayımla sihirbazını kullanabilirsiniz. Bu, aşağıdaki yayımlama özelliklerini içerir:  
  
- Yayımlama klasörü konumu-Visual Studio dosyaları (yerel bilgisayar, ağ dosya paylaşma, FTP sunucusu veya Web sitesi) kopyalayacaktır  
  
- Yükleme klasörü konumu-son kullanıcıların yükleneceği konum (ağ dosya paylaşma, FTP sunucusu, Web sitesi, CD/DVD)  
  
- Çevrimiçi veya çevrimdışı kullanılabilirlik-son kullanıcılar uygulamaya ağ bağlantısı olmadan veya bu bağlantıyla erişebil,  
  
- Güncelleştirme sıklığı-uygulamanın yeni güncelleştirmeleri ne sıklıkta denetleyeceğini.  
  
  Daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="publish-page"></a>Yayımla Sayfası  
 **Proje Tasarımcısı** ' nın **Yayımla** sayfası ClickOnce dağıtımı için özellikleri yapılandırmak üzere kullanılır. Aşağıdaki tabloda konular listelenmektedir  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Visual Studio'nun Dosyaları Nereye Kopyalayacağını Belirtme](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Visual Studio 'Nun uygulama dosyalarını ve bildirimlerini nereye yerleştirçalıştığını nasıl ayarlayabileceğinizi açıklar.|  
|[Nasıl yapılır: Son Kullanıcıların Yükleme Yapacakları Konumu Belirtme](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Kullanıcıların uygulamayı indirip yüklemek için gideceği konumun nasıl ayarlanacağını açıklar.|  
|[Nasıl yapılır: ClickOnce Çevrimdışı veya Çevrimiçi Yükleme Modunu Belirtme](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Uygulamanın çevrimdışı veya çevrimiçi olarak kullanılabilir olup olmayacağını nasıl ayarlayabileceğinizi açıklar.|  
|[Nasıl yapılır: ClickOnce Yayım Sürümü'nü Ayarlama](../deployment/how-to-set-the-clickonce-publish-version.md)|Yayımlamakta olduğunuz uygulamanın güncelleştirme olarak değerlendirilip değerlendirilmeyeceğini belirleyen ClickOnce **Publish Version** özelliğinin nasıl ayarlanacağını açıklar.|  
|[Nasıl yapılır: ClickOnce Yayım Sürümünü Otomatik Olarak Artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Uygulamayı yayımladığınızda **Publishversion** öğesinin Düzeltme numarasının otomatik olarak nasıl arttırılacağını açıklar.|  
  
 Daha fazla bilgi için bkz. [Yayımlama sayfası, proje Tasarımcısı](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>Uygulama dosyaları Iletişim kutusu  
 Bu iletişim kutusu, projenizdeki dosyaların yayımlama, dinamik indirme ve güncelleştirme için nasıl kategorilere ayrıldığınızı belirtmenize olanak tanır. Varsayılan olarak Dışlanmayan veya bir indirme grubuna sahip proje dosyalarını listeleyen bir kılavuz içerir.  
  
 Dosyaları dışlamak, dosyaları veri dosyaları veya önkoşulları olarak işaretlemek ve Visual Studio Kullanıcı arabiriminde koşullu yükleme için dosya grupları oluşturmak için bkz. [nasıl yapılır: ClickOnce tarafından hangi dosyaların yayımlandığını belirleme](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). Ayrıca, Mage.exe kullanarak veri dosyalarını işaretleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulamasına veri dosyası ekleme](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### <a name="prerequisites-dialog-box"></a>Önkoşullar İletişim Kutusu  
 Bu iletişim kutusu, hangi önkoşul bileşenlerinin yüklendiğini ve bunların nasıl yüklendiğini belirtir. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce uygulaması ve önkoşulları Ile önkoşulları yüklemek](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) [iletişim kutusu](../ide/reference/prerequisites-dialog-box.md).  
  
### <a name="application-updates-dialog-box"></a>Uygulama güncelleştirmeleri Iletişim kutusu  
 Bu iletişim kutusu, uygulama yüklemesinin güncelleştirmeleri nasıl denetlemesi gerektiğini belirtir. Daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulaması Için güncelleştirmeleri yönetme](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### <a name="publish-options-dialog-box"></a>Yayımlama seçenekleri Iletişim kutusu  
 Yayımlama Seçenekleri iletişim kutusu, bir uygulamanın dağıtım seçeneklerini belirtir.  
  
|Başlık|Açıklama|
|-|-|  
|[Nasıl yapılır: ClickOnce Uygulaması için Yayımlama Dilini Değiştirme](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Yerelleştirilmiş sürümle eşleşecek bir dilin ve kültürün nasıl belirtileceğini açıklar.|  
|[Nasıl yapılır: ClickOnce Uygulaması için Başlat Menüsü Adı Belirtme](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|ClickOnce uygulamasının görünen adının nasıl değiştirileceğini açıklar.|  
|[Nasıl yapılır: Teknik Destek için bir Bağlantı Belirtme](../deployment/how-to-specify-a-link-for-technical-support.md)|Kullanıcıların uygulama hakkında bilgi almak için gidebileceği bir Web sayfası veya dosya paylaşma tanımlayan **Destek URL** özelliğinin nasıl ayarlanacağını açıklar.|  
|[Nasıl yapılır: Bir ClickOnce Dağıtımı'nda Bağımsız Önkoşullar için Destek URL'sini Belirtme](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|Uygulama bildiriminin her bir önkoşul için ayrı destek URL 'Leri içermesi için el ile nasıl değiştirileceği gösterilmiştir.|  
|[Nasıl yapılır: ClickOnce Uygulaması için bir Yayımlama Sayfası Belirtme](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Uygulama ile birlikte varsayılan bir Web sayfası (publish.htm) oluşturmayı ve yayımlamayı açıklar|  
|[Nasıl yapılır: ClickOnce Varsayılan Web Sayfasını Özelleştirme](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Otomatik olarak oluşturulan ve uygulamayla birlikte yayımlanan Web sayfasının nasıl özelleştirileceğini açıklar.|  
|[Nasıl yapılır: CD Yüklemeleri için AutoStart'ı Etkinleştirme](../deployment/how-to-enable-autostart-for-cd-installations.md)|Medya takıldığında ClickOnce uygulamasının otomatik olarak başlatılması için AutoStart 'ın nasıl etkinleştirileceğini açıklar.|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: ClickOnce Uygulaması için Dosya İlişkilendirmeleri Oluşturma](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|ClickOnce uygulamasına dosya adı uzantısı desteğinin nasıl ekleneceğini açıklar.|  
|[Nasıl yapılır: Çevrimiçi bir ClickOnce Uygulamasında Sorgu Dize Bilgilerini Alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|ClickOnce uygulamasını çalıştırmak için kullanılan URL 'ye geçirilen parametrelerin nasıl alınacağını gösterir.|  
|[Nasıl yapılır: Tasarımcıyı Kullanarak ClickOnce Uygulamalarında URL Etkinleştirmeyi Devre Dışı Bırakma](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Tasarımcı kullanarak, kullanıcıların uygulamayı **Başlat** menüsünden başlatmaya nasıl zorlanacağı açıklanmaktadır.|  
|[Nasıl yapılır: ClickOnce Uygulamalarında URL Etkinleştirmeyi Devre Dışı Bırakma](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Kullanıcıların uygulamayı **Başlat** menüsünden başlatmaya nasıl zorlanacağı açıklanmaktadır.|  
|[İzlenecek yol: Tasarımcıyı Kullanarak ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Uygulama derlemelerinin yalnızca Tasarımcı kullanılarak uygulama tarafından ilk kez kullanıldıklarında nasıl indirileceği açıklanır.|  
|[İzlenecek yol: ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Uygulama derlemelerinin yalnızca uygulama tarafından ilk kez kullanıldıklarında nasıl indirileceği açıklanır.|  
|[İzlenecek yol: ClickOnce Dağıtım API'si ile Uydu Derlemelerini İndirme](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Uydu derlemelerinizi isteğe bağlı olarak nasıl işaretleneceğini ve yalnızca geçerli kültür ayarlarına yönelik bir istemci makinesi için gereken derlemeyi nasıl indirecek açıklanmaktadır.|  
|[İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|ClickOnce uygulamanızı dağıtmak için .NET Framework yardımcı programlarının nasıl kullanılacağını açıklar.|  
|[İzlenecek yol: Yeniden İmzalama Gerektirmeyen ve Marka Bilgisini Koruyan bir ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)|Bildirimleri yeniden imzalamadan ClickOnce uygulamanızı dağıtmak için .NET Framework yardımcı programlarının nasıl kullanılacağını açıklar.|  
|[NIB: nasıl yapılır: belirli bir CPU türü için bir uygulamayı Iyileştirme](https://msdn.microsoft.com/294a75d2-4279-4b72-8298-2bea05be907a)|Projenizdeki **hedef CPU** veya **Platform hedefi** özelliğini değiştirerek 64 bitlik bir işlemcinin nasıl yayımlanacağını açıklar.|  
|[İzlenecek yol: bir ClickOnce uygulamasının birden çok .NET Framework sürümünde çalışmasını sağlama](https://msdn.microsoft.com/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Bir ClickOnce uygulamasının, NET Framework 'ün birden çok sürümünü yüklemek ve çalıştırmak için nasıl etkinleştirileceğini açıklar.|  
|[İzlenecek Yol: ClickOnce Uygulaması için Özel bir Yükleyici Oluşturma](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|ClickOnce uygulamasını yüklemek için özel bir yükleyicinin nasıl oluşturulacağını açıklar.|  
|[Nasıl yapılır: Görsel Stiller Etkinken WPF Uygulaması Yayımlama](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Görsel stillerin etkin kıldığı bir WPF uygulamasını yayımlamak istediğinizde görüntülenen bir hatayı gidermek için adım adım yönergeler sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce Başvurusu](../deployment/clickonce-reference.md)
