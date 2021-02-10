---
title: Güvenlik Sayfası, Proje Tasarımcısı
description: Proje Tasarımcısı 'nın güvenlik sayfası, ClickOnce dağıtımı kullanılarak dağıtılan uygulamalar için kod erişimi güvenlik ayarlarını yapılandırmak üzere kullanılır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 426179eb20fcb71ac02039c3b2be20dab6f685b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957861"
---
# <a name="security-page-project-designer"></a>Güvenlik Sayfası, Proje Tasarımcısı

**Proje Tasarımcısı** 'nın **güvenlik** sayfası, ClickOnce dağıtımı kullanılarak dağıtılan uygulamalar için kod erişimi güvenlik ayarlarını yapılandırmak üzere kullanılır. Daha fazla bilgi için bkz. [ClickOnce uygulamaları Için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).

**Güvenlik** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümüne tıklayın ve ardından **Proje** menüsünde **Özellikler**' e tıklayın. **Proje Tasarımcısı** göründüğünde, **güvenlik** sekmesine tıklayın.

## <a name="security-settings"></a>Güvenlik Ayarları

 **ClickOnce güvenlik ayarlarını etkinleştir**

Tasarım zamanında güvenlik ayarlarının etkinleştirilip etkinleştirilmeyeceğini belirler. Bu seçenek silinirse, **güvenlik** sayfasındaki diğer tüm seçenekler kullanılamaz.

> [!NOTE]
> **Yayımla** sihirbazını kullanarak bir uygulamayı yayımladığınızda, bu seçenek otomatik olarak etkinleştirilir.

Bu seçeneği belirlediğinizde, iki radyo düğmesinden birini seçme seçeneğiniz vardır: **Bu bir tam güven uygulamasıdır** veya **Bu bir kısmi güven uygulamasıdır**.

Varsayılan olarak, WPF Web tarayıcısı uygulama projeleri için bu seçenek seçilidir.

Varsayılan olarak, tüm diğer proje türleri için bu seçenek temizlenir.

 **Bu bir tam güven uygulamasıdır**

Bu seçeneği belirlerseniz, uygulama bir istemci bilgisayarda yüklendiğinde veya çalıştırıldığında tam güven izinleri ister. Mümkünse, uygulamanız dosya sistemi ve kayıt defteri gibi kaynaklara Kısıtlanmamış erişim izni vereceğinden, tam güven kullanmaktan kaçının.

Varsayılan olarak, WPF Web tarayıcısı uygulama projeleri için bu seçenek kısmi güven olarak ayarlanır.

Varsayılan olarak, tüm diğer proje türleri için bu seçenek tam güven olarak ayarlanır.

 **Bu bir kısmi güven uygulamasıdır**

Bu seçeneği belirlerseniz, uygulama bir istemci bilgisayarda yüklendiğinde veya çalıştırıldığında kısmi güven izinleri ister. *Kısmi güven* , yalnızca istenen kod erişimi güvenlik izinlerinin altında izin verilen eylemlerin çalışacağı anlamına gelir. Güvenlik izinlerini yapılandırma hakkında daha fazla bilgi için bkz. [ClickOnce uygulamaları Için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).

**ClickOnce güvenlik izinleri** alanındaki seçenekleri yapılandırarak kısmi güven güvenlik ayarlarını belirtebilirsiniz.

## <a name="clickonce-security-permissions"></a>ClickOnce güvenlik Izinleri

 **Uygulamanızın yükleneceği bölge**

Varsayılan bir kod erişimi güvenlik izinleri kümesi belirtir. Kısıtlı bir izin kümesi için **Internet** veya **Yerel Intranet** ' i seçin veya özel bir izin kümesi yapılandırmak için **(özel)** seçeneğini belirleyin. Uygulama bir bölgede verilenden daha fazla izin isterse, son kullanıcının ek izinleri vermesi için bir ClickOnce güven istemi görüntülenir. Güvenlik izinlerini yapılandırma hakkında daha fazla bilgi için bkz. [ClickOnce uygulamaları Için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).

Varsayılan olarak, WPF Web tarayıcısı uygulama projeleri için bu seçenek **Internet** olarak ayarlanır.

 **Izinleri Düzenle XML**

**(Özel)** izin kümesi için izinleri yapılandırmak üzere uygulama bildirimi şablonunu (App. manifest) açar.

 **Gelişmiş**

Kısıtlanmış izinlerle uygulamada hata ayıklamaya yönelik ayarları yapılandırmak için kullanılan [Gelişmiş güvenlik ayarları Iletişim kutusunu](../../ide/reference/advanced-security-settings-dialog-box.md)açar. Bu ayarlar hata ayıklama sırasında denetlenir ve izin özel durumları, uygulamanızın bir bölgede tanımlı olandan daha fazla izne ihtiyacı olabileceğini gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [ClickOnce uygulamaları için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md)
- [Nasıl yapılır: ClickOnce Güvenlik Ayarlarını Etkinleştirme](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Nasıl yapılır: ClickOnce Uygulaması için Bir Güvenlik Bölgesi Ayarlama](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Nasıl yapılır: ClickOnce Uygulaması için Özel İzinleri Ayarlama](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Güvenli ClickOnce uygulamaları](../../deployment/securing-clickonce-applications.md)
- [ClickOnce güvenliği ve dağıtımı](../../deployment/clickonce-security-and-deployment.md)
- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Gelişmiş Güvenlik Ayarları İletişim Kutusu](../../ide/reference/advanced-security-settings-dialog-box.md)
