---
title: Hizmetler sayfası, proje Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 11e1cd997c76974e7b4b8771c0579c175469eca6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665482"
---
# <a name="services-page-project-designer"></a>Hizmetler Sayfası, Proje Tasarımcısı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İstemci uygulama hizmetleri, Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarından [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] oturum açma, rol ve profil hizmetlerine yönelik Basitleştirilmiş erişim sağlar. Projeniz için istemci uygulama hizmetlerini etkinleştirmek ve yapılandırmak üzere **Proje Tasarımcısı** ' nın **Hizmetler** sayfasını kullanabilirsiniz.

 İstemci uygulama hizmetleri ile, kullanıcıların kimliğini doğrulamak, her kullanıcının atanan rolünü veya rollerini tespit etmek ve ağ genelinde paylaşabileceğiniz Kullanıcı başına uygulama ayarlarını depolamak için merkezi bir sunucu kullanabilirsiniz. Daha fazla bilgi için bkz. [istemci uygulama hizmetleri](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).

 **Hizmetler** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler** ' e tıklayın. **Proje Tasarımcısı** göründüğünde, **Hizmetler** sekmesine tıklayın.

> [!NOTE]
> İstemci uygulama hizmetleri .NET Framework tam sürümünü gerektirir ve .NET Framework Istemci profilinde desteklenmez. **İstemci uygulama hizmetlerini etkinleştir** onay kutusu devre dışıysa, **hedef framework 'ün** .NET Framework 3,5 veya sonraki bir sürümü olarak ayarlandığını doğrulayın. İçindeki C# **hedef Framework** ayarını görüntülemek için, proje tasarımcısını açın ve ardından **uygulama** sayfasına tıklayın. Visual Basic ' de **hedef Framework** ayarını görüntülemek Için, proje tasarımcısını açın, **Derle** sayfasına tıklayın ve **Gelişmiş derleme seçenekleri**' ne tıklayın.

## <a name="task-list"></a>Görev Listesi
 [Nasıl Yapılır: İstemci Uygulama Servislerini Yapılandırma](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)

## <a name="uielement-list"></a>UIElement Listesi
 **Yapılandırma** Bu denetim bu sayfada düzenlenemez. Bu denetimin açıklaması için bkz. [derleme sayfası, proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) veya [derleme sayfası, proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platform** Bu denetim bu sayfada düzenlenemez. Bu denetimin açıklaması için bkz. [derleme sayfası, proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) veya [derleme sayfası, proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **İstemci uygulama hizmetlerini etkinleştir** İstemci uygulama hizmetlerini etkinleştirmek için seçin. İstemci uygulama hizmetlerini kullanmak için **Hizmetler** sayfasında hizmet konumları belirtmeniz gerekir.

 **Windows kimlik doğrulamasını kullan** Kimlik doğrulama sağlayıcısının Windows tabanlı kimlik doğrulaması (yani, Windows işletim sistemi tarafından sağlanan kimlik) kullanacağını gösterir.

 **Forms kimlik doğrulaması kullan** Kimlik doğrulama sağlayıcısının form kimlik doğrulaması kullanacağını gösterir. Bu, uygulamanızın oturum açmak için bir kullanıcı arabirimi sağlaması gerektiği anlamına gelir. Daha fazla bilgi için bkz. [nasıl yapılır: istemci uygulama hizmetleri Ile Kullanıcı oturum açmayı uygulama](https://msdn.microsoft.com/library/5431a671-eb02-4e18-a651-24764fccec9a).

 **Kimlik doğrulama hizmeti konumu** Yalnızca Forms kimlik doğrulaması ile kullanılır. Kimlik doğrulama hizmetinin konumunu belirtir.

 **Isteğe bağlı: kimlik bilgileri sağlayıcısı** Yalnızca Forms kimlik doğrulaması ile kullanılır. Uygulamanız `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> yöntemini çağırdığında ve boş dizeleri geçirirse ve parametreler için `null`, kimlik doğrulama hizmetinin bir oturum açma iletişim kutusunu görüntülemesi için kullanacağı <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> uygulamasını gösterir. Bu kutuyu boş bırakırsanız <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> metoduna geçerli bir Kullanıcı adı ve parola geçirmeniz gerekir. Kimlik bilgileri sağlayıcısını derleme nitelikli bir tür adı olarak belirtmeniz gerekir. Daha fazla bilgi için bkz. <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> ve [derleme adları](https://msdn.microsoft.com/library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e). En basit biçimde, derleme nitelikli tür adı aşağıdaki örneğe benzer şekilde görünür: `MyNamespace.MyLoginClass, MyAssembly`

 **Rol hizmeti konumu** Rol hizmetinin konumunu belirtir.

 **Web ayarları hizmet konumu** Profil (Web ayarları) hizmetinin konumunu belirtir.

 **Gelişmiş** Varsayılan davranışı geçersiz kılmak için kullanabileceğiniz [Hizmetler Için Gelişmiş ayarlar Iletişim kutusunu](../../ide/reference/advanced-settings-for-services-dialog-box.md)açar. Örneğin, bu iletişim kutusunu yerel dosya sistemini kullanmak yerine çevrimdışı depolama için bir veritabanı belirtmek üzere kullanabilirsiniz. Daha fazla bilgi için bkz. [Hizmetler Için Gelişmiş ayarlar Iletişim kutusu](../../ide/reference/advanced-settings-for-services-dialog-box.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [İstemci uygulama hizmetleri](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e) [Hizmetler Için Gelişmiş ayarlar iletişim kutusu](../../ide/reference/advanced-settings-for-services-dialog-box.md) [nasıl yapılır: Istemci uygulama hizmetleri](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8) [Derleme sayfasını, proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) [Derleme sayfasını yapılandırma sayfası, proje TasarımcısıC#()](../../ide/reference/build-page-project-designer-csharp.md) [Proje tasarımcısına giriş](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)
