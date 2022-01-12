---
title: .NET MVC projelerinde Azure AD ile çalışmaya başlama | Mavisi
description: Visual Studio bağlı hizmetleri kullanarak bir Azure AD 'ye bağlandıktan veya bağlantı kurulduktan sonra .net MVC projelerinde Azure Active Directory kullanmaya başlama
author: ghogen
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 12/14/2021
ms.author: ghogen
ms.custom: devx-track-csharp, aaddev, vs-azure
ms.openlocfilehash: dfe137accb35e2fe3a84ccb2b8acf9ef08a32538
ms.sourcegitcommit: d3578c384959f1b76dd06fb4b5d075fb052f8c69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2021
ms.locfileid: "135386750"
---
# <a name="getting-started-with-azure-active-directory-aspnet-mvc-projects"></a>Azure Active Directory kullanmaya başlama (ASP.NET MVC projeleri)

> [!div class="op_single_selector"]
> - [Başlarken](vs-active-directory-dotnet-getting-started.md)
> - [Ne oldu](vs-active-directory-dotnet-what-happened.md)

bu makalede, Visual Studio **Project > bağlı hizmetler** komutu aracılığıyla bir ASP.NET MVC projesine Active Directory ekledikten sonra ek rehberlik sunulmaktadır. Hizmeti projenize henüz eklemediyseniz, bunu dilediğiniz zaman yapabilirsiniz.

Bağlı hizmet eklenirken projenizde yapılan değişiklikler için bkz. [MVC projem ne oldu?](vs-active-directory-dotnet-what-happened.md)

## <a name="requiring-authentication-to-access-controllers"></a>Erişim denetleyicilerine kimlik doğrulaması gerektirme

Projenizdeki tüm denetleyiciler özniteliğiyle donatılmıştı `[Authorize]` . Bu öznitelik, bu denetleyicilere erişmeden önce kullanıcının kimliğinin doğrulanmasını gerektirir. Denetleyiciye anonim olarak erişilmesine izin vermek için bu özniteliği denetleyiciden kaldırın. İzinleri daha ayrıntılı bir düzeyde ayarlamak istiyorsanız, bu özniteliği denetleyici sınıfına uygulamak yerine yetkilendirme gerektiren her bir yönteme uygulayın.

## <a name="adding-signin--signout-controls"></a>SignIn/SignOut denetimleri ekleme

Görünüminizdeki SignIn/SignOut denetimlerini eklemek için, `_LoginPartial.cshtml` görünümlerinizin birine işlevselliği eklemek için kısmi görünümü kullanabilirsiniz. Standart görünüme eklenen işlevlere bir örnek aşağıda verilmiştir `_Layout.cshtml` . (Sınıf gezinti çubuğu ile div içindeki son öğeye göz önünde bulunan):

```html
<!DOCTYPE html>
 <html>
 <head>
     <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>@ViewBag.Title - My ASP.NET Application</title>
    @Styles.Render("~/Content/css")
    @Scripts.Render("~/bundles/modernizr")
</head>
<body>
    <div class="navbar navbar-inverse navbar-fixed-top">
        <div class="container">
            <div class="navbar-header">
                <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                </button>
                @Html.ActionLink("Application name", "Index", "Home", new { area = "" }, new { @class = "navbar-brand" })
            </div>
            <div class="navbar-collapse collapse">
                <ul class="nav navbar-nav">
                    <li>@Html.ActionLink("Home", "Index", "Home")</li>
                    <li>@Html.ActionLink("About", "About", "Home")</li>
                    <li>@Html.ActionLink("Contact", "Contact", "Home")</li>
                </ul>
                @Html.Partial("_LoginPartial")
            </div>
        </div>
    </div>
    <div class="container body-content">
        @RenderBody() 
        <hr />
        <footer>
            <p>&copy; @DateTime.Now.Year - My ASP.NET Application</p>
        </footer>
    </div>
    @Scripts.Render("~/bundles/jquery")
    @Scripts.Render("~/bundles/bootstrap")
    @RenderSection("scripts", required: false)
</body>
</html>
```

## <a name="next-steps"></a>Sonraki adımlar

- [Azure Active Directory için kimlik doğrulama senaryoları](/azure/active-directory/develop/authentication-vs-authorization)
- [Microsoft 'a ASP.NET web uygulamasına oturum açma ekleme](/azure/active-directory/develop/quickstart-v2-aspnet-webapp)