---
title: Başlarken WebApi projelerinde Azure AD Visual Studio ile çalışma
description: Bağlı hizmetlere bağlandıktan Azure Active Directory Azure AD'ye bağlandıktan veya bu hizmetleri kullanarak Bir Azure AD oluşturduk Visual Studio kullanmaya başlama
author: ghogen
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 12/14/2021
ms.author: ghogen
ms.custom: devx-track-csharp, aaddev, vs-azure
ms.openlocfilehash: 46540feb8409a78c766f83dd08a5b52ebd8b3b26
ms.sourcegitcommit: d3578c384959f1b76dd06fb4b5d075fb052f8c69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2021
ms.locfileid: "135386751"
---
# <a name="get-started-with-azure-active-directory-webapi-projects"></a>Başlarken ile Azure Active Directory (WebApi projeleri)

> [!div class="op_single_selector"]
> - [Başlarken](vs-active-directory-webapi-getting-started.md)
> - [Ne oldu](vs-active-directory-webapi-what-happened.md)

Bu makale, active directory'i ASP.NET Bağlı Hizmetler komutu aracılığıyla ASP.NET Web **Project > API** projesine ekledikten sonra ek Visual Studio. Hizmeti projenize henüz eklenmediyse, bunu herhangi bir zamanda da yapabiliriz.

Bağlı [hizmeti eklerken projenize yapılan](vs-active-directory-webapi-what-happened.md) değişiklikler için bkz. WebAPI projeme ne oldu?

## <a name="requiring-authentication-to-access-controllers"></a>Denetleyicilere erişmek için kimlik doğrulaması gerektirme

Projenizin tüm denetleyicileri özniteliğiyle `[Authorize]` donatıldı. Bu öznitelik, bu denetleyiciler tarafından tanımlanan API'lere erişmeden önce kullanıcının kimliği doğrulanmalıdır. Denetleyiciye anonim olarak erişime izin vermek için bu özniteliği denetleyiciden kaldırın. İzinleri daha ayrıntılı bir düzeyde ayarlamak için, denetleyici sınıfına uygulamak yerine yetkilendirme gerektiren her yönteme özniteliğini uygulayabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [Azure Active Directory için kimlik doğrulama senaryoları](/azure/active-directory/develop/authentication-vs-authorization)
- [Microsoft ile bir web uygulamasına ASP.NET ekleme](/azure/active-directory/develop/quickstart-v2-aspnet-webapp)