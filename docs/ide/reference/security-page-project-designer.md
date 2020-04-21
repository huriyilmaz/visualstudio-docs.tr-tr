---
title: Güvenlik Sayfası, Proje Tasarımcısı
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 272d37ef9e73aa5dd0d10ca0210b18a945f993fd
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649832"
---
# <a name="security-page-project-designer"></a>Güvenlik Sayfası, Proje Tasarımcısı

**Project Designer'ın** **Güvenlik** sayfası, ClickOnce dağıtımını kullanarak dağıtılan uygulamalar için kod erişim güvenlik ayarlarını yapılandırmak için kullanılır. Daha fazla bilgi [için ClickOnce Uygulamaları için Kod Erişim Güvenliği'ne](../../deployment/code-access-security-for-clickonce-applications.md)bakın.

**Güvenlik** sayfasına erişmek için **Çözüm Gezgini'nde**bir proje düğümüne tıklayın ve ardından **Proje** menüsünde **Özellikler'i**tıklatın. Proje **Tasarımcısı** göründüğünde Güvenlik **sekmesini** tıklatın.

## <a name="security-settings"></a>Güvenlik Ayarları

 **ClickOnce Güvenlik Ayarlarını Etkinleştir**

Tasarım zamanında güvenlik ayarlarının etkin olup olmadığını belirler. Bu seçenek temizlendiğinde, **Güvenlik** sayfasındaki diğer tüm seçenekler kullanılamaz.

> [!NOTE]
> **Yayımla** sihirbazını kullanarak bir uygulama yayımladığınızda, bu seçenek otomatik olarak etkinleştirilir.

Bu seçeneği seçtiğinizde, iki radyo düğmesinden birini seçme seçeneğiniz vardır: **Bu tam bir güven uygulamasıdır** veya kısmi bir güven **uygulamasıdır.**

Varsayılan olarak, WPF Web Tarayıcısı Uygulaması projeleri için bu seçenek seçilir.

Varsayılan olarak, diğer tüm proje türleri için bu seçenek temizlenir.

 **Bu tam bir güven uygulamasıdır**

Bu seçeneği seçerseniz, uygulama bir istemci bilgisayarda yüklendiğinde veya çalıştırıldığında Tam Güven izinleri ister. Uygulamanız dosya sistemi ve kayıt defteri gibi kaynaklara sınırsız erişim hakkı tanıyacaktır, çünkü mümkünse Tam Güven kullanmaktan kaçının.

Varsayılan olarak, WPF Web Tarayıcısı Uygulaması projeleri için bu seçenek Kısmi Güven olarak ayarlanır.

Varsayılan olarak, diğer tüm proje türleri için bu seçenek Tam Güven olarak ayarlanır.

 **Bu kısmi bir güven uygulamasıdır**

Bu seçeneği seçerseniz, uygulama bir istemci bilgisayarda yüklendiğinde veya çalıştırıldığında Kısmi Güven izinleri ister. *Kısmi Güven,* yalnızca istenen kod erişim güvenlik izinleri altında izin verilen eylemlerin çalışacağı anlamına gelir. Güvenlik izinlerinin nasıl yapılandırılabildiğini hakkında daha fazla bilgi için [ClickOnce Uygulamaları için Kod Erişim Güvenliği'ne](../../deployment/code-access-security-for-clickonce-applications.md)bakın.

**ClickOnce Güvenlik İzinleri** alanındaki seçenekleri yapılandırarak Kısmi Güven güvenlik ayarlarını belirtebilirsiniz.

## <a name="clickonce-security-permissions"></a>ClickOnce Güvenlik İzinleri

 **Uygulamanızın yüklenecek**

Varsayılan kod erişim güvenlik izinleri kümesini belirtir. Sınırlı bir izin kümesi için **Internet** veya **Yerel Intranet'i** seçin veya özel izin kümesini yapılandırmak için **(Özel)** seçin. Uygulama bir bölgede verilenden daha fazla izin isterse, son kullanıcının ek izinleri vermesi için clickonce güven istemi görüntülenir. Güvenlik izinlerinin nasıl yapılandırılabildiğini hakkında daha fazla bilgi için [ClickOnce Uygulamaları için Kod Erişim Güvenliği'ne](../../deployment/code-access-security-for-clickonce-applications.md)bakın.

Varsayılan olarak, WPF Web Tarayıcısı Uygulaması projeleri için bu seçenek **Internet**olarak ayarlanır.

 **İzinleri XML'i Edin**

**(Özel)** izin kümesinin izinlerini yapılandırmak için uygulama bildirimi şablonu (app.manifest) açılır.

 **Gelişmiş**

Uygulamanın hata ayıklama ayarlarını kısıtlı izinlerle yapılandırmak için kullanılan [Gelişmiş Güvenlik Ayarları İletişim Kutusu'nu](../../ide/reference/advanced-security-settings-dialog-box.md)açar. Bu ayarlar hata ayıklama sırasında denetlenir ve izin özel durumları uygulamanızın bir bölgede tanımlanandan daha fazla izine ihtiyaç duyabileceğini gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [ClickOnce Uygulamaları için Kod Erişim Güvenliği](../../deployment/code-access-security-for-clickonce-applications.md)
- [Nasıl yapılır: ClickOnce Güvenlik Ayarlarını Etkinleştirme](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Nasıl yapılır: ClickOnce Uygulaması için Bir Güvenlik Bölgesi Ayarlama](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Nasıl yapılır: ClickOnce Uygulaması için Özel İzinleri Ayarlama](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Güvenli ClickOnce uygulamaları](../../deployment/securing-clickonce-applications.md)
- [ClickOnce Güvenlik ve Dağıtım](../../deployment/clickonce-security-and-deployment.md)
- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Gelişmiş Güvenlik Ayarları İletişim Kutusu](../../ide/reference/advanced-security-settings-dialog-box.md)
