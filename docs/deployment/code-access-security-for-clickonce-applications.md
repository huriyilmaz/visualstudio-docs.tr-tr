---
title: ClickOnce Uygulamaları için Kod Erişim Güvenliği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vb.XBAPProjectPropertiesSecurity.HowTo
- vb.XBAProjectPropertiesSecurity.HowTo
- vb.ProjectPropertiesSecurity.HowTo
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], security
- ClickOnce applications, caspol
- security [ClickOnce], WPF browser-hosted applications
- security [ClickOnce], ClickOnce applications
- ClickOnce applications, code access security policies
- security, ClickOnce
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fd2d9b6792cae002967c9000474a825bd3a0651
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649271"
---
# <a name="code-access-security-for-clickonce-applications"></a>ClickOnce uygulamaları için kod erişimi güvenliği
ClickOnce uygulamaları .NET Framework'e dayanır ve kod erişim güvenlik kısıtlamalarına tabidir. Bu nedenle, kod erişim güvenliğinin etkilerini anlamanız ve ClickOnce uygulamalarınızı buna göre yazmanız önemlidir.

 Kod erişim güvenliği,.NET Framework'de, kodun korumalı kaynaklara ve işlemlere erişimini sınırlamaya yardımcı olan bir mekanizmadır. Uygulama yükleyicisinin konumuna uygun bölgeyi kullanmak için ClickOnce uygulamanızın kod erişim güvenlik izinlerini yapılandırmanız gerekir. Çoğu durumda, sınırlı bir izin kümesi için **Internet** bölgesini veya daha büyük bir izin kümesi için **Yerel Intranet** bölgesini seçebilirsiniz.

## <a name="default-clickonce-code-access-security"></a>Varsayılan ClickOnce kod erişim güvenliği
 Varsayılan olarak, ClickOnce uygulaması bir istemci bilgisayarda yüklendiğinde veya çalıştırıldığında Tam Güven izinleri alır.

- Tam Güven izinlerine sahip bir uygulama, dosya sistemi ve kayıt defteri gibi kaynaklara sınırsız erişime sahiptir. Bu, uygulamanızın (ve son kullanıcının sisteminin) kötü amaçlı kodtarafından istismar edilmesine olanak sağlar.

- Bir uygulama Tam Güven izinleri gerektiriyorsa, son kullanıcıdan uygulamaya izin vermesi istenebilir. Bu, uygulamanın gerçekten bir ClickOnce deneyimi sağlamadığı ve komut isteminin daha az deneyimli kullanıcılar için kafa karıştırıcı olabileceği anlamına gelir.

  > [!NOTE]
  > CD-ROM gibi çıkarılabilir ortamlardan bir uygulama yüklerken, kullanıcıdan istenmez. Ayrıca, ağ yöneticisi, kullanıcıların güvenilir bir kaynaktan bir uygulama yüklediklerinde istenmemesi için ağ ilkesini yapılandırabilir. Daha fazla bilgi için bkz: [Güvenilen uygulama dağıtımına genel bakış.](../deployment/trusted-application-deployment-overview.md)

  ClickOnce uygulamasının izinlerini kısıtlamak için, uygulamanızın gerektirdiği izinlere en uygun bölgeyi istemek için uygulamanızın kod erişim güvenlik izinlerini değiştirebilirsiniz. Çoğu durumda, uygulamanın dağıtıldığı bölgeyi seçebilirsiniz. Örneğin, uygulamanız kurumsal bir uygulamaysa, **Yerel Intranet** bölgesini kullanabilirsiniz. Uygulamanız bir internet uygulamasıysa, **Internet** bölgesini kullanabilirsiniz.

## <a name="configure-security-permissions"></a>Güvenlik izinlerini yapılandırma
 Kod erişim güvenlik izinlerini sınırlamak için uygun bölgeyi istemek için ClickOnce uygulamanızı her zaman yapılandırmanız gerekir. Güvenlik izinlerini **Proje Tasarımcısı'nın** **Güvenlik** sayfasında yapılandırabilirsiniz.

 **Project Designer'daki** **Güvenlik** sayfası, **Güvenlik Ayarlarını Etkinleştir** onay kutusunu içerir. Bu onay kutusu seçildiğinde, uygulamanız için dağıtım bildirimine güvenlik izni istekleri eklenir. Yükleme sırasında, istenen izinler uygulamanın dağıtıldığı bölge için varsayılan izinleri aşarsa, kullanıcıdan izin vermesi istenir. Daha fazla bilgi için [bkz: ClickOnce güvenlik ayarlarını etkinleştirin.](../deployment/how-to-enable-clickonce-security-settings.md)

 Farklı konumlardan dağıtılan uygulamalara istenmeden farklı düzeylerde izin verilir. Örneğin, bir uygulama Internet'ten dağıtıldığında, son derece kısıtlayıcı bir izin kümesi alır. Yerel bir Intranet'ten yüklendiğinde, daha fazla izin alır ve bir CD-ROM'dan yüklendiğinde Tam Güven izinleri alır.

 İzinleri yapılandırmak için bir başlangıç noktası olarak, **Güvenlik** sayfasındaki **Bölge** listesinden bir güvenlik bölgesi seçebilirsiniz. Uygulamanız birden fazla bölgeden dağıtılacaksa, en az izine sahip bölgeyi seçin. Daha fazla bilgi için [bkz: ClickOnce uygulaması için bir güvenlik bölgesi ayarlayın.](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)

 Ayarlanabilen özellikler izin kümesine göre değişir; tüm izin kümelerinin yapılabilen özellikleri yoktur. Uygulamanızın isteyebileceği izinlerin tam listesi hakkında daha <xref:System.Security.Permissions>fazla bilgi için bkz. Özel bir bölge için izinlerin nasıl ayarlan da olduğu hakkında daha fazla bilgi için [bkz.](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)

## <a name="debug-an-application-that-has-restricted-permissions"></a>İzinleri kısıtlayan bir uygulamayı hata ayıklama
 Geliştirici olarak, geliştirme bilgisayarınızı büyük olasılıkla Full Trust izinleriyle çalıştırın. Bu nedenle, kullanıcıların sınırlı izinlerle çalıştırdıklarında görebileceği uygulamayı hata ayıklama yaptığınızda aynı güvenlik özel durumlarını görmezsiniz.

 Bu özel durumları yakalamak için, uygulamayı son kullanıcıyla aynı izinlerle hata ayıklamanız gerekir. Kısıtlı izinlerle hata **ayıklama, Project Designer'ın** **Güvenlik** sayfasında etkinleştirilebilir.

 Kısıtlanmış izinlere sahip bir uygulamayı hata ayıklama yaptığınızda, **Güvenlik** sayfasında etkinleştirilmeyen kod güvenliği talepleri için özel durumlar yükseltilir. Özel durumu önlemek için kodunuzu nasıl değiştireceğiniz hakkında öneriler sağlayan bir özel durum yardımcısı görüntülenir.

 Ayrıca, kod yazdığınızda, Kod Düzenleyicisi'ndeki IntelliSense özelliği, yapılandırdığınız güvenlik izinlerine dahil olmayan tüm üyeleri devre dışı bırakmaz.

 Daha fazla bilgi için [bkz: Kısıtlı İzinlerle ClickOnce Uygulamasını Hata ayıklama.](securing-clickonce-applications.md)

## <a name="security-permissions-for-browser-hosted-applications"></a>Tarayıcı tarafından barındırılan uygulamalar için güvenlik izinleri
 Visual Studio, Windows Presentation Foundation (WPF) uygulamaları için aşağıdaki proje türlerini sağlar:

- WPF Windows Uygulaması

- WPF Web TarayıcıSı Uygulaması

- WPF Özel Denetim Kitaplığı

- WPF Hizmet Kütüphanesi

  Bu proje türlerinin yalnızca WPF Web Tarayıcısı Uygulamaları bir Web tarayıcısında barındırılır ve bu nedenle özel dağıtım ve güvenlik ayarları gerektirir. Bu uygulamalar için varsayılan güvenlik ayarları aşağıdaki gibidir:

- **ClickOnce Güvenlik Ayarlarını Etkinleştir**

- **Bu kısmi bir güven uygulamasıdır**

- **Internet bölgesi** (WPF Web Tarayıcısı Uygulamaları için varsayılan izin ayarlanmış)

  Gelişmiş **Güvenlik Ayarları** iletişim kutusunda, seçili izin kümesi onay kutusunu **içeren bu uygulamayı hata ayıklama** seçilir ve devre dışı bırakılır. Bunun nedeni, Tarayıcı tarafından barındırılan uygulamalar için Hata Ayıklama Bölgesinde kapatılamaz olmasıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [Nasıl Yapılır: ClickOnce güvenlik ayarlarını etkinleştirin](../deployment/how-to-enable-clickonce-security-settings.md)
- [Nasıl yapilir: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Nasıl yapılsın: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Nasıl?](securing-clickonce-applications.md)
- [Güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)
- [Güvenlik Sayfası, Proje Tasarımcısı](../ide/reference/security-page-project-designer.md)