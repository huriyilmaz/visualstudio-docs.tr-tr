---
title: 'Nasıl kullanılır: Web Sayfalarında Profil JavaScript Kodu | Microsoft Dokümanlar'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775312"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Nasıl kullanılır: Web sayfalarında Profil JavaScript kodu

Visual Studio Profil Oluşturma Araçları, enstrümantasyon profiloluşturma [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] yöntemini kullanarak bir web uygulamasında, rasgele bir web sayfasında veya JavaScript uygulamasında yürüten JavaScript kodu için performans verileri toplayabilir. Internet Explorer 8 veya sonraki gerektirir.

> [!WARNING]
> UWP uygulamalarında JavaScript profili için [Bkz.](../profiling/javascript-memory.md)

Performans oturumu oluşturmak için Profil Oluşturma Sihirbazı'nı kullanabilirsiniz. Enstrümantasyon yöntemini belirtin ve ardından performans oturumu için özellikler iletişim kutusunun Enstrümantasyon sayfasında JavaScript profil oluşturma seçeneğini belirtin.

JavaScript profil oluşturmayı belirttiğiniz zaman, hem tarayıcıda yürüten [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] JavaScript kodu hem de sunucuda çalıştırılabilen kod profillenir.

- Bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması için, hem tarayıcıda çalıştıran JavaScript kodu hem de sunucuda çalıştırılabilen [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kod profillenir.

- Rasgele bir web sayfası için, tarayıcıda çalıştıran JavaScript kodu profillenir.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>ASP.NET bir web uygulama projesinde JavaScript profilini çıkarmak için

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web projesini Visual Studio'da açın.

2. **Analiz** menüsünde, **Performans Sihirbazı Başlat'ı**tıklatın.

3. Performans Sihirbazı'nın ilk sayfasında **Enstrümantasyon** profil oluşturma yöntemini belirtin ve sonra **İleri'yi**tıklatın.

4. Sihirbazın ikinci sayfasında, geçerli projenin hedefler listesinde seçildiğinden emin olun ve sonra **İleri'yi tıklatın.**

5. Sihirbazın üçüncü sayfasında Profile **JavaScript** onay kutusunu seçin ve sonra **İleri'yi**tıklatın.

6. Sihirbazın dördüncü sayfasında, tarayıcıdaki web uygulamasını başlatmak için **Bitir'i** tıklatın.

7. Profilini çıkarmak istediğiniz işlevselliği kullanın.

8. Profil oluşturma oturumunu sona erdirmek için tarayıcıyı kapatın.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>JavaScript'i tek tek web sayfalarında veya JavaScript uygulamalarında profillemek için

1. Visual Studio'yu açın.

2. **Analiz** menüsünde, **Performans Sihirbazı Başlat'ı**tıklatın.

3. Performans Sihirbazı'nın ilk sayfasında **Enstrümantasyon** profil oluşturma yöntemini belirtin ve sonra **İleri'yi**tıklatın.

4. Sihirbazın ikinci sayfasında, ASP.NET veya JavaScript uygulamasını tıklatın ve sonra **İleri'yi tıklatın.**

5. Sihirbazın üçüncü sayfasında:

    1. Uygulama kutunuzda **hangi URL'nin veya yolun çalışacağına** sayfanın URL'sini yazın.

    2. Profil **JavaScript** onay kutusunu seçin ve sonra **İleri'yi**tıklatın.

6. Sihirbazın dördüncü sayfasında, tarayıcıdaki web sayfasını başlatmak için **Bitir'i** tıklatın.

7. Profilini çıkarmak istediğiniz işlevselliği kullanın.

8. Profil oluşturma oturumunu sona erdirmek için tarayıcıyı kapatın.
