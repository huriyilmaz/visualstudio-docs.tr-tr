---
title: ClickOnce uygulamaları için kod erişimi güvenliği | Microsoft Docs
description: ClickOnce uygulamaları için kod erişimi güvenliği ve kod erişimi güvenlik izinlerinin nasıl yapılandırılacağı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4bf2977b3b6875a7dc38711b235f5848aa78559e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889167"
---
# <a name="code-access-security-for-clickonce-applications"></a>ClickOnce uygulamaları için kod erişimi güvenliği
ClickOnce uygulamaları .NET Framework tabanlıdır ve kod erişimi güvenlik kısıtlamalarına tabidir. Bu nedenle, kod erişimi güvenliğinin etkilerini anlamanız ve ClickOnce uygulamalarınızı buna göre yazmanız önemlidir.

 Kod erişimi güvenliği, kod üzerinde korunan kaynaklara ve işlemlere erişimi sınırlamaya yardımcı olan .NET Framework bir mekanizmadır. ClickOnce uygulamanız için kod erişimi güvenlik izinlerini, uygulama yükleyicisinin konumuna uygun bölgeyi kullanacak şekilde yapılandırmanız gerekir. Çoğu durumda, daha fazla izin kümesi için sınırlı bir izin kümesi veya **Yerel Intranet** bölgesi için **Internet** bölgesini seçebilirsiniz.

## <a name="default-clickonce-code-access-security"></a>Varsayılan ClickOnce kod erişim güvenliği
 Varsayılan olarak, bir ClickOnce uygulaması, bir istemci bilgisayarda yüklendiğinde veya çalıştırıldığında tam güven izinleri alır.

- Tam güven izinlerine sahip bir uygulama, dosya sistemi ve kayıt defteri gibi kaynaklara Kısıtlanmamış erişime sahiptir. Bu potansiyel olarak uygulamanızın (ve son kullanıcının sistemine) kötü amaçlı kod tarafından yararlanmasına olanak tanır.

- Bir uygulama tam güven izinleri gerektirdiğinde, son kullanıcıdan uygulamaya izin vermesi istenebilir. Bu, uygulamanın gerçekten bir ClickOnce deneyimi sağlamaması ve istemin daha az deneyimli kullanıcılar için kafa karıştırıcı olabileceği anlamına gelir.

  > [!NOTE]
  > CD-ROM gibi çıkarılabilir medyadan bir uygulama yüklerken, kullanıcıya istenmez. Buna ek olarak, bir ağ yöneticisi, kullanıcıların güvenilen bir kaynaktan bir uygulama yüklediklerinde sorulmaması için ağ ilkesini yapılandırabilir. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).

  Bir ClickOnce uygulaması için izinleri kısıtlamak amacıyla, uygulamanız için kod erişimi güvenlik izinlerini, uygulamanızın gerektirdiği izinlere en uygun bölgeyi isteyecek şekilde değiştirebilirsiniz. Çoğu durumda, uygulamanın dağıtıldığı bölgeyi seçebilirsiniz. Örneğin, uygulamanız bir kurumsal uygulama ise, **Yerel Intranet** bölgesini kullanabilirsiniz. Uygulamanız bir Internet uygulaması ise, **İnternet** alanını kullanabilirsiniz.

