---
title: ClickOnce uygulamalarının güvenliğini sağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a2610c1fef92bb77d150dad7972bb991b6ef4a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686018"
---
# <a name="securing-clickonce-applications"></a>ClickOnce Uygulamalarının Güvenliğini Sağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalar, kodun korumalı kaynaklara ve işlemlere erişimi sınırlamaya yardımcı olmak üzere .NET Framework kod erişimi güvenlik kısıtlamalarına tabidir. Bu nedenle, uygulamalarınızı uygun şekilde yazmak için kod erişimi güvenliğinin etkilerini anlamanız önemlidir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Uygulamalarınız erişim için Internet ve Intranet gibi tam güven veya kısmi bölgeler kullanabilir.  
  
 Ayrıca ClickOnce, uygulama yayımcısının özgünlüğünü doğrulamak ve dosyaların karışmadığını ispatlamak üzere dağıtım bildirimleri ve uygulamayı imzalamak için sertifikalar kullanır. İmzalama isteğe bağlı bir adımdır; bu, bildirimler üretildikten sonra uygulama dosyalarını değiştirmeyi kolaylaştırır. Ancak, imzalı bildirimler olmadan, uygulama yükleyicisinin ortadaki adam güvenlik saldırılarında müdahaleye uğramadığından olmak zordur. Bu nedenle, uygulamalarınızı güvenlik altına almak için uygulama ve dağıtım bildirimlerinizi imzalamanızı öneririz.  
  
## <a name="zones"></a>Bölgeler  
 Teknolojisi kullanılarak dağıtılan uygulamalar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , güvenlik bölgesi tarafından tanımlanan bir izin ve eylem kümesiyle kısıtlıdır. Güvenlik bölgeleri, Internet Explorer'da tanımlanmış ve uygulamanın konumunu temel alır. Aşağıdaki tablo dağıtım konumunu temel alan varsayılan izinleri listeler:  
  
|Dağıtım Konumu|Güvenlik Bölgesi|  
|-------------------------|-------------------|  
|Web'den çalıştırın|Internet Bölgesi|  
|Web'den yükleyin|Internet Bölgesi|  
|Ağ dosya paylaşımından yükleyin|Yerel Intranet bölgesi|  
|CD-ROM'dan yükleyin|Tam Güven|  
  
 Varsayılan izinler uygulamanın özgün sürümüyle dağıtılan konumu temel alır; uygulama güncelleştirmeleri de bu izinleri devralır. Uygulama Web veya ağ konumundan güncelleştirmeleri denetlemek için yapılandırılmış ve daha yeni bir sürüm varsa, özgün yükleme tam güven izinleri yerine Internet ve Intranet bölgesi için izinleri alabilir. Kullanıcıların uyarılmasını önlemek için, Sistem Yöneticisi belirli bir uygulama yayımcısını güvenilir kaynak olarak tanımlayan bir ClickOnce dağıtım ilkesi belirtebilir. Bu ilkenin dağıtılmış olduğu bilgisayarlar için, izinler otomatik olarak verilecek ve kullanıcı uyarılmayacaktır. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md). Güvenilir uygulama dağıtımını yapılandırmak için, sertifika makine veya kuruluş düzeyinde yüklenebilir. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce uygulamaları için bir Istemci bilgisayara güvenilir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Kod Erişim Güvenliği İlkeleri  
 Bir uygulama için izinler, uygulama bildiriminin [ \<trustInfo> öğe](../deployment/trustinfo-element-clickonce-application.md) öğesindeki ayarlara göre belirlenir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Bu bilgileri projenin **güvenlik** özelliği sayfasındaki ayarlara göre otomatik olarak oluşturur. Bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamaya yalnızca istediği belirli izinler verilir. Örneğin, dosya erişiminin tam güven izinlerini gerektirdiği yerde uygulama tam güven izinleri isterse, uygulamaya tam güven izinleri değil de sadece dosya erişim izni verilir. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Uygulamanızı geliştirirken yalnızca uygulamanın ihtiyacı olan belirli izinleri istediğinizden emin olun. Çoğu durumda, uygulamanızı kısmi güvenle sınırlamak için Internet veya yerel Intranet bölgelerini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulaması Için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Uygulamanız özel izinleri gerektiriyorsa, özel bir bölge oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulaması Için özel Izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Uygulamanın dağıtıldığı bölge için varsayılan izin kümesinin parçası olmayan bir izni dahil etme, son kullanıcının güncelleme ve yükleme zamanında iznin verilmesi için uyarılmasına sebep olur. Kullanıcıların uyarılmasını önlemek için, sistem yöneticisi belirli bir uygulama yayımcısını güvenilir kaynak olarak tanımlayan bir ClickOnce dağıtım ilkesi belirtebilir. Bu ilkenin dağıtılmış olduğu bilgisayarlar üzerinde, izinler otomatik olarak verilecek ve kullanıcı uyarılmayacaktır.  
  
 Geliştirici olarak, uygulamanızın uygun izinlerle çalıştığından emin olmak sizin sorumluluğunuzdur. Uygulama çalışma zamanı sırasında bir bölge dışında izinler isterse, güvenlik özel durumu ortaya çıkabilir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Hedef güvenlik bölgesinde uygulamanızın hatalarını ayıklamanızı sağlar. ve güvenli uygulamalar geliştirmeye yönelik yardım sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: kısıtlanmış Izinlerle ClickOnce uygulamasında hata ayıklama](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Kod erişimi güvenliği ve ClickOnce hakkında daha fazla bilgi için bkz. [ClickOnce uygulamaları Için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Kod İmzalama Sertifikaları  
 Dağıtım kullanarak bir uygulamayı yayımlamak için [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , ortak/özel anahtar çiftini kullanarak uygulama için uygulama ve dağıtım bildirimlerini imzalayabilirsiniz. Bir bildirimi imzalama araçları, **Proje Tasarımcısı**' nın **imzalama** sayfasında kullanılabilir. Daha fazla bilgi için bkz. [Imzalama sayfası, proje Tasarımcısı](../ide/reference/signing-page-project-designer.md). Alternatif olarak, Yayımlama Sihirbazı 'nı kullanarak, yayımlama işlemi sırasında bildirimleri bir anahtar dosyası ile imzalayabilirsiniz.  
  
 Bildirimler imzalandıktan sonra, Authenticode imzasına bağlı yayımcı bilgisi uygulamanın güvenilir bir kaynaktan olduğunu kullanıcıya göstermek için izinler iletişim kutusunda gösterilir.  
  
 ClickOnce ve sertifikalar hakkında daha fazla bilgi için bkz. [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>ASP.NET Form Tabanlı Kimlik Doğrulaması  
 Her bir kullanıcının hangi dağıtımlara erişebileceğini denetlemek isterseniz, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bir Web sunucusunda dağıtılan uygulamalara anonim erişimi etkinleştirmemelisiniz. Alternatif olarak, kullanıcı erişimini bir kullanıcı kimliği üzerinde yüklenmiş dağıtımlar için, Windows kimlik doğrulaması kullanarak etkinleştirebilirsiniz.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] kalıcı tanımlama bilgileri kullandığından ASP.NET form tabanlı kimlik doğrulamasını desteklemez; Bunlar Internet Explorer önbelleğinde olduklarından bir güvenlik riskine neden olur ve bu da etkinleştirilebilir. Bu nedenle, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama dağıtıyorsanız, Windows kimlik doğrulamasının yanı sıra herhangi bir kimlik doğrulama senaryosu desteklenmez.  
  
## <a name="passing-arguments"></a>Bağımsız Değişkenleri Geçirme  
 Bağımsız değişkenleri bir uygulamaya geçirmeniz gerekiyorsa ek bir güvenlik değerlendirmesi oluşur [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] geliştiricilerin Web üzerinde dağıtılan uygulamalara bir sorgu dizesi vermesini sağlar. Sorgu dizesi, uygulamayı başlatmak için kullanılan URL'nin sonunda bir dizi ad-değer çiftleri şeklini alır:  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Varsayılan olarak, sorgu dizesi bağımsız değişkenleri devre dışıdır. Bunları etkinleştirmek için, özniteliğin `trustUrlParameters` uygulamanın dağıtım bildiriminde ayarlanması gerekir. Bu değer, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] MageUI.exe 'den ve öğesinden ayarlanabilir. Sorgu dizelerini geçirmeyi etkinleştirme hakkında ayrıntılı adımlar için bkz. [nasıl yapılır: sorgu dizesi bilgilerini bir çevrimiçi ClickOnce uygulamasında alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 Bir komut satırı veya veritabanı için olan sorgu dizesi aracılığıyla elde edilen bağımsız değişkenleri güvenli oldukları konusunda emin olmadan geçirmeyin. Güvenli olmayan bağımsız değişkenler rasgele komutları çalıştırarak uygulamanızı yönetmek için kötü amaçlı kullanıcılara izin verebilecek veritabanı ve komut satırı kaçış karakterlerini içeren dizelerdir.  
  
> [!NOTE]
> Sorgu dizesi bağımsız değişkenleri, başlatma sırasında bir uygulamaya bağımsız değişkenleri geçirmenin tek yoludur [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Komut satırından bir uygulamaya bağımsız değişken geçirilemez [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
## <a name="deploying-obfuscated-assemblies"></a>Gizlenmiş (Obfuscated) Derlemeleri Dağıtma  
 Başkaları tarafından kod üzerine tersine mühendislik yapılmasını engellemek için Dotfuscator kullanarak uygulamanızı gizleyebilirsiniz. Bunun yanında, derleme gizleme Visual Studio IDE veya ClickOnce dağıtım sürecine tümleşikleştirilmemiştir. Bu nedenle, gizleme işlemini dağıtım sürecinin dışında belki bir bağlama sonrası adımı kullanarak gerçekleştirebilirsiniz. Projeyi derledikten sonra, aşağıdaki adımları Visual Studio'nun dışında el ile gerçekleştirmelisiniz.  
  
1. Dotfuscator kullanarak gizlemeyi yapın.  
  
2. ClickOnce bildirimleri oluşturmak ve bunları imzalamak için Mage.exe veya MagUI.exe kullanın. Daha fazla bilgi için bkz. [Mage.exe (bildirim oluşturma ve düzenleme aracı)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) ve [MageUI.exe (bildirim oluşturma ve düzenleme aracı, grafik istemci)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
3. El ile dosyaları dağıtım kaynağı konumuna (Web sunucusu, UNC paylaşımı veya CD-ROM) yayımlayın. (Kopyalayın.)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce Dağıtım Stratejisini Seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)
