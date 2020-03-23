---
title: Hizmetler Sayfası, Proje Tasarımcısı
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
ms.openlocfilehash: d30d8e8ddcdc8c1fa4fe1935da1f1dedd1b18f4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593570"
---
# <a name="services-page-project-designer"></a>Hizmetler Sayfası, Proje Tasarımcısı

İstemci uygulama hizmetleri, [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarından giriş, roller ve profil hizmetlerine basitleştirilmiş erişim sağlar. Projeniz için istemci uygulama hizmetlerini etkinleştirmek ve yapılandırmak için **Proje Tasarımcısı'nın** **Hizmetler** sayfasını kullanabilirsiniz.

İstemci uygulama hizmetleriyle, kullanıcıların kimliğini doğrulamak, her kullanıcının atanan rolünü veya rolünü belirlemek ve ağ da paylaşabileceğiniz kullanıcı başına uygulama ayarlarını depolamak için merkezi bir sunucu kullanabilirsiniz. Daha fazla bilgi için [Bkz. İstemci Uygulama Hizmetleri.](/dotnet/framework/common-client-technologies/client-application-services)

**Hizmetler** sayfasına erişmek için **Çözüm Gezgini'nde**bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler'i** tıklatın. Proje **Tasarımcısı** göründüğünde, **Hizmetler** sekmesini tıklatın.

## <a name="task-list"></a>Görev Listesi

[Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>UIElement Listesi

 **Yapılandırma**

Bu denetim bu sayfada denetlenemez. Bu denetimin açıklaması için bkz: [Sayfayı Derle, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) veya [Build Page, Project Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platform**

Bu denetim bu sayfada denetlenemez. Bu denetimin açıklaması için bkz: [Sayfayı Derle, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) veya [Build Page, Project Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **İstemci uygulama hizmetlerini etkinleştirme**

İstemci uygulama hizmetlerini etkinleştirmek için seçin. İstemci uygulama hizmetlerini kullanmak için **Hizmetler** sayfasında hizmet konumlarını belirtmeniz gerekir.

 **Windows kimlik doğrulamayı kullanma**

Kimlik doğrulama sağlayıcısının Windows tabanlı kimlik doğrulaması, yani Windows işletim sistemi tarafından sağlanan kimliği kullanacağını gösterir.

 **Formlar kimlik doğrulamasını kullanma**

Kimlik doğrulama sağlayıcısının form kimlik doğrulaması kullanacağını gösterir. Bu, uygulamanızın oturum açmak için bir kullanıcı arabirimi sağlaması gerektiği anlamına gelir. Daha fazla bilgi için [bkz: Müşteri Uygulama Hizmetleri ile Kullanıcı Girişi Uygulayın.](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services)

 **Kimlik doğrulama hizmeti konumu**

Yalnızca form kimlik doğrulamasıyla kullanılır. Kimlik doğrulama hizmetinin konumunu belirtir.

 **İsteğe bağlı: Kimlik bilgileri sağlayıcısı**

Yalnızca form kimlik doğrulamasıyla kullanılır. Uygulamanız <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> yöntemi aradığında ve boş dizeleri geçtiğinde veya `null` parametreler için bir giriş iletişim kutusunu görüntülemek için kimlik doğrulama hizmetinin kullanacağı uygulamayı gösterir. Bu kutuyu boş bırakırsanız, <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> yönteme geçerli bir kullanıcı adı ve parola geçirmeniz gerekir. Kimlik bilgileri sağlayıcısını montaja uygun bir tür adı olarak belirtmeniz gerekir. Daha fazla bilgi <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> için bkz ve [Derleme Adları.](/dotnet/framework/app-domains/assembly-names) En basit haliyle, derleme nitelikli bir tür adı aşağıdaki örneğe benzer:`MyNamespace.MyLoginClass, MyAssembly`

 **Roller hizmet konumu**

Roller hizmetinin konumunu belirtir.

 **Web ayarları hizmet konumu**

Profil (web ayarları) hizmetinin konumunu belirtir.

 **Gelişmiş**

Varsayılan davranışı geçersiz kılmak için kullanabileceğiniz [Hizmetler Için Gelişmiş Ayarlar İletişim Kutusu'nu](../../ide/reference/advanced-settings-for-services-dialog-box.md)açar. Örneğin, yerel dosya sistemini kullanmak yerine çevrimdışı depolama için bir veritabanı belirtmek için bu iletişim kutusunu kullanabilirsiniz. Daha fazla bilgi [için Hizmetler Için Gelişmiş Ayarlar İletişim Kutusu'na](../../ide/reference/advanced-settings-for-services-dialog-box.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Uygulama Servisleri](/dotnet/framework/common-client-technologies/client-application-services)
- [Hizmetler İçin Gelişmiş Ayarlar İletişim Kutusu](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Derleme Sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md)
