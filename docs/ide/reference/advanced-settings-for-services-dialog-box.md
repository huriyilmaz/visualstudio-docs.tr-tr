---
title: Hizmetler İçin Gelişmiş Ayarlar İletişim Kutusu
description: İstemci uygulama hizmetleri için Gelişmiş ayarları yapılandırmak üzere Hizmetler özelliklerinin Gelişmiş ayarları 'nı nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b705042f7713b2571e391801c4a1d29734a031bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969808"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Hizmetler İçin Gelişmiş Ayarlar İletişim Kutusu
İstemci uygulama Hizmetleri [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] , Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarından oturum açma, rol ve profil hizmetlerine Basitleştirilmiş erişim sağlar. İstemci uygulama hizmetlerini yapılandırmak için **Proje tasarımcısında** **Hizmetler** sayfasını kullanabilirsiniz. **Hizmetler** sayfası hakkında daha fazla bilgi için bkz. [Hizmetler sayfası, proje Tasarımcısı](../../ide/reference/services-page-project-designer.md).

İstemci uygulama hizmetlerinin gelişmiş ayarlarını yapılandırmak için **Proje Tasarımcısı** 'ndaki **Hizmetler** sayfasının **Gelişmiş ayarlar** iletişim kutusunu kullanın. Bu ayarları kullanarak, daha az yaygın senaryolar sağlamak için bazı varsayılan uygulama hizmeti davranışlarını geçersiz kılabilirsiniz. Daha fazla bilgi için bkz. [istemci uygulama hizmetleri](/dotnet/framework/common-client-technologies/client-application-services).

**Hizmetler Için Gelişmiş ayarlar** iletişim kutusuna erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler** ' e tıklayın. **Proje Tasarımcısı** göründüğünde, **Hizmetler** sekmesine tıklayın ve ardından **Gelişmiş** düğmesine tıklayın. Bu düğme, istemci uygulama hizmetlerini etkinleştirene kadar devre dışı bırakılır.

## <a name="task-list"></a>Görev Listesi

- [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>UIElement Listesi

 **Çevrimdışı oturum açmayı etkinleştirmek için parola karmasını yerel olarak kaydet** Kullanıcının, uygulama çevrimdışı moddayken oturum açmasını sağlamak için Kullanıcı parolasının şifreli bir biçiminin yerel olarak önbelleğe alınıp alınmayacağını belirtir. Bu seçenek varsayılan olarak seçilidir.

 **Sunucu tanımlama bilgilerinin süresi dolduğu zaman kullanıcıların yeniden oturum açmasını gerektir** Uygulamanız rollere veya profil hizmetine eriştiğinde ve sunucu kimlik doğrulama tanımlama bilgisinin süresi dolduğunda, önceden kimliği doğrulanmış kullanıcıların otomatik olarak yeniden kimlik doğrulaması yapılıp yapılmayacağını belirtir. Uygulama hizmetlerine erişimi reddetmek ve tanımlama bilgisinin süresi dolduktan sonra açık yeniden kimlik doğrulaması istemek için bu seçeneği belirleyin. Bu, ortak konumlarda dağıtılan uygulamalar için yararlıdır ve bu durumda, uygulamayı kullanımda bırakarak çalıştıran kullanıcıların kimliği doğrulanmamış olarak kalmaz. Bu seçenek varsayılan olarak temizlenir.

 **Rol hizmeti önbellek zaman aşımı** İstemci rolü sağlayıcısının roller hizmetine erişmek yerine önbelleğe alınmış rol değerlerini kullanacağı süreyi belirtir. Roller sık sık güncelleştirildiği zaman zaman aralığını küçük bir değere ayarlayın ve roller seyrek olarak güncelleniyorsa daha büyük bir değere ayarlayın. Varsayılan değer bir gündür.

Rol sağlayıcısı, yöntemi çağırdığınızda önbelleğe alınmış rol değerlerine veya rol hizmetine erişir <xref:System.Web.Security.RolePrincipal.IsInRole%2A> . Önbelleği programlı bir şekilde temizlemek ve bu yöntemin uzak hizmete erişmesini zorlamak için <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> yöntemini çağırın.

 **Özel bağlantı dizesi kullan** İstemci hizmet sağlayıcılarının yerel önbellek için özel bir veri deposu kullanıp kullanmayacağını belirtir. Varsayılan olarak, hizmet sağlayıcıları önbellek için yerel dosya sistemini kullanır. Bu seçeneğin belirlenmesi, metin kutusunu otomatik olarak varsayılan bir bağlantı dizesiyle dolduracaktır. Otomatik olarak bir SQL Server Compact Edition veritabanı oluşturmak ve kullanmak için varsayılan bağlantı dizesini tutabilir veya var olan bir SQL Server veritabanına bir bağlantı dizesi belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Configure Client uygulama hizmetleri](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services). Bu seçenek varsayılan olarak temizlenir.

## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Uygulama Servisleri](/dotnet/framework/common-client-technologies/client-application-services)
- [Hizmetler Sayfası, Proje Tasarımcısı](../../ide/reference/services-page-project-designer.md)
- [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
