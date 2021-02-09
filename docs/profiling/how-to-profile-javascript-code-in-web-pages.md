---
title: Web sayfalarında JavaScript kodu profili | Microsoft Docs
description: Visual Studio Profil Oluşturma Araçları 'nin, izleme profili oluşturma yöntemini kullanarak JavaScript kodu için performans verilerini nasıl toplayabileceği hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 288fa04fa44528ad34c68cf3d770bb6d5673b976
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907122"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Nasıl yapılır: Web sayfalarında JavaScript kodu profili oluşturma

Visual Studio Profil Oluşturma Araçları [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , izleme profili oluşturma yöntemi kullanılarak bir Web uygulamasında, rastgele bir Web sayfasında veya JavaScript uygulamasında yürütülen JavaScript kodu için performans verilerini toplayabilir. Internet Explorer 8 veya üstünü gerektirir.

> [!WARNING]
> UWP uygulamalarında JavaScript profili için bkz. [JavaScript belleği](../profiling/javascript-memory.md)

Bir performans oturumu oluşturmak için profil oluşturma sihirbazını kullanabilirsiniz. İzleme yöntemini belirtin ve ardından performans oturumunun Özellikler iletişim kutusunun Araçlar sayfasında JavaScript profil oluşturma seçeneğini belirtin.

JavaScript profil oluşturmayı belirttiğinizde, hem tarayıcıda çalıştırılan JavaScript kodu hem de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sunucuda yürütülen kod profili oluşturulur.

- Bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması için, hem tarayıcıda çalıştırılan JavaScript kodu hem de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sunucuda yürütülen kod için profil oluşturulur.

- Rastgele bir Web sayfasında, tarayıcıda yürütülen JavaScript kodu profili oluşturulur.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Bir ASP.NET Web uygulaması projesindeki JavaScript 'ı profil oluşturma

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Web projesini Visual Studio 'da açın.

2. **Çözümle** menüsünde, **Performans Sihirbazını Başlat**' ı tıklatın.

3. Performans sihirbazının ilk sayfasında, **izleme** profil oluşturma yöntemini belirtin ve ardından **İleri**' ye tıklayın.

4. Sihirbazın ikinci sayfasında, geçerli projenin hedef listesinde seçili olduğundan emin olun ve ardından Ileri ' ye tıklayın **.**

5. Sihirbazın üçüncü sayfasında **profil JavaScript** onay kutusunu seçin ve ardından **İleri**' ye tıklayın.

6. Sihirbazın dördüncü sayfasında, Web uygulamasını tarayıcıda başlatmak için **son** ' a tıklayın.

7. Profil eklemek istediğiniz işlevselliği yapın.

8. Profil oluşturma oturumunu sonlandırmak için tarayıcıyı kapatın.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Ayrı Web sayfalarında veya JavaScript uygulamalarında JavaScript profili oluşturma

1. Visual Studio'yu açın.

2. **Çözümle** menüsünde, **Performans Sihirbazını Başlat**' ı tıklatın.

3. Performans sihirbazının ilk sayfasında, **izleme** profil oluşturma yöntemini belirtin ve ardından **İleri**' ye tıklayın.

4. Sihirbazın ikinci sayfasında, bir ASP.NET veya JavaScript uygulamasına tıklayın ve sonra Ileri ' ye tıklayın **.**

5. Sihirbazın üçüncü sayfasında:

    1. Uygulamanızın URL 'sini **veya yolunu HANGI URL veya yolda çalıştıracağınızı** yazın.

    2. **Profil JavaScript** onay kutusunu seçin ve ardından **İleri**' ye tıklayın.

6. Sihirbazın dördüncü sayfasında, Web sayfasını tarayıcıda başlatmak için **son** ' a tıklayın.

7. Profil eklemek istediğiniz işlevselliği yapın.

8. Profil oluşturma oturumunu sonlandırmak için tarayıcıyı kapatın.
