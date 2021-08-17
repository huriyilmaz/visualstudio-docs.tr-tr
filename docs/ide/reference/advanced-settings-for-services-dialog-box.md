---
title: Hizmetler İçin Gelişmiş Ayarlar İletişim Kutusu
description: İstemci uygulama hizmetleri için gelişmiş ayarları yapılandırmak üzere Hizmetler için Gelişmiş Ayarlar özelliklerini kullanmayı öğrenin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a752855e639d6c7bce13ba1caa588ae0928828706ff7e4c56cc488437c8b0b68
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121232724"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Hizmetler İçin Gelişmiş Ayarlar İletişim Kutusu
İstemci uygulama hizmetleri, Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarından oturum açma, roller ve profil hizmetleri için [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] basitleştirilmiş erişim sağlar. İstemci uygulama hizmetlerini **yapılandırmak** için Proje **Tasarımcısı'nda** Hizmetler sayfasını kullanabilirsiniz. Hizmetler sayfası hakkında daha fazla **bilgi** için bkz. [Hizmetler Sayfası, Proje Tasarımcısı.](../../ide/reference/services-page-project-designer.md)

İstemci uygulama **hizmetleri için gelişmiş** ayarları yapılandırmak  üzere Proje **Tasarımcısı'nda** Hizmetler sayfasının Hizmetler için Gelişmiş Ayarlar iletişim kutusunu kullanın. Bu ayarları kullanarak, daha az yaygın senaryoları etkinleştirmek için bazı varsayılan uygulama hizmeti davranışlarını geçersiz kılabilirsiniz. Daha fazla bilgi için [bkz. İstemci Uygulama Hizmetleri.](/dotnet/framework/common-client-technologies/client-application-services)

Hizmetler için **Gelişmiş Ayarlar iletişim kutusuna erişmek** için, Çözüm Gezgini'de bir proje düğümü **seçin** ve ardından Proje **menüsünde** **Özellikler'e** tıklayın. Proje **Tasarımcısı görüntülendiğinde** Hizmetler **sekmesine** ve ardından Gelişmiş **düğmesine** tıklayın. Bu düğme, istemci uygulama hizmetlerini etkinleştirene kadar devre dışı bırakılır.

## <a name="task-list"></a>Görev Listesi

- [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>UIElement Listesi

 **Çevrimdışı oturum açma bilgilerini etkinleştirmek için parola karması yerel olarak kaydedin** Uygulama çevrimdışı moddayken kullanıcının oturum açması için kullanıcının parolasının şifrelenmiş bir formunun yerel olarak önbelleğe alınıp alınmayacaklarını belirtir. Bu seçenek varsayılan olarak seçilidir.

 **Sunucu tanımlama bilgisinin süresi dolduğunda kullanıcıların yeniden oturum açmalarını gerektirme** Uygulamanız rollere veya profil hizmetine erişdiğinde ve sunucu kimlik doğrulaması tanımlama bilgisinin süresi dolduğunda önceden kimliği doğrulanmış kullanıcıların otomatik olarak yeniden kimlik doğrulamasına sahip olup olmadığını belirtir. Uygulama hizmetlerine erişimi reddetmek ve tanımlama bilgisinin süresi dolsa da açık yeniden kimlik doğrulaması gerektirmek için bu seçeneği belirleyin. Bu, genel konumlarda dağıtılan uygulamaların, kullanımdan sonra uygulamayı çalıştıran kullanıcıların süresiz olarak kimliği doğrulanmış olarak kalmayacaklarını doğrulamaları için yararlıdır. Bu seçenek varsayılan olarak temizdir.

 **Rol hizmeti önbelleği zaman aşımı** İstemci rol sağlayıcısının rol hizmetine erişmek yerine önbelleğe alınmış rol değerlerini ne kadar süre kullanmayacaklarını belirtir. Roller sık güncelleştirildiğinde bu zaman aralığını küçük bir değere veya roller seyrek güncelleştirildiğinde daha büyük bir değere ayarlayın. Varsayılan değer bir gün olur.

Rol sağlayıcısı, yöntemini çağırarak önbelleğe alınan rol değerlerine veya roller hizmetine <xref:System.Web.Security.RolePrincipal.IsInRole%2A> erişer. Program aracılığıyla önbelleği temizlemek ve bu yöntemi uzak hizmete erişmeye zorlamak için yöntemini <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> çağırabilirsiniz.

 **Özel bağlantı dizesi kullanma** İstemci hizmet sağlayıcılarının yerel önbellek için özel bir veri deposu kullanıp kullanmayacaklarını belirtir. Varsayılan olarak, hizmet sağlayıcıları önbellek için yerel dosya sistemini kullanır. Bu seçeneğin işaretlenirken metin kutusu otomatik olarak varsayılan bağlantı dizesiyle doldurmaktır. Otomatik olarak bir SQL Server Compact Edition veritabanı oluşturmak ve kullanmak için varsayılan bağlantı dizesini tutabilirsiniz veya mevcut bir veritabanına bağlantı dizesi SQL Server belirtebilirsiniz. Daha fazla bilgi için, [bkz. How to: Configure Client Application Services](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services). Bu seçenek varsayılan olarak temizdir.

## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Uygulama Servisleri](/dotnet/framework/common-client-technologies/client-application-services)
- [Hizmetler Sayfası, Proje Tasarımcısı](../../ide/reference/services-page-project-designer.md)
- [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
