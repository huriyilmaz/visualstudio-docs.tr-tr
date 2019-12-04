---
title: 'Nasıl yapılır: Web sayfalarında JavaScript kodu profili oluşturma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 07c628b3c1f0be1c7ecc615dcae44f7736aa884e
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74775312"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Nasıl yapılır: Web sayfalarında JavaScript kodu profili oluşturma

Visual Studio Profil Oluşturma Araçları, izleme profili oluşturma yöntemi kullanılarak bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasında, rastgele bir Web sayfasında veya JavaScript uygulamasında yürütülen JavaScript kodu için performans verilerini toplayabilir. Internet Explorer 8 veya üstünü gerektirir.

> [!WARNING]
> UWP uygulamalarında JavaScript profili için bkz. [JavaScript belleği](../profiling/javascript-memory.md)

Bir performans oturumu oluşturmak için profil oluşturma sihirbazını kullanabilirsiniz. İzleme yöntemini belirtin ve ardından performans oturumunun Özellikler iletişim kutusunun Araçlar sayfasında JavaScript profil oluşturma seçeneğini belirtin.

JavaScript profil oluşturmayı belirttiğinizde, hem tarayıcıda çalıştırılan JavaScript kodu hem de sunucuda yürütülen [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kodu profili oluşturulur.

- [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması için hem tarayıcıda çalıştırılan JavaScript kodu hem de sunucuda yürütülen [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kodu profili oluşturulur.

- Rastgele bir Web sayfasında, tarayıcıda yürütülen JavaScript kodu profili oluşturulur.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Bir ASP.NET Web uygulaması projesindeki JavaScript 'ı profil oluşturma

1. Visual Studio 'da [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web projesi ' ni açın.

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
