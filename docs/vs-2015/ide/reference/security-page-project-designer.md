---
title: Güvenlik sayfası, proje Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 768b0d43d8e6b52781e3f2dc2029e0b96b3a6548
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665531"
---
# <a name="security-page-project-designer"></a>Güvenlik Sayfası, Proje Tasarımcısı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Proje Tasarımcısı** 'nın **güvenlik** sayfası, dağıtım kullanılarak dağıtılan uygulamalar için kod erişimi güvenlik ayarlarını yapılandırmak üzere kullanılır [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] . Daha fazla bilgi için bkz. [ClickOnce uygulamaları Için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).

 **Güvenlik** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümüne tıklayın ve ardından **Proje** menüsünde **Özellikler**' e tıklayın. **Proje Tasarımcısı** göründüğünde, **güvenlik** sekmesine tıklayın.

## <a name="security-settings"></a>Güvenlik Ayarları
 **ClickOnce güvenlik ayarlarını etkinleştir** Tasarım zamanında güvenlik ayarlarının etkinleştirilip etkinleştirilmeyeceğini belirler. Bu seçenek silinirse, **güvenlik** sayfasındaki diğer tüm seçenekler kullanılamaz.

> [!NOTE]
> **Yayımla** sihirbazını kullanarak bir uygulamayı yayımladığınızda, bu seçenek otomatik olarak etkinleştirilir.

 Bu seçeneği belirlediğinizde, iki radyo düğmesinden birini seçme seçeneğiniz vardır: **Bu bir tam güven uygulamasıdır** veya **Bu bir kısmi güven uygulamasıdır**.

 Varsayılan olarak, WPF Web tarayıcısı uygulama projeleri için bu seçenek seçilidir.

 Varsayılan olarak, tüm diğer proje türleri için bu seçenek temizlenir.

 **Bu bir tam güven uygulamasıdır** Bu seçeneği belirlerseniz, uygulama bir istemci bilgisayarda yüklendiğinde veya çalıştırıldığında tam güven izinleri ister. Mümkünse, uygulamanız dosya sistemi ve kayıt defteri gibi kaynaklara Kısıtlanmamış erişim izni vereceğinden, tam güven kullanmaktan kaçının.

 Varsayılan olarak, WPF Web tarayıcısı uygulama projeleri için bu seçenek kısmi güven olarak ayarlanır.

 Varsayılan olarak, tüm diğer proje türleri için bu seçenek tam güven olarak ayarlanır.

 **Bu bir kısmi güven uygulamasıdır** Bu seçeneği belirlerseniz, uygulama bir istemci bilgisayarda yüklendiğinde veya çalıştırıldığında kısmi güven izinleri ister. *Kısmi güven* , yalnızca istenen kod erişimi güvenlik izinlerinin altında izin verilen eylemlerin çalışacağı anlamına gelir. Güvenlik izinlerini yapılandırma hakkında daha fazla bilgi için bkz. [ClickOnce uygulamaları Için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).

 **ClickOnce güvenlik izinleri** alanındaki seçenekleri yapılandırarak kısmi güven güvenlik ayarlarını belirtebilirsiniz.

## <a name="clickonce-security-permissions"></a>ClickOnce güvenlik Izinleri
 **Uygulamanızın yükleneceği bölge** Varsayılan bir kod erişimi güvenlik izinleri kümesi belirtir. Kısıtlı bir izin kümesi için **Internet** veya **Yerel Intranet** ' i seçin veya özel bir izin kümesi yapılandırmak için **(özel)** seçeneğini belirleyin. Uygulama bir bölgede verilenden daha fazla izin isterse, son kullanıcının ek izinleri vermesi için bir ClickOnce güven istemi görüntülenir. Güvenlik izinlerini yapılandırma hakkında daha fazla bilgi için bkz. [ClickOnce uygulamaları Için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).

 Varsayılan olarak, WPF Web tarayıcısı uygulama projeleri için bu seçenek **Internet**olarak ayarlanır.

 **Izinleri Düzenle XML** **(Özel)** izin kümesi için izinleri yapılandırmak üzere uygulama bildirimi şablonunu (App. manifest) açar.

 **Gelişmiş** Kısıtlanmış izinlerle uygulamada hata ayıklamaya yönelik ayarları yapılandırmak için kullanılan [Gelişmiş güvenlik ayarları Iletişim kutusunu](../../ide/reference/advanced-security-settings-dialog-box.md)açar. Bu ayarlar hata ayıklama sırasında denetlenir ve izin özel durumları, uygulamanızın bir bölgede tanımlı olandan daha fazla izne ihtiyacı olabileceğini gösterir.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Security.Permissions.WebBrowserPermission> <xref:System.Security.Permissions.MediaPermission>
 [ClickOnce uygulamaları Için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md) [nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../../deployment/how-to-enable-clickonce-security-settings.md) nasıl yapılır: ClickOnce uygulaması Için bir [güvenlik bölgesi ayarlama](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md) nasıl yapılır: bir [ClickOnce uygulaması Için](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md) [özel izinleri ayarlama](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md) [ClickOnce güvenliği ve dağıtım](../../deployment/clickonce-security-and-deployment.md) [projesi özellikleri başvuru](../../ide/reference/project-properties-reference.md) [Gelişmiş güvenlik ayarları iletişim kutusu](../../ide/reference/advanced-security-settings-dialog-box.md)
