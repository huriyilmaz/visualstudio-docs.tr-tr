---
title: Hizmetler Sayfası, Proje Tasarımcısı
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd374482d0432a54ed66442610aac1f60ca1828f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655481"
---
# <a name="services-page-project-designer"></a>Hizmetler Sayfası, Proje Tasarımcısı

İstemci uygulama hizmetleri, Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarından [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] oturum açma, rol ve profil hizmetlerine yönelik Basitleştirilmiş erişim sağlar. Projeniz için istemci uygulama hizmetlerini etkinleştirmek ve yapılandırmak üzere **Proje Tasarımcısı** ' nın **Hizmetler** sayfasını kullanabilirsiniz.

İstemci uygulama hizmetleri ile, kullanıcıların kimliğini doğrulamak, her kullanıcının atanan rolünü veya rollerini tespit etmek ve ağ genelinde paylaşabileceğiniz Kullanıcı başına uygulama ayarlarını depolamak için merkezi bir sunucu kullanabilirsiniz. Daha fazla bilgi için bkz. [istemci uygulama hizmetleri](/dotnet/framework/common-client-technologies/client-application-services).

**Hizmetler** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler** ' e tıklayın. **Proje Tasarımcısı** göründüğünde, **Hizmetler** sekmesine tıklayın.

## <a name="task-list"></a>Görev Listesi

[Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>UIElement Listesi

 **Yapılandırma**

Bu denetim bu sayfada düzenlenemez. Bu denetimin açıklaması için bkz. [derleme sayfası, proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) veya [derleme sayfası, proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platformunun**

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

Yalnızca Forms kimlik doğrulaması ile kullanılır. Uygulamanız `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> yöntemini çağırdığında ve boş dizeleri geçirirse ve parametreler için `null`, kimlik doğrulama hizmetinin bir oturum açma iletişim kutusunu görüntülemesi için kullanacağı <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> uygulamasını gösterir. Bu kutuyu boş bırakırsanız <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> metoduna geçerli bir Kullanıcı adı ve parola geçirmeniz gerekir. Kimlik bilgileri sağlayıcısını derleme nitelikli bir tür adı olarak belirtmeniz gerekir. Daha fazla bilgi için bkz. <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> ve [derleme adları](/dotnet/framework/app-domains/assembly-names). En basit biçimde, derleme nitelikli tür adı aşağıdaki örneğe benzer şekilde görünür: `MyNamespace.MyLoginClass, MyAssembly`

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
