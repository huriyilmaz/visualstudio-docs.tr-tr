---
title: ClickOnce uygulamalar için kod erişimi güvenliği | Microsoft Docs
description: ClickOnce uygulamalar için kod erişimi güvenliği ve kod erişimi güvenlik izinlerinin nasıl yapılandırılacağı hakkında bilgi edinin.
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
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 1d60cc8e982e094a3deff406763c234c755a1c32
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153751"
---
# <a name="code-access-security-for-clickonce-applications"></a>ClickOnce uygulamaları için kod erişimi güvenliği
ClickOnce uygulamalar .NET Framework tabanlıdır ve kod erişimi güvenlik kısıtlamalarına tabidir. bu nedenle, kod erişimi güvenliğinin etkilerini anlamanız ve ClickOnce uygulamalarınızı buna göre yazmanız önemlidir.

 kod erişimi güvenliği, kod üzerinde korunan kaynaklara ve işlemlere erişimi sınırlamaya yardımcı olan .NET Framework bir mekanizmadır. ClickOnce uygulamanız için kod erişimi güvenlik izinlerini, uygulama yükleyicisinin konumuna uygun bölgeyi kullanacak şekilde yapılandırmanız gerekir. Çoğu durumda, daha fazla izin kümesi için sınırlı bir izin kümesi veya **Yerel Intranet** bölgesi için **Internet** bölgesini seçebilirsiniz.

## <a name="default-clickonce-code-access-security"></a>varsayılan ClickOnce kod erişim güvenliği
 varsayılan olarak, bir ClickOnce uygulama bir istemci bilgisayarda yüklendiğinde veya çalıştırıldığında tam güven izinleri alır.

- Tam güven izinlerine sahip bir uygulama, dosya sistemi ve kayıt defteri gibi kaynaklara Kısıtlanmamış erişime sahiptir. Bu potansiyel olarak uygulamanızın (ve son kullanıcının sistemine) kötü amaçlı kod tarafından yararlanmasına olanak tanır.

- Bir uygulama tam güven izinleri gerektirdiğinde, son kullanıcıdan uygulamaya izin vermesi istenebilir. bu, uygulamanın gerçekten ClickOnce bir deneyim sağlamamasıdır ve istem daha az deneyimli kullanıcılar için kafa karıştırıcı olabilir.

  > [!NOTE]
  > CD-ROM gibi çıkarılabilir medyadan bir uygulama yüklerken, kullanıcıya istenmez. Buna ek olarak, bir ağ yöneticisi, kullanıcıların güvenilen bir kaynaktan bir uygulama yüklediklerinde sorulmaması için ağ ilkesini yapılandırabilir. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).

  ClickOnce bir uygulamayla ilgili izinleri kısıtlamak için, uygulamanız için kod erişimi güvenlik izinlerini, uygulamanızın gerektirdiği izinlere en uygun bölgeyi isteyecek şekilde değiştirebilirsiniz. Çoğu durumda, uygulamanın dağıtıldığı bölgeyi seçebilirsiniz. Örneğin, uygulamanız bir kurumsal uygulama ise, **Yerel Intranet** bölgesini kullanabilirsiniz. Uygulamanız bir Internet uygulaması ise, **İnternet** alanını kullanabilirsiniz.

