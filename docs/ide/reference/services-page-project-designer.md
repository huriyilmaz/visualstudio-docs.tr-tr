---
title: Hizmetler Sayfası, Proje Tasarımcısı
description: Projeniz için istemci uygulama hizmetlerini etkinleştirmek ve yapılandırmak üzere proje Tasarımcısı ' nın Hizmetler sayfasını nasıl kullanacağınızı öğrenin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c286dbd632e09a9a9c2c2b62ac2002f2e48f283
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560804"
---
# <a name="services-page-project-designer"></a>Hizmetler Sayfası, Proje Tasarımcısı

İstemci uygulama Hizmetleri [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] , Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarından oturum açma, rol ve profil hizmetlerine Basitleştirilmiş erişim sağlar. Projeniz için istemci uygulama hizmetlerini etkinleştirmek ve yapılandırmak üzere **Proje Tasarımcısı** ' nın **Hizmetler** sayfasını kullanabilirsiniz.

İstemci uygulama hizmetleri ile, kullanıcıların kimliğini doğrulamak, her kullanıcının atanan rolünü veya rollerini tespit etmek ve ağ genelinde paylaşabileceğiniz Kullanıcı başına uygulama ayarlarını depolamak için merkezi bir sunucu kullanabilirsiniz. Daha fazla bilgi için bkz. [istemci uygulama hizmetleri](/dotnet/framework/common-client-technologies/client-application-services).

**Hizmetler** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler** ' e tıklayın. **Proje Tasarımcısı** göründüğünde, **Hizmetler** sekmesine tıklayın.

## <a name="task-list"></a>Görev Listesi

[Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>UIElement Listesi

 **Yapılandırma**

Bu denetim bu sayfada düzenlenemez. Bu denetimin açıklaması için bkz. [derleme sayfası, proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) veya [derleme sayfası, proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platform**

Bu denetim bu sayfada düzenlenemez. Bu denetimin açıklaması için bkz. [derleme sayfası, proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) veya [derleme sayfası, proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **İstemci uygulama hizmetlerini etkinleştir**

İstemci uygulama hizmetlerini etkinleştirmek için seçin. İstemci uygulama hizmetlerini kullanmak için **Hizmetler** sayfasında hizmet konumları belirtmeniz gerekir.

 **Windows kimlik doğrulamasını kullan**

Kimlik doğrulama sağlayıcısının Windows tabanlı kimlik doğrulaması (yani, Windows işletim sistemi tarafından sağlanan kimlik) kullanacağını gösterir.

 **Forms kimlik doğrulaması kullan**

Kimlik doğrulama sağlayıcısının form kimlik doğrulaması kullanacağını gösterir. Bu, uygulamanızın oturum açmak için bir kullanıcı arabirimi sağlaması gerektiği anlamına gelir. Daha fazla bilgi için bkz. [nasıl yapılır: istemci uygulama hizmetleri Ile Kullanıcı oturum açmayı uygulama](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).

 **Kimlik doğrulama hizmeti konumu**

Yalnızca Forms kimlik doğrulaması ile kullanılır. Kimlik doğrulama hizmetinin konumunu belirtir.

 **İsteğe bağlı: kimlik bilgileri sağlayıcısı**

Yalnızca Forms kimlik doğrulaması ile kullanılır. <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>Uygulamanız `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> yöntemi çağırdığında ve boş dizeler ya da parametreler için bir oturum açma iletişim kutusu göstermek için kimlik doğrulama hizmetinin kullanacağı uygulamayı gösterir `null` . Bu kutuyu boş bırakırsanız, yönteme geçerli bir Kullanıcı adı ve parola geçirmeniz gerekir <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> . Kimlik bilgileri sağlayıcısını derleme nitelikli bir tür adı olarak belirtmeniz gerekir. Daha fazla bilgi için bkz <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> . ve [derleme adları](/dotnet/framework/app-domains/assembly-names). En basit biçimde, derleme nitelikli tür adı aşağıdaki örneğe benzer şekilde görünür: `MyNamespace.MyLoginClass, MyAssembly`

 **Rol hizmeti konumu**

Rol hizmetinin konumunu belirtir.

 **Web ayarları hizmet konumu**

Profil (Web ayarları) hizmetinin konumunu belirtir.

 **Gelişmiş**

Varsayılan davranışı geçersiz kılmak için kullanabileceğiniz [Hizmetler Için Gelişmiş ayarlar Iletişim kutusunu](../../ide/reference/advanced-settings-for-services-dialog-box.md)açar. Örneğin, bu iletişim kutusunu yerel dosya sistemini kullanmak yerine çevrimdışı depolama için bir veritabanı belirtmek üzere kullanabilirsiniz. Daha fazla bilgi için bkz. [Hizmetler Için Gelişmiş ayarlar Iletişim kutusu](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Uygulama Servisleri](/dotnet/framework/common-client-technologies/client-application-services)
- [Hizmetler İçin Gelişmiş Ayarlar İletişim Kutusu](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Derleme Sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md)
