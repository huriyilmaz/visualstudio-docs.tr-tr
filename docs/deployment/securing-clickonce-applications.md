---
title: ClickOnce Uygulamaları Güvence | Microsoft Dokümanlar
ms.date: 02/17/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6743e08517a8b360d7635f11b6d3a0c0d84c780f
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649412"
---
# <a name="secure-clickonce-applications"></a>ClickOnce uygulamalarını koruma
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]uygulamalar, kodun korumalı kaynaklara ve işlemlere erişimini sınırlamaya yardımcı olmak için .NET Framework'deki kod erişim güvenlik kısıtlamalarına tabidir. Bu nedenle, uygulamalarınızı buna göre yazmak için kod erişim [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] güvenliğinin etkilerini anlamanız önemlidir. Uygulamalarınız erişim için Internet ve Intranet gibi tam güven veya kısmi bölgeler kullanabilir.

 Ayrıca ClickOnce, uygulama yayımcısının özgünlüğünü doğrulamak ve dosyaların karışmadığını ispatlamak üzere dağıtım bildirimleri ve uygulamayı imzalamak için sertifikalar kullanır. İmzalama isteğe bağlı bir adımdır; bu, bildirimler üretildikten sonra uygulama dosyalarını değiştirmeyi kolaylaştırır. Ancak, imzalı bildirimler olmadan, uygulama yükleyicisinin ortadaki adam güvenlik saldırılarında müdahaleye uğramadığından olmak zordur. Bu nedenle, uygulamalarınızı güvenlik altına almak için uygulama ve dağıtım bildirimlerinizi imzalamanızı öneririz.

## <a name="zones"></a>Bölgeler
 Teknoloji kullanılarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtılan uygulamalar, güvenlik bölgesi tarafından tanımlanan bir dizi izin ve eylemle sınırlıdır. Güvenlik bölgeleri, Internet Explorer'da tanımlanmış ve uygulamanın konumunu temel alır. Aşağıdaki tablo dağıtım konumunu temel alan varsayılan izinleri listeler:

|Dağıtım Konumu|Güvenlik Bölgesi|
|-------------------------|-------------------|
|Web'den çalıştırın|Internet Bölgesi|
|Web'den yükleyin|Internet Bölgesi|
|Ağ dosya paylaşımından yükleyin|Yerel Intranet bölgesi|
|CD-ROM'dan yükleyin|Tam Güven|

 Varsayılan izinler uygulamanın özgün sürümüyle dağıtılan konumu temel alır; uygulama güncelleştirmeleri de bu izinleri devralır. Uygulama Web veya ağ konumundan güncelleştirmeleri denetlemek için yapılandırılmış ve daha yeni bir sürüm varsa, özgün yükleme tam güven izinleri yerine Internet ve Intranet bölgesi için izinleri alabilir. Kullanıcıların uyarılmasını önlemek için, Sistem Yöneticisi belirli bir uygulama yayımcısını güvenilir kaynak olarak tanımlayan bir ClickOnce dağıtım ilkesi belirtebilir. Bu ilkenin dağıtılmış olduğu bilgisayarlar için, izinler otomatik olarak verilecek ve kullanıcı uyarılmayacaktır. Daha fazla bilgi için bkz: [Güvenilir Uygulama Dağıtımına Genel Bakış.](../deployment/trusted-application-deployment-overview.md) Güvenilir uygulama dağıtımını yapılandırmak için, sertifika makine veya kuruluş düzeyinde yüklenebilir. Daha fazla bilgi için [bkz: ClickOnce Applications için Istemci Bilgisayara Güvenilir Yayımcı Ekleme.](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)

## <a name="code-access-security-policies"></a>Kod erişim güvenlik ilkeleri
 Uygulama izinleri, uygulama bildiriminin [ \<trustInfo> Öğesi](../deployment/trustinfo-element-clickonce-application.md) öğesindeki ayarlara göre belirlenir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]bu bilgileri projenin **Güvenlik** özelliği sayfasındaki ayarlara göre otomatik olarak oluşturur. Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamaya yalnızca talep ettiği belirli izinler verilir. Örneğin, dosya erişiminin tam güven izinlerini gerektirdiği yerde uygulama tam güven izinleri isterse, uygulamaya tam güven izinleri değil de sadece dosya erişim izni verilir. Uygulamanızı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] geliştirirken, yalnızca uygulamanın ihtiyaç duyduğu belirli izinleri istediğinizden emin olmalısınız. Çoğu durumda, uygulamanızı kısmi güvenle sınırlamak için Internet veya yerel Intranet bölgelerini kullanabilirsiniz. Daha fazla bilgi için [bkz: ClickOnce uygulaması için bir güvenlik bölgesi ayarlayın.](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md) Uygulamanız özel izinleri gerektiriyorsa, özel bir bölge oluşturabilirsiniz. Daha fazla bilgi için [bkz: ClickOnce uygulaması için özel izinler ayarlayın.](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)

 Uygulamanın dağıtıldığı bölge için varsayılan izin kümesinin parçası olmayan bir izni dahil etme, son kullanıcının güncelleme ve yükleme zamanında iznin verilmesi için uyarılmasına sebep olur. Kullanıcıların uyarılmasını önlemek için, sistem yöneticisi belirli bir uygulama yayımcısını güvenilir kaynak olarak tanımlayan bir ClickOnce dağıtım ilkesi belirtebilir. Bu ilkenin dağıtılmış olduğu bilgisayarlar üzerinde, izinler otomatik olarak verilecek ve kullanıcı uyarılmayacaktır.

 Geliştirici olarak, uygulamanızın uygun izinlerle çalıştığından emin olmak sizin sorumluluğunuzdur. Uygulama çalışma zamanı sırasında bir bölge dışında izinler isterse, güvenlik özel durumu ortaya çıkabilir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]hedef güvenlik bölgesinde uygulamanızı hata ayıklamanızı sağlar. ve güvenli uygulamaların geliştirilmesinde yardımcı olur. Daha fazla bilgi için [bkz: Nasıl: Kısıtlı izinlerle ClickOnce uygulamasını hata ayıklama.](securing-clickonce-applications.md)

 Kod erişim güvenliği ve ClickOnce hakkında daha fazla bilgi [için ClickOnce uygulamaları için Kod erişim güvenliğine](../deployment/code-access-security-for-clickonce-applications.md)bakın.

## <a name="code-signing-certificates"></a>Kod imzalama sertifikaları
 Dağıtım kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir uygulama yayımlamak için, uygulama için uygulama ve dağıtım bildirimlerini ortak/özel anahtar çifti kullanarak imzalayabilirsiniz. Bir manifesto imzalama araçları **Proje Tasarımcısı'nın** **İmzalama** sayfasında mevcuttur. Daha fazla bilgi için Bkz. [İmzaLama Sayfası, Proje Tasarımcısı.](../ide/reference/signing-page-project-designer.md) Alternatif olarak, Yayımlama Sihirbazı'nı kullanarak yayımlama işlemi sırasında bildirimleri önemli bir dosyayla imzalayabilirsiniz.

 Bildirimler imzalandıktan sonra, Authenticode imzasına bağlı yayımcı bilgisi uygulamanın güvenilir bir kaynaktan olduğunu kullanıcıya göstermek için izinler iletişim kutusunda gösterilir.

 ClickOnce ve sertifikalar hakkında daha fazla bilgi için [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)bölümüne bakın.

## <a name="aspnet-form-based-authentication"></a>ASP.NET form tabanlı kimlik doğrulama
 Her kullanıcının hangi dağıtımlara erişebileceğini denetlemek istiyorsanız, Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Web sunucusunda dağıtılan uygulamalara anonim erişim sağlamamalısınız. Alternatif olarak, kullanıcı erişimini bir kullanıcı kimliği üzerinde yüklenmiş dağıtımlar için, Windows kimlik doğrulaması kullanarak etkinleştirebilirsiniz.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]kalıcı tanımlama bilgileri kullandığından ASP.NET form tabanlı kimlik doğrulamasını desteklemez; Bunlar, Internet Explorer önbelleğinde bulunduğundan ve saldırıya uğradıkları için bir güvenlik riski oluşturur. Bu nedenle, uygulamaları [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtıyorsanız, Windows kimlik doğrulaması dışında herhangi bir kimlik doğrulama senaryosu desteklenmez.

## <a name="pass-arguments"></a>Geçiş bağımsız değişkenleri
 Bağımsız değişkenleri bir uygulamaya geçirmeniz gerekiyorsa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ek bir güvenlik değerlendirmesi oluşur. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]geliştiricilerin Web üzerinden dağıtılan uygulamalara bir sorgu dizesi sağlamasına olanak tanır. Sorgu dizesi, uygulamayı başlatmak için kullanılan URL'nin sonunda bir dizi ad-değer çiftleri şeklini alır:

 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`

 Varsayılan olarak, sorgu dizesi bağımsız değişkenleri devre dışıdır. Bunları etkinleştirmek için `trustUrlParameters` öznitelik uygulamanın dağıtım bildiriminde ayarlanmalıdır. Bu değer MageUI.exe'den ve MageUI.exe'den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ayarlanabilir. Sorgu dizelerini geçirmeyi etkinleştirme konusunda ayrıntılı adımlar için [bkz.](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)

 Bir komut satırı veya veritabanı için olan sorgu dizesi aracılığıyla elde edilen bağımsız değişkenleri güvenli oldukları konusunda emin olmadan geçirmeyin. Güvenli olmayan bağımsız değişkenler rasgele komutları çalıştırarak uygulamanızı yönetmek için kötü amaçlı kullanıcılara izin verebilecek veritabanı ve komut satırı kaçış karakterlerini içeren dizelerdir.

> [!NOTE]
> Sorgu dize bağımsız değişkenleri, bağımsız [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] değişkenleri başlangıçta bir uygulamaya geçirmenin tek yoludur. Bağımsız değişkenleri komut [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] satırından bir uygulamaya geçiremezsiniz.

## <a name="deploying-obfuscated-assemblies"></a>Obfuscated montajları dağıtma
 Visual Studio ücretsiz [PreEmptive Koruma içerir - Dotfuscator Topluluk](../ide/dotfuscator/index.md), kod gizleme ve aktif koruma önlemleri ile ClickOnce uygulamaları korumak için kullanabilirsiniz.  Ayrıntılar için lütfen [Dotfuscator Topluluk Kullanım Kılavuzu'nun ClickOnce bölümüne](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)