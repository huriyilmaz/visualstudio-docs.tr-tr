---
title: ClickOnce uygulamalarının güvenliğini sağlama | Microsoft Docs
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
ms.openlocfilehash: 09d447a33e73c2f27598b027788b3cf1dcd2822b
ms.sourcegitcommit: 960bab34e126c9ca449560a76a839a8f8c3263fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82139643"
---
# <a name="secure-clickonce-applications"></a>ClickOnce uygulamalarını koruma
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]uygulamalar, kodun korumalı kaynaklara ve işlemlere erişimi sınırlamaya yardımcı olmak üzere .NET Framework kod erişimi güvenlik kısıtlamalarına tabidir. Bu nedenle, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamalarınızı uygun şekilde yazmak için kod erişimi güvenliğinin etkilerini anlamanız önemlidir. Uygulamalarınız erişim için Internet ve Intranet gibi tam güven veya kısmi bölgeler kullanabilir.

 Ayrıca ClickOnce, uygulama yayımcısının özgünlüğünü doğrulamak ve dosyaların karışmadığını ispatlamak üzere dağıtım bildirimleri ve uygulamayı imzalamak için sertifikalar kullanır. İmzalama isteğe bağlı bir adımdır; bu, bildirimler üretildikten sonra uygulama dosyalarını değiştirmeyi kolaylaştırır. Ancak, imzalı bildirimler olmadan, uygulama yükleyicisinin ortadaki adam güvenlik saldırılarında müdahaleye uğramadığından olmak zordur. Bu nedenle, uygulamalarınızı güvenlik altına almak için uygulama ve dağıtım bildirimlerinizi imzalamanızı öneririz.

## <a name="zones"></a>Bölgeler
 Teknolojisi kullanılarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtılan uygulamalar, güvenlik bölgesi tarafından tanımlanan bir izin ve eylem kümesiyle kısıtlıdır. Güvenlik bölgeleri, Internet Explorer'da tanımlanmış ve uygulamanın konumunu temel alır. Aşağıdaki tablo dağıtım konumunu temel alan varsayılan izinleri listeler:

|Dağıtım Konumu|Güvenlik Bölgesi|
|-------------------------|-------------------|
|Web'den çalıştırın|Internet Bölgesi|
|Web'den yükleyin|Internet Bölgesi|
|Ağ dosya paylaşımından yükleyin|Yerel Intranet bölgesi|
|CD-ROM'dan yükleyin|Tam Güven|

 Varsayılan izinler uygulamanın özgün sürümüyle dağıtılan konumu temel alır; uygulama güncelleştirmeleri de bu izinleri devralır. Uygulama Web veya ağ konumundan güncelleştirmeleri denetlemek için yapılandırılmış ve daha yeni bir sürüm varsa, özgün yükleme tam güven izinleri yerine Internet ve Intranet bölgesi için izinleri alabilir. Kullanıcıların uyarılmasını önlemek için, Sistem Yöneticisi belirli bir uygulama yayımcısını güvenilir kaynak olarak tanımlayan bir ClickOnce dağıtım ilkesi belirtebilir. Bu ilkenin dağıtılmış olduğu bilgisayarlar için, izinler otomatik olarak verilecek ve kullanıcı uyarılmayacaktır. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md). Güvenilir uygulama dağıtımını yapılandırmak için, sertifika makine veya kuruluş düzeyinde yüklenebilir. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce uygulamaları için bir Istemci bilgisayara güvenilir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

