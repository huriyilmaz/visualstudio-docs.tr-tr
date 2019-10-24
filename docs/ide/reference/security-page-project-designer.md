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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29723f5e253a2ff6d4f6c35e8ad8d3e09e2393f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748652"
---
# <a name="security-page-project-designer"></a>Güvenlik Sayfası, Proje Tasarımcısı

**Proje Tasarımcısı** 'nın **güvenlik** sayfası, ClickOnce dağıtımı kullanılarak dağıtılan uygulamalar için kod erişimi güvenlik ayarlarını yapılandırmak üzere kullanılır. Daha fazla bilgi için bkz. [ClickOnce uygulamaları Için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).

**Güvenlik** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümüne tıklayın ve ardından **Proje** menüsünde **Özellikler**' e tıklayın. **Proje Tasarımcısı** göründüğünde, **güvenlik** sekmesine tıklayın.

## <a name="security-settings"></a>Güvenlik ayarları

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

Varsayılan olarak, WPF Web tarayıcısı uygulama projeleri için bu seçenek **Internet**olarak ayarlanır.

 **Izinleri Düzenle XML**

**(Özel)** izin kümesi için izinleri yapılandırmak üzere uygulama bildirimi şablonunu (App. manifest) açar.

 **Gelişmiş**

Kısıtlanmış izinlerle uygulamada hata ayıklamaya yönelik ayarları yapılandırmak için kullanılan [Gelişmiş güvenlik ayarları Iletişim kutusunu](../../ide/reference/advanced-security-settings-dialog-box.md)açar. Bu ayarlar hata ayıklama sırasında denetlenir ve izin özel durumları, uygulamanızın bir bölgede tanımlı olandan daha fazla izne ihtiyacı olabileceğini gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [ClickOnce Uygulamaları İçin Kod Erişimi Güvenliği](../../deployment/code-access-security-for-clickonce-applications.md)
- [Nasıl yapılır: ClickOnce Güvenlik Ayarlarını Etkinleştirme](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Nasıl yapılır: ClickOnce Uygulaması için Bir Güvenlik Bölgesi Ayarlama](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Nasıl yapılır: ClickOnce Uygulaması için Özel İzinleri Ayarlama](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Nasıl yapılır: Sınırlı İzinler ile ClickOnce Uygulamasında Hata Ayıklama](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [ClickOnce Güvenliği ve Dağıtımı](../../deployment/clickonce-security-and-deployment.md)
- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Gelişmiş Güvenlik Ayarları İletişim Kutusu](../../ide/reference/advanced-security-settings-dialog-box.md)