## <a name="configure-security-permissions"></a>Güvenlik izinlerini yapılandırma
 Her zaman ClickOnce uygulamanızı, kod erişimi güvenlik izinlerini sınırlamak üzere uygun bölgeyi isteyecek şekilde yapılandırmanız gerekir. **Proje Tasarımcısı**'nın **güvenlik** sayfasında güvenlik izinlerini yapılandırabilirsiniz.

 **Proje Tasarımcısı** 'ndaki **güvenlik** sayfasında **ClickOnce güvenlik ayarlarını etkinleştir** onay kutusu bulunur. Bu onay kutusu seçildiğinde, uygulamanız için dağıtım bildirimine güvenlik izin istekleri eklenir. Yükleme zamanında, istenen izinler uygulamanın dağıtıldığı bölge için varsayılan izinleri aşarsa kullanıcıdan izin vermesi istenir. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md).

 Farklı konumlardan dağıtılan uygulamalara, sormadan farklı düzeylerde izinler verilir. Örneğin, bir uygulama Internet 'ten dağıtıldığında, yüksek oranda kısıtlayıcı bir izin kümesi alır. Yerel Intranetten yüklendiğinde, daha fazla izin alır ve bir CD-ROM ' d a n yüklendiğinde, tam güven izinleri alır.

 İzinleri yapılandırmaya yönelik bir başlangıç noktası olarak, **güvenlik** sayfasındaki **bölge** listesinden bir güvenlik bölgesi seçebilirsiniz. Uygulamanız potansiyel olarak birden fazla bölgeden dağıtılırsa, en az izinlere sahip bölgeyi seçin. Daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulaması için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).

 Ayarlanabilir Özellikler izin kümesine göre farklılık gösterir; Tüm izin kümelerinde yapılandırılabilir özellikler yoktur. Uygulamanızın isteyebileceği izinlerin tam listesi hakkında daha fazla bilgi için bkz <xref:System.Security.Permissions> .. Özel bir bölgeye yönelik izinlerin nasıl ayarlanacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulaması için özel Izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

## <a name="debug-an-application-that-has-restricted-permissions"></a>Kısıtlanmış izinlere sahip bir uygulamada hata ayıklama
 Bir geliştirici olarak, büyük ihtimalle geliştirme bilgisayarınızı tam güven izinleriyle çalıştıracaksınız. Bu nedenle, kullanıcıların kısıtlı izinlerle çalıştıklarında görebileceği uygulamanın hatalarını ayıkladığınızda aynı güvenlik özel durumlarını görmezsiniz.

 Bu özel durumları yakalamak için, uygulamayı son kullanıcıyla aynı izinlerle ayıklamanız gerekir. Kısıtlanmış izinlerle hata ayıklama, **Proje Tasarımcısı**'nın **güvenlik** sayfasında etkinleştirilebilir.

 Kısıtlanmış izinlerle bir uygulamada hata ayıklarken, **güvenlik** sayfasında etkinleştirilmemiş tüm kod güvenliği talepleri için özel durumlar tetiklenir. Özel durumu engellemek için kodunuzun nasıl değiştirileceği hakkında öneriler sağlayan bir özel durum Yardımcısı görüntülenir.

 Ayrıca, kod yazdığınızda, kod düzenleyicisinde IntelliSense özelliği yapılandırdığınız güvenlik izinlerine dahil olmayan tüm üyeleri devre dışı bırakır.

 Daha fazla bilgi için bkz. [nasıl yapılır: kısıtlanmış Izinlerle ClickOnce uygulamasında hata ayıklama](securing-clickonce-applications.md).

## <a name="security-permissions-for-browser-hosted-applications"></a>Tarayıcıda barındırılan uygulamalar için güvenlik izinleri
 Visual Studio, Windows Presentation Foundation (WPF) uygulamaları için aşağıdaki proje türlerini sağlar:

- WPF Windows uygulaması

- WPF Web tarayıcısı uygulaması

- WPF Özel Denetim Kitaplığı

- WPF hizmet kitaplığı

  Bu proje türlerinde, yalnızca WPF Web tarayıcı uygulamaları bir Web tarayıcısında barındırılır ve bu nedenle özel dağıtım ve güvenlik ayarları gerektirir. Bu uygulamalar için varsayılan güvenlik ayarları aşağıdaki gibidir:

- **ClickOnce güvenlik ayarlarını etkinleştir**

- **Bu bir kısmi güven uygulamasıdır**

- **Internet bölgesi** (WPF Web tarayıcı uygulamaları için varsayılan izin kümesi seçiliyken)

  **Gelişmiş güvenlik ayarları** iletişim kutusunda, **Bu uygulamanın seçili Izin kümesiyle hata ayıkla** onay kutusu seçilidir ve devre dışı bırakılır. Bunun nedeni, bölgedeki hata ayıklamanın tarayıcıda barındırılan uygulamalar için devre dışı bırakılamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [Nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md)
- [Nasıl yapılır: ClickOnce uygulaması için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Nasıl yapılır: kısıtlanmış izinlerle ClickOnce uygulamasında hata ayıklama](securing-clickonce-applications.md)
- [Güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)
- [Güvenlik Sayfası, Proje Tasarımcısı](../ide/reference/security-page-project-designer.md)