## <a name="code-access-security-policies"></a>Kod erişimi güvenlik ilkeleri
 Bir uygulama için izinler, uygulama bildiriminin [ \<TrustInfo> öğesi](../deployment/trustinfo-element-clickonce-application.md) öğesindeki ayarlar tarafından belirlenir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Bu bilgileri projenin **güvenlik** özelliği sayfasındaki ayarlara göre otomatik olarak oluşturur. Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamaya yalnızca istediği belirli izinler verilir. Örneğin, dosya erişiminin tam güven izinlerini gerektirdiği yerde uygulama tam güven izinleri isterse, uygulamaya tam güven izinleri değil de sadece dosya erişim izni verilir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Uygulamanızı geliştirirken yalnızca uygulamanın ihtiyacı olan belirli izinleri istediğinizden emin olun. Çoğu durumda, uygulamanızı kısmi güvenle sınırlamak için Internet veya yerel Intranet bölgelerini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulaması için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Uygulamanız özel izinleri gerektiriyorsa, özel bir bölge oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulaması için özel Izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

 Uygulamanın dağıtıldığı bölge için varsayılan izin kümesinin parçası olmayan bir izni dahil etme, son kullanıcının güncelleme ve yükleme zamanında iznin verilmesi için uyarılmasına sebep olur. Kullanıcıların uyarılmasını önlemek için, sistem yöneticisi belirli bir uygulama yayımcısını güvenilir kaynak olarak tanımlayan bir ClickOnce dağıtım ilkesi belirtebilir. Bu ilkenin dağıtılmış olduğu bilgisayarlar üzerinde, izinler otomatik olarak verilecek ve kullanıcı uyarılmayacaktır.

 Geliştirici olarak, uygulamanızın uygun izinlerle çalıştığından emin olmak sizin sorumluluğunuzdur. Uygulama çalışma zamanı sırasında bir bölge dışında izinler isterse, güvenlik özel durumu ortaya çıkabilir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Hedef güvenlik bölgesinde uygulamanızın hatalarını ayıklamanızı sağlar. ve güvenli uygulamalar geliştirmeye yönelik yardım sağlar. Daha fazla bilgi için bkz. [System. Deployment. Application kullanan ClickOnce uygulamalarında hata ayıklama](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md).

 Kod erişimi güvenliği ve ClickOnce hakkında daha fazla bilgi için bkz. [ClickOnce uygulamaları Için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="code-signing-certificates"></a>Kod imzalama sertifikaları
 Dağıtım kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir uygulamayı yayımlamak için, ortak/özel anahtar çiftini kullanarak uygulama için uygulama ve dağıtım bildirimlerini imzalayabilirsiniz. Bir bildirimi imzalama araçları, **Proje Tasarımcısı**' nın **imzalama** sayfasında kullanılabilir. Daha fazla bilgi için bkz. [Imzalama sayfası, proje Tasarımcısı](../ide/reference/signing-page-project-designer.md). Alternatif olarak, Yayımlama Sihirbazı 'nı kullanarak, yayımlama işlemi sırasında bildirimleri bir anahtar dosyası ile imzalayabilirsiniz.

 Bildirimler imzalandıktan sonra, Authenticode imzasına bağlı yayımcı bilgisi uygulamanın güvenilir bir kaynaktan olduğunu kullanıcıya göstermek için izinler iletişim kutusunda gösterilir.

 ClickOnce ve sertifikalar hakkında daha fazla bilgi için bkz. [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).

## <a name="aspnet-form-based-authentication"></a>ASP.NET form tabanlı kimlik doğrulaması
 Her bir kullanıcının hangi dağıtımlara erişebileceğini denetlemek isterseniz, bir Web sunucusunda dağıtılan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamalara anonim erişimi etkinleştirmemelisiniz. Alternatif olarak, kullanıcı erişimini bir kullanıcı kimliği üzerinde yüklenmiş dağıtımlar için, Windows kimlik doğrulaması kullanarak etkinleştirebilirsiniz.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]kalıcı tanımlama bilgileri kullandığından ASP.NET form tabanlı kimlik doğrulamasını desteklemez; Bunlar Internet Explorer önbelleğinde olduklarından bir güvenlik riskine neden olur ve bu da etkinleştirilebilir. Bu nedenle, uygulama dağıtıyorsanız [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , Windows kimlik doğrulamasının yanı sıra herhangi bir kimlik doğrulama senaryosu desteklenmez.

## <a name="pass-arguments"></a>Geçiş bağımsız değişkenleri
 Bağımsız değişkenleri bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamaya geçirmeniz gerekiyorsa ek bir güvenlik değerlendirmesi oluşur. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]geliştiricilerin Web üzerinde dağıtılan uygulamalara bir sorgu dizesi vermesini sağlar. Sorgu dizesi, uygulamayı başlatmak için kullanılan URL'nin sonunda bir dizi ad-değer çiftleri şeklini alır:

 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`

 Varsayılan olarak, sorgu dizesi bağımsız değişkenleri devre dışıdır. Bunları etkinleştirmek için, özniteliğin `trustUrlParameters` uygulamanın dağıtım bildiriminde ayarlanması gerekir. Bu değer, MageUI. exe [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ' den ve öğesinden ayarlanabilir. Sorgu dizelerini geçirmeyi etkinleştirme hakkında ayrıntılı adımlar için bkz. [nasıl yapılır: sorgu dizesi bilgilerini bir çevrimiçi ClickOnce uygulamasında alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

 Bir komut satırı veya veritabanı için olan sorgu dizesi aracılığıyla elde edilen bağımsız değişkenleri güvenli oldukları konusunda emin olmadan geçirmeyin. Güvenli olmayan bağımsız değişkenler rasgele komutları çalıştırarak uygulamanızı yönetmek için kötü amaçlı kullanıcılara izin verebilecek veritabanı ve komut satırı kaçış karakterlerini içeren dizelerdir.

> [!NOTE]
> Sorgu dizesi bağımsız değişkenleri, başlatma sırasında bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamaya bağımsız değişkenleri geçirmenin tek yoludur. Komut satırından bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamaya bağımsız değişken geçirilemez.

## <a name="deploying-obfuscated-assemblies"></a>Karıştırılmış derlemeler dağıtma
 Visual Studio, kod gizleme ve etkin koruma önlemleri aracılığıyla ClickOnce uygulamalarınızı korumak için kullanabileceğiniz ücretsiz [preemptive Protection-Dotfuscator topluluğunu](../ide/dotfuscator/index.md)içerir.  Ayrıntılar için lütfen [Dotfuscator Community Kullanıcı kılavuzunun ClickOnce bölümüne](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)
