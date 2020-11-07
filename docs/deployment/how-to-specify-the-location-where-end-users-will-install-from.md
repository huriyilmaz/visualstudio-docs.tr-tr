---
title: Son kullanıcıların yükleneceği konumu belirtin
description: Yayımlanan bir ClickOnce uygulamasının yüklenmek üzere barındırıldığı, yükleme URL özelliğini ayarlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3518a2eef331414e5c73c0cebb36681ad2b72d61
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349626"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Nasıl yapılır: son kullanıcıların yükleneceği konumu belirtme

Bir uygulamayı yayımlarken [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , kullanıcıların uygulamayı indirmek ve yüklemek için gideceği konum, uygulamayı ilk olarak yayımladığınız konum değildir. Örneğin, bazı kuruluşlarda bir geliştirici bir uygulamayı hazırlama sunucusuna yayımlayabilir ve ardından Yönetici uygulamayı bir Web sunucusuna taşır.

Bu durumda, `Installation URL` kullanıcıların uygulamayı indirmek için Gideceleceği Web sunucusunu belirtmek için özelliğini kullanabilirsiniz. Bu, uygulama bildiriminin güncelleştirmelerin nerede bakacağını bilmesini sağlamak için gereklidir.

`Installation URL`Özelliği, **Proje Tasarımcısı** ' nın **Yayımla** sayfasında ayarlanabilir.

> [!NOTE]
> `Installation URL`Özelliği **publishwizard** kullanılarak da ayarlanabilir. Daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>Yükleme URL 'SI belirtmek için

1. **Çözüm Gezgini** ' de bir proje seçiliyken, **Proje** menüsünde **Özellikler** ' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. Yükleme URL 'SI alanında, biçimi kullanarak tam URL 'YI veya biçimi kullanarak bir UNC yolunu kullanarak yükleme konumunu girin `https://www.contoso.com/ApplicationName` `\Server\ApplicationName` .

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Visual Studio 'Nun dosyaları nereye kopyaladığını belirtme](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)