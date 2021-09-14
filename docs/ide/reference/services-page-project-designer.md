---
title: Hizmetler Sayfası, Proje Tasarımcısı
description: Projeniz için istemci uygulama hizmetlerini etkinleştirmek ve yapılandırmak Project Tasarımcısı'nın Hizmetler sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: bc765f09966a9dbd5aed7ab31b4c2829e6c490dc
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627129"
---
# <a name="services-page-project-designer"></a>Hizmetler Sayfası, Proje Tasarımcısı

İstemci uygulama hizmetleri, Windows Forms ve [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] Windows Presentation Foundation (WPF) uygulamalarından oturum açma, roller ve profil hizmetleri için basitleştirilmiş erişim sağlar. Projeniz için **istemci** uygulama hizmetlerini **etkinleştirmek ve yapılandırmak Project** Tasarımcısı'nın Hizmetler sayfasını kullanabilirsiniz.

İstemci uygulama hizmetleriyle, kullanıcıların kimliğini doğrulamak, her kullanıcının atanmış rolünü veya rollerini belirlemek ve ağ üzerinde paylaşabilirsiniz kullanıcı başına uygulama ayarlarını depolamak için merkezi bir sunucu kullanabilirsiniz. Daha fazla bilgi için [bkz. İstemci Uygulama Hizmetleri.](/dotnet/framework/common-client-technologies/client-application-services)

Hizmetler sayfasına **erişmek** için, Çözüm Gezgini menüsünden bir **proje** düğümü seçin ve ardından **Project** tıklayın. Project **Tasarımcısı** göründüğünde Hizmetler **sekmesine** tıklayın.

## <a name="task-list"></a>Görev Listesi

[Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>UIElement Listesi

 **Yapılandırma**

Bu denetim bu sayfada düzenlenemez. Bu denetimin açıklaması için bkz. [Derleme Sayfası, Project Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) veya [Derleme Sayfası, Project Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platform**

Bu denetim bu sayfada düzenlenemez. Bu denetimin açıklaması için bkz. [Derleme Sayfası, Project Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) veya [Derleme Sayfası, Project Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **İstemci uygulama hizmetlerini etkinleştirme**

İstemci uygulama hizmetlerini etkinleştirmek için seçin. İstemci uygulama hizmetlerini kullanmak için Hizmetler **sayfasında** hizmet konumlarını belirtmeniz gerekir.

 **Kimlik Windows kullanma**

Kimlik doğrulama sağlayıcısının, Windows tabanlı kimlik doğrulaması, yani işletim sistemi tarafından sağlanan kimlik Windows belirtir.

 **Forms kimlik doğrulamasını kullanma**

Kimlik doğrulama sağlayıcısının form kimlik doğrulaması kullanmayacaklarını gösterir. Bu, uygulamanın oturum açma için bir kullanıcı arabirimi sağlaması gerektiğini gösterir. Daha fazla bilgi için, [bkz. How to: Implement User Login with Client Application Services](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).

 **Kimlik doğrulama hizmeti konumu**

Yalnızca form kimlik doğrulaması ile kullanılır. Kimlik doğrulama hizmetinin konumunu belirtir.

 **İsteğe bağlı: Kimlik bilgileri sağlayıcısı**

Yalnızca form kimlik doğrulaması ile kullanılır. Kimlik doğrulama hizmetinin, uygulamanız yöntemini çağıran ve boş dizeleri veya parametreleri geçtiğinde oturum açma iletişim kutusunu görüntülemek <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> için kullanabileceği `null` uygulamayı gösterir. Bu kutuyu boş bırakırsanız yöntemine geçerli bir kullanıcı adı ve parola geçmeniz <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> gerekir. Kimlik bilgileri sağlayıcısını derlemeye uygun bir tür adı olarak belirtmeniz gerekir. Daha fazla bilgi için <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> bkz. ve [Derleme Adları.](/dotnet/framework/app-domains/assembly-names) En basit biçimiyle, derlemeye uygun tür adı aşağıdaki örnektekine benzer: `MyNamespace.MyLoginClass, MyAssembly`

 **Rollerin hizmet konumu**

Rol hizmetinin konumunu belirtir.

 **Web ayarları hizmet konumu**

Profil (web ayarları) hizmetinin konumunu belirtir.

 **Gelişmiş**

Varsayılan davranışı [geçersiz Ayarlar için kullanabileceğiniz](../../ide/reference/advanced-settings-for-services-dialog-box.md)Hizmetler için Gelişmiş Hizmet İletişim Kutusu'Ayarlar açar. Örneğin, yerel dosya sistemini kullanmak yerine çevrimdışı depolama için bir veritabanı belirtmek üzere bu iletişim kutusunu kullanabilirsiniz. Daha fazla bilgi için [bkz. Hizmetler Ayarlar Gelişmiş Hizmetler İletişim Kutusu.](../../ide/reference/advanced-settings-for-services-dialog-box.md)

## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Uygulama Servisleri](/dotnet/framework/common-client-technologies/client-application-services)
- [Hizmetler İçin Gelişmiş Ayarlar İletişim Kutusu](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Derleme Sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md)