## <a name="configure-security-permissions"></a>Güvenlik izinlerini yapılandırma
 kod erişimi güvenlik izinlerini sınırlamak üzere ClickOnce uygulamanızı her zaman uygun bölgeyi isteyecek şekilde yapılandırmanız gerekir. **Project tasarımcısının** **güvenlik** sayfasında güvenlik izinlerini yapılandırabilirsiniz.

 **Project tasarımcısında** **güvenlik** sayfasında **ClickOnce güvenliği etkinleştir Ayarlar** onay kutusu bulunur. Bu onay kutusu seçildiğinde, uygulamanız için dağıtım bildirimine güvenlik izin istekleri eklenir. Yükleme zamanında, istenen izinler uygulamanın dağıtıldığı bölge için varsayılan izinleri aşarsa kullanıcıdan izin vermesi istenir. daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md).

 Farklı konumlardan dağıtılan uygulamalara, sormadan farklı düzeylerde izinler verilir. Örneğin, bir uygulama Internet 'ten dağıtıldığında, yüksek oranda kısıtlayıcı bir izin kümesi alır. Yerel Intranetten yüklendiğinde, daha fazla izin alır ve bir CD-ROM ' d a n yüklendiğinde, tam güven izinleri alır.

 İzinleri yapılandırmaya yönelik bir başlangıç noktası olarak, **güvenlik** sayfasındaki **bölge** listesinden bir güvenlik bölgesi seçebilirsiniz. Uygulamanız potansiyel olarak birden fazla bölgeden dağıtılırsa, en az izinlere sahip bölgeyi seçin. daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce bir uygulama için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).

 Ayarlanabilir Özellikler izin kümesine göre farklılık gösterir; Tüm izin kümelerinde yapılandırılabilir özellikler yoktur. Uygulamanızın isteyebileceği izinlerin tam listesi hakkında daha fazla bilgi için bkz <xref:System.Security.Permissions> .. özel bir bölgeye yönelik izinlerin nasıl ayarlanacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel izinleri ayarlama ClickOnce bir uygulama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

## <a name="debug-an-application-that-has-restricted-permissions"></a>Kısıtlanmış izinlere sahip bir uygulamada hata ayıklama
 Bir geliştirici olarak, büyük ihtimalle geliştirme bilgisayarınızı tam güven izinleriyle çalıştıracaksınız. Bu nedenle, kullanıcıların kısıtlı izinlerle çalıştıklarında görebileceği uygulamanın hatalarını ayıkladığınızda aynı güvenlik özel durumlarını görmezsiniz.

 Bu özel durumları yakalamak için, uygulamayı son kullanıcıyla aynı izinlerle ayıklamanız gerekir. kısıtlanmış izinlerle hata ayıklama **Project tasarımcısının** **güvenlik** sayfasında etkinleştirilebilir.

 Kısıtlanmış izinlerle bir uygulamada hata ayıklarken, **güvenlik** sayfasında etkinleştirilmemiş tüm kod güvenliği talepleri için özel durumlar tetiklenir. Özel durumu engellemek için kodunuzun nasıl değiştirileceği hakkında öneriler sağlayan bir özel durum Yardımcısı görüntülenir.

 Ayrıca, kod yazdığınızda, kod düzenleyicisinde IntelliSense özelliği yapılandırdığınız güvenlik izinlerine dahil olmayan tüm üyeleri devre dışı bırakır.

 daha fazla bilgi için bkz. [nasıl yapılır: kısıtlanmış izinlerle ClickOnce bir uygulamada hata ayıklama](securing-clickonce-applications.md).

## <a name="security-permissions-for-browser-hosted-applications"></a>Tarayıcıda barındırılan uygulamalar için güvenlik izinleri
 Visual Studio, Windows Presentation Foundation (WPF) uygulamaları için aşağıdaki proje türlerini sağlar:

- WPF Windows uygulaması

- WPF Web tarayıcısı uygulaması

- WPF Özel Denetim Kitaplığı

- WPF hizmet kitaplığı

  Bu proje türlerinde, yalnızca WPF Web tarayıcı uygulamaları bir Web tarayıcısında barındırılır ve bu nedenle özel dağıtım ve güvenlik ayarları gerektirir. Bu uygulamalar için varsayılan güvenlik ayarları aşağıdaki gibidir:

- **ClickOnce güvenlik Ayarlar etkinleştir**

- **Bu bir kısmi güven uygulamasıdır**

- **Internet bölgesi** (WPF Web tarayıcı uygulamaları için varsayılan izin kümesi seçiliyken)

  **gelişmiş güvenlik Ayarlar** iletişim kutusunda, **bu uygulamanın seçili izin kümesiyle hata ayıkla** onay kutusu seçilidir ve devre dışı bırakılır. Bunun nedeni, bölgedeki hata ayıklamanın tarayıcıda barındırılan uygulamalar için devre dışı bırakılamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md)
- [nasıl yapılır: ClickOnce bir uygulama için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [nasıl yapılır: bir ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [nasıl yapılır: kısıtlanmış izinlerle ClickOnce bir uygulamada hata ayıklama](securing-clickonce-applications.md)
- [Güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)
- [Güvenlik Sayfası, Proje Tasarımcısı](../ide/reference/security-page-project-designer.md)