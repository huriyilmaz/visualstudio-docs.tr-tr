---
title: ClickOnce uygulamalarının güvenliğini sağlama | Microsoft Docs
description: ClickOnce uygulamalarınızın koduna erişimi sınırlayan .NET Framework kod erişimi güvenlik kısıtlamalarının etkileri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 722e37cf87256d6b1e95232228d2ae4357075618
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627747"
---
# <a name="secure-clickonce-applications"></a>ClickOnce uygulamalarını koruma
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]uygulamalar, kodun korumalı kaynaklara ve işlemlere erişimi sınırlamaya yardımcı olmak üzere .NET Framework kod erişimi güvenlik kısıtlamalarına tabidir. Bu nedenle, uygulamalarınızı uygun şekilde yazmak için kod erişimi güvenliğinin etkilerini anlamanız önemlidir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Uygulamalarınız erişim için Internet ve Intranet gibi tam güven veya kısmi bölgeler kullanabilir.

 Ayrıca ClickOnce, uygulama yayımcısının özgünlüğünü doğrulamak ve dosyaların karışmadığını ispatlamak üzere dağıtım bildirimleri ve uygulamayı imzalamak için sertifikalar kullanır. İmzalama isteğe bağlı bir adımdır; bu, bildirimler üretildikten sonra uygulama dosyalarını değiştirmeyi kolaylaştırır. Ancak, imzalı bildirimler olmadan, uygulama yükleyicisinin ortadaki adam güvenlik saldırılarında müdahaleye uğramadığından olmak zordur. Bu nedenle, uygulamalarınızı güvenlik altına almak için uygulama ve dağıtım bildirimlerinizi imzalamanızı öneririz.

## <a name="zones"></a>Bölgeler
 Teknolojisi kullanılarak dağıtılan uygulamalar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , güvenlik bölgesi tarafından tanımlanan bir izin ve eylem kümesiyle kısıtlıdır. Güvenlik bölgeleri, Internet Explorer'da tanımlanmış ve uygulamanın konumunu temel alır. Aşağıdaki tablo dağıtım konumunu temel alan varsayılan izinleri listeler:

|Dağıtım Konumu|Güvenlik Bölgesi|
|-------------------------|-------------------|
|Web'den çalıştırın|Internet Bölgesi|
|Web'den yükleyin|Internet Bölgesi|
|Ağ dosya paylaşımından yükleyin|Yerel Intranet bölgesi|
|CD-ROM'dan yükleyin|Tam Güven|

 Varsayılan izinler uygulamanın özgün sürümüyle dağıtılan konumu temel alır; uygulama güncelleştirmeleri de bu izinleri devralır. Uygulama Web veya ağ konumundan güncelleştirmeleri denetlemek için yapılandırılmış ve daha yeni bir sürüm varsa, özgün yükleme tam güven izinleri yerine Internet ve Intranet bölgesi için izinleri alabilir. Kullanıcıların uyarılmasını önlemek için, sistem yöneticisi belirli bir uygulama yayımcısını güvenilir kaynak olarak tanımlayan bir ClickOnce dağıtım ilkesi belirtebilir. Bu ilkenin dağıtılmış olduğu bilgisayarlar için, izinler otomatik olarak verilecek ve kullanıcı uyarılmayacaktır. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md). Güvenilir uygulama dağıtımını yapılandırmak için, sertifika makine veya kuruluş düzeyinde yüklenebilir. daha fazla bilgi için bkz. [nasıl yapılır: istemci bilgisayara güvenilir Publisher ekleme ClickOnce uygulamalar için](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

## <a name="code-access-security-policies"></a>Kod erişimi güvenlik ilkeleri
 Bir uygulama için izinler, uygulama bildiriminin [ \<trustInfo> öğe](../deployment/trustinfo-element-clickonce-application.md) öğesindeki ayarlara göre belirlenir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Bu bilgileri projenin **güvenlik** özelliği sayfasındaki ayarlara göre otomatik olarak oluşturur. Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamaya yalnızca istediği belirli izinler verilir. Örneğin, dosya erişiminin tam güven izinlerini gerektirdiği yerde uygulama tam güven izinleri isterse, uygulamaya tam güven izinleri değil de sadece dosya erişim izni verilir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulamanızı geliştirirken yalnızca uygulamanın ihtiyacı olan belirli izinleri istediğinizden emin olun. Çoğu durumda, uygulamanızı kısmi güvenle sınırlamak için Internet veya yerel Intranet bölgelerini kullanabilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce bir uygulama için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Uygulamanız özel izinleri gerektiriyorsa, özel bir bölge oluşturabilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

 Uygulamanın dağıtıldığı bölge için varsayılan izin kümesinin parçası olmayan bir izni dahil etme, son kullanıcının güncelleme ve yükleme zamanında iznin verilmesi için uyarılmasına sebep olur. Kullanıcıların uyarılmasını önlemek için, sistem yöneticisi belirli bir uygulama yayımcısını güvenilir kaynak olarak tanımlayan bir ClickOnce dağıtım ilkesi belirtebilir. Bu ilkenin dağıtılmış olduğu bilgisayarlar üzerinde, izinler otomatik olarak verilecek ve kullanıcı uyarılmayacaktır.

 Geliştirici olarak, uygulamanızın uygun izinlerle çalıştığından emin olmak sizin sorumluluğunuzdur. Uygulama çalışma zamanı sırasında bir bölge dışında izinler isterse, güvenlik özel durumu ortaya çıkabilir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Hedef güvenlik bölgesinde uygulamanızın hatalarını ayıklamanızı sağlar ve güvenli uygulamalar geliştirmeye yönelik yardım sağlar. daha fazla bilgi için bkz. [System. Deployment. Application kullanan ClickOnce hata ayıklama uygulamaları](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md).

 kod erişimi güvenliği ve ClickOnce hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalar için kod erişim güvenliği](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="code-signing-certificates"></a>Kod imzalama sertifikaları
 Dağıtım kullanarak bir uygulamayı yayımlamak için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , ortak/özel anahtar çiftini kullanarak uygulama için uygulama ve dağıtım bildirimlerini imzalayabilirsiniz. bir bildirimi imzalamak için araçlar **Project tasarımcısının** **imzalama** sayfasında kullanılabilir. daha fazla bilgi için bkz. [imzalama sayfası, Project tasarımcısı](../ide/reference/signing-page-project-designer.md).

 Bildirimler imzalandıktan sonra, Authenticode imzasına bağlı yayımcı bilgisi uygulamanın güvenilir bir kaynaktan olduğunu kullanıcıya göstermek için izinler iletişim kutusunda gösterilir.

 ClickOnce ve sertifikalar hakkında daha fazla bilgi için bkz. [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md).

## <a name="aspnet-form-based-authentication"></a>ASP.NET form tabanlı kimlik doğrulaması
 Her bir kullanıcının hangi dağıtımlara erişebileceğini denetlemek isterseniz, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir Web sunucusunda dağıtılan uygulamalara anonim erişimi etkinleştirmemelisiniz. Alternatif olarak, kullanıcı erişimini bir kullanıcı kimliği üzerinde yüklenmiş dağıtımlar için, Windows kimlik doğrulaması kullanarak etkinleştirebilirsiniz.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]kalıcı tanımlama bilgileri kullandığından ASP.NET form tabanlı kimlik doğrulamasını desteklemez; Bunlar Internet Explorer önbelleğinde olduklarından bir güvenlik riskine neden olur ve bu da etkinleştirilebilir. bu nedenle, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama dağıtıyorsanız Windows kimlik doğrulamasının yanı sıra herhangi bir kimlik doğrulama senaryosu desteklenmez.

