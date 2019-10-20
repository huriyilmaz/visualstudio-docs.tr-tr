---
title: Hizmetler için Gelişmiş ayarlar Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a021475df1ade9bb6220612aad666d503c19cb8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651711"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Hizmetler İçin Gelişmiş Ayarlar İletişim Kutusu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İstemci uygulama hizmetleri, Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarından [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] oturum açma, rol ve profil hizmetlerine yönelik Basitleştirilmiş erişim sağlar. İstemci uygulama hizmetlerini yapılandırmak için **Proje tasarımcısında** **Hizmetler** sayfasını kullanabilirsiniz. **Hizmetler** sayfası hakkında daha fazla bilgi için bkz. [Hizmetler sayfası, proje Tasarımcısı](../../ide/reference/services-page-project-designer.md).

 İstemci uygulama hizmetlerinin gelişmiş ayarlarını yapılandırmak için **Proje Tasarımcısı** 'ndaki **Hizmetler** sayfasının **Gelişmiş ayarlar** iletişim kutusunu kullanın. Bu ayarları kullanarak, daha az yaygın senaryolar sağlamak için bazı varsayılan uygulama hizmeti davranışlarını geçersiz kılabilirsiniz. Daha fazla bilgi için bkz. [istemci uygulama hizmetleri](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).

 **Hizmetler Için Gelişmiş ayarlar** iletişim kutusuna erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler** ' e tıklayın. **Proje Tasarımcısı** göründüğünde, **Hizmetler** sekmesine tıklayın ve ardından **Gelişmiş** düğmesine tıklayın. Bu düğme, istemci uygulama hizmetlerini etkinleştirene kadar devre dışı bırakılır.

## <a name="task-list"></a>Görev Listesi
 [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)

 [Nasıl yapılır: Istemci Uygulama Hizmetleri ile çevrimdışı çalışma](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)

## <a name="uielement-list"></a>UIElement Listesi
 **Çevrimdışı oturum açmayı etkinleştirmek için parola karmasını yerel olarak kaydet** Kullanıcının, uygulama çevrimdışı moddayken oturum açmasını sağlamak için Kullanıcı parolasının şifreli bir biçiminin yerel olarak önbelleğe alınıp alınmayacağını belirtir. Daha fazla bilgi için bkz. [nasıl yapılır: istemci uygulama hizmetleri Ile çevrimdışı çalışma](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38). Bu seçenek varsayılan olarak seçilidir.

 **Sunucu tanımlama bilgilerinin süresi dolduğu zaman kullanıcıların yeniden oturum açmasını gerektir** Uygulamanız rollere veya profil hizmetine eriştiğinde ve sunucu kimlik doğrulama tanımlama bilgisinin süresi dolduğunda, önceden kimliği doğrulanmış kullanıcıların otomatik olarak yeniden kimlik doğrulaması yapılıp yapılmayacağını belirtir. Uygulama hizmetlerine erişimi reddetmek ve tanımlama bilgisinin süresi dolduktan sonra açık yeniden kimlik doğrulaması istemek için bu seçeneği belirleyin. Bu, ortak konumlarda dağıtılan uygulamalar için yararlıdır ve bu durumda, uygulamayı kullanımda bırakarak çalıştıran kullanıcıların kimliği doğrulanmamış olarak kalmaz. Bu seçenek varsayılan olarak temizlenir.

 **Rol hizmeti önbellek zaman aşımı** İstemci rolü sağlayıcısının roller hizmetine erişmek yerine önbelleğe alınmış rol değerlerini kullanacağı süreyi belirtir. Roller sık sık güncelleştirildiği zaman zaman aralığını küçük bir değere ayarlayın ve roller seyrek olarak güncelleniyorsa daha büyük bir değere ayarlayın. Varsayılan değer bir gündür.

 Rol sağlayıcısı, <xref:System.Web.Security.RolePrincipal.IsInRole%2A> yöntemini çağırdığınızda önbelleğe alınmış rol değerlerine veya rol hizmetine erişir. Önbelleği programlı bir şekilde temizlemek ve bu yöntemin uzak hizmete erişmesini zorlamak için <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> yöntemini çağırın.

 **Özel bağlantı dizesi kullan** İstemci hizmet sağlayıcılarının yerel önbellek için özel bir veri deposu kullanıp kullanmayacağını belirtir. Varsayılan olarak, hizmet sağlayıcıları önbellek için yerel dosya sistemini kullanır. Bu seçeneğin belirlenmesi, metin kutusunu otomatik olarak varsayılan bir bağlantı dizesiyle dolduracaktır. Otomatik olarak bir SQL Server Compact Edition veritabanı oluşturmak ve kullanmak için varsayılan bağlantı dizesini tutabilir veya var olan bir SQL Server veritabanına bir bağlantı dizesi belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Configure Client uygulama hizmetleri](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8). Bu seçenek varsayılan olarak temizlenir.

## <a name="see-also"></a>Ayrıca Bkz.
 [İstemci uygulama hizmetleri](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e) [Hizmetleri sayfası, proje Tasarımcısı](../../ide/reference/services-page-project-designer.md) [nasıl yapılır: istemciyi yapılandırma uygulama hizmetleri](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8) [nasıl yapılır: istemci ile çevrimdışı çalışma uygulama hizmetleri](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)
