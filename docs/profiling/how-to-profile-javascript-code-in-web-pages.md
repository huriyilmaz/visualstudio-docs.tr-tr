---
title: Web Sayfaları Sayfalarında JavaScript Kodunun Profilini | Microsoft Docs
description: Ölçüm Visual Studio Profil Oluşturma Araçları yöntemini kullanarak JavaScript kodu için performans verilerini nasıl toplayabilirsiniz?
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f6ff70d45f47a8f7c34be58cfa33491f28e34bdb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060979"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Nasıl kullanılır: Web sayfalarında JavaScript kodunun profilini oluşturma

Visual Studio Profil Oluşturma Araçları bir web uygulamasında, rastgele bir web sayfasında veya JavaScript uygulamasında yürütülen JavaScript kodu için performans verilerini, ölçüm ölçüm profil [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] oluşturma yöntemini kullanarak toplayabilirsiniz. 8 veya Internet Explorer gerektirir.

> [!WARNING]
> UWP uygulamalarına JavaScript profili oluşturmak için bkz. [JavaScript Belleği](../profiling/javascript-memory.md)

Profil Oluşturma Sihirbazı'nı kullanarak bir performans oturumu oluşturabilirsiniz. Ölçüm yöntemini belirtin ve ardından performans oturumu için özellikler iletişim kutusunun Ölçümler sayfasında JavaScript profil oluşturma seçeneğini belirtin.

JavaScript profili oluşturmayı belirttiğinizde, hem tarayıcıda yürütülen JavaScript kodu hem de sunucuda [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] yürütülen kod profili açılır.

- Bir web uygulaması için hem tarayıcıda yürütülen JavaScript kodu hem de sunucuda [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] yürütülen kodun profili görüntülenir.

- Rastgele bir web sayfası için, tarayıcıda yürütülen JavaScript kodunun profili profili açılır.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Bir web uygulaması projesinde JavaScript ASP.NET profili oluşturmak için

1. Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projesini Visual Studio.

2. Analiz menüsünde **Performans** Sihirbazı'nı **Başlat'a tıklayın.**

3. Performans Sihirbazı'nın ilk sayfasında, Ölçümleme profil oluşturma yöntemini **belirtin** ve ardından Sonraki 'ye **tıklayın.**

4. Sihirbazın ikinci sayfasında, hedef listesinde geçerli projenin seçili olduğundan emin olun ve ardından Sonraki'ye **tıklayın.**

5. Sihirbazın üçüncü sayfasında, Profil **JavaScript** onay kutusunu seçin ve ardından Sonraki 'ye **tıklayın.**

6. Sihirbazın dördüncü sayfasında, web uygulamasını **tarayıcıda** başlatmak için Son'a tıklayın.

7. Profil oluşturmak istediğiniz işlevselliği kullanın.

8. Profil oluşturma oturumunu sona ererken tarayıcıyı kapatın.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Tek tek web sayfalarında veya bir JavaScript uygulamalarında JavaScript profili oluşturmak için

1. Visual Studio'yu açın.

2. Analiz menüsünde **Performans** Sihirbazı'nı **Başlat'a tıklayın.**

3. Performans Sihirbazı'nın ilk sayfasında, Ölçümleme profil oluşturma yöntemini **belirtin** ve ardından Sonraki 'ye **tıklayın.**

4. Sihirbazın ikinci sayfasında An ASP.NET veya JavaScript uygulaması'nı ve ardından Sonraki'ye **tıklayın.**

5. Sihirbazın üçüncü sayfasında:

    1. Uygulamanızı çalıştıracak URL veya **yol kutusuna sayfanın URL'sini** yazın.

    2. Profil **JavaScript onay kutusunu** seçin ve ardından Sonraki'ye **tıklayın.**

6. Sihirbazın dördüncü sayfasında, tarayıcıda web **sayfasını** başlatmak için Son'a tıklayın.

7. Profil oluşturmak istediğiniz işlevselliği kullanın.

8. Profil oluşturma oturumunu sona ererken tarayıcıyı kapatın.