## <a name="pass-arguments"></a>Geçiş bağımsız değişkenleri
 Bağımsız değişkenleri bir uygulamaya geçirmeniz gerekiyorsa ek bir güvenlik değerlendirmesi oluşur [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] geliştiricilerin Web üzerinde dağıtılan uygulamalara bir sorgu dizesi vermesini sağlar. Sorgu dizesi, uygulamayı başlatmak için kullanılan URL'nin sonunda bir dizi ad-değer çiftleri şeklini alır:

 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`

 Varsayılan olarak, sorgu dizesi bağımsız değişkenleri devre dışıdır. Bunları etkinleştirmek için, özniteliğin `trustUrlParameters` uygulamanın dağıtım bildiriminde ayarlanması gerekir. Bu değer, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] MageUI.exe 'den ve öğesinden ayarlanabilir. sorgu dizelerini geçirmeyi etkinleştirme hakkında ayrıntılı adımlar için bkz. [nasıl yapılır: sorgu dizesi bilgilerini bir çevrimiçi ClickOnce uygulamasında alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

 Bir komut satırı veya veritabanı için olan sorgu dizesi aracılığıyla elde edilen bağımsız değişkenleri güvenli oldukları konusunda emin olmadan geçirmeyin. Güvenli olmayan bağımsız değişkenler rasgele komutları çalıştırarak uygulamanızı yönetmek için kötü amaçlı kullanıcılara izin verebilecek veritabanı ve komut satırı kaçış karakterlerini içeren dizelerdir.

> [!NOTE]
> Sorgu dizesi bağımsız değişkenleri, başlatma sırasında bir uygulamaya bağımsız değişkenleri geçirmenin tek yoludur [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Komut satırından bir uygulamaya bağımsız değişken geçirilemez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

## <a name="deploying-obfuscated-assemblies"></a>Karıştırılmış derlemeler dağıtma
 Visual Studio, kod gizleme ve etkin koruma önlemleri aracılığıyla ClickOnce uygulamalarınızı korumak için kullanabileceğiniz ücretsiz [PreEmptive Protection-dotfuscator Community](../ide/dotfuscator/index.md)içerir.  ayrıntılar için lütfen [dotfuscator Community kullanıcı kılavuzunun ClickOnce bölümüne](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)
