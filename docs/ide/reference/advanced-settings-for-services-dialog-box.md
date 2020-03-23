---
title: Hizmetler İçin Gelişmiş Ayarlar İletişim Kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 967e99102f3b88e82a5466e7ce8d2cac2412d286
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585684"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Hizmetler İçin Gelişmiş Ayarlar İletişim Kutusu
İstemci uygulama hizmetleri, [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarından giriş, roller ve profil hizmetlerine basitleştirilmiş erişim sağlar. İstemci uygulama hizmetlerini yapılandırmak için **Project Designer'daki** **Hizmetler** sayfasını kullanabilirsiniz. **Hizmetler** sayfası hakkında daha fazla bilgi için [Hizmetler Sayfası, Proje Tasarımcısı sayfasına](../../ide/reference/services-page-project-designer.md)bakın.

İstemci uygulama hizmetleri için gelişmiş ayarları yapılandırmak için **Project Designer'daki** **Hizmetler** sayfasının **Gelişmiş Hizmetler** ayarları iletişim kutusunu kullanın. Bu ayarları kullanarak, daha az yaygın senaryoları etkinleştirmek için bazı varsayılan uygulama hizmeti davranışlarını geçersiz kılabilirsiniz. Daha fazla bilgi için [Bkz. İstemci Uygulama Hizmetleri.](/dotnet/framework/common-client-technologies/client-application-services)

**Hizmetler için Gelişmiş Ayarlar** iletişim kutusuna erişmek için **Çözüm Gezgini'nde**bir proje düğümü seçin ve ardından **Project** menüsünde **Özellikler'i** tıklatın. Proje **Tasarımcısı** göründüğünde, **Hizmetler** sekmesini tıklatın ve sonra **Gelişmiş** düğmesini tıklatın. İstemci uygulama hizmetlerini etkinleştirene kadar bu düğme devre dışı bırakılır.

## <a name="task-list"></a>Görev Listesi

- [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>UIElement Listesi

 **Çevrimdışı girişi etkinleştirmek için parola karmasını yerel olarak kaydet** Kullanıcının parolasının şifreli bir formunun, uygulama çevrimdışı modda yken kullanıcının oturum açmasını sağlamak için yerel olarak önbelleğe alınıp alınmayacağını belirtir. Bu seçenek varsayılan olarak seçilidir.

 **Sunucu çerezinin süresi dolduğunda kullanıcıların yeniden oturum açmasını zorunlu kılmasını zorunlu kılmaktadır** Uygulamanız rollere veya profil hizmetine eriştiğinde ve sunucu kimlik doğrulama çerezinin süresi dolduğunda, daha önce kimlik doğrulaması yapılan kullanıcıların otomatik olarak yeniden kimlik doğrulaması yapılıp yapılmayacağını belirtir. Uygulama hizmetlerine erişimi reddetmek ve çerezin süresi dolduktan sonra açık bir şekilde yeniden kimlik doğrulaması gerektirmek için bu seçeneği belirleyin. Bu, kullanımdan sonra uygulamayı çalışan kullanıcıların süresiz olarak kimlik doğrulaması kalmayacağından emin olmak için ortak konumlarda dağıtılan uygulamalar için yararlıdır. Bu seçenek varsayılan olarak temizlenir.

 **Rol hizmeti önbelleği zaman ası** İstemci rol sağlayıcısının roller hizmetine erişmek yerine önbelleğe alınmış rol değerlerini kullanacağı süreyi belirtir. Roller sık sık güncelleştirildiğinde bu zaman aralığını küçük bir değere veya roller seyrek güncelleştirildiğinde daha büyük bir değere ayarlayın. Varsayılan değer bir gündür.

Yöntem çağırdığınızda rol sağlayıcısı önbelleğe alınmış rol değerlerine veya rol hizmetine <xref:System.Web.Security.RolePrincipal.IsInRole%2A> erişir. Önbelleği programlı bir şekilde temizlemek ve bu yöntemi uzak <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> hizmete erişmeye zorlamak için yöntemi arayın.

 **Özel bağlantı dizesi kullanma** İstemci hizmet sağlayıcılarının yerel önbellek için özel bir veri deposu kullanıp kullanmayacağı belirtilir. Varsayılan olarak, hizmet sağlayıcıları önbellek için yerel dosya sistemini kullanır. Bu seçeneğin seçilmesi, metin kutusunu varsayılan bağlantı dizesiyle otomatik olarak dolduracaktır. Varsayılan bağlantı dizesini otomatik olarak bir SQL Server Compact Edition veritabanı oluşturmak ve kullanmak için tutabilir veya varolan bir SQL Server veritabanına bağlantı dizesi belirtebilirsiniz. Daha fazla bilgi için [bkz: İstemci Uygulama Hizmetlerini Yapılandırma.](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services) Bu seçenek varsayılan olarak temizlenir.

## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Uygulama Servisleri](/dotnet/framework/common-client-technologies/client-application-services)
- [Hizmetler Sayfası, Proje Tasarımcısı](../../ide/reference/services-page-project-designer.md)
- [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
