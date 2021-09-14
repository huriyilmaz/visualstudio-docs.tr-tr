---
title: Son kullanıcıların yüklemenin bulunduğu konumu belirtme
description: Yayımlanmış bir uygulamanın yükleme için barındır bulunduğu Yükleme URL'si ClickOnce özelliğini ayarlamayı öğrenin.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: dae59aa3fb9bde3d2ed43cf7d8c41da4079cf408
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725395"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Nasıl kurulur: Son kullanıcıların yükleyecekleri konumu belirtme

Bir uygulamayı yayımlarken, kullanıcıların uygulamayı indirmeye ve yüklemeye gideceği konum, uygulamayı ilk kez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yayımlay konumunuz olmayabilir. Örneğin, bazı kuruluşlarda bir geliştirici bir uygulamayı hazırlama sunucusuna yayımlar ve ardından bir yönetici uygulamayı bir Web sunucusuna taşımaya devam eder.

Bu durumda, kullanıcıların uygulamayı `Installation URL` indirmek için gideceği Web sunucusunu belirtmek için özelliğini kullanabilirsiniz. Bu, uygulama bildiriminin güncelleştirmeleri nerede baktırılabızı bildiği için gereklidir.

özelliği, `Installation URL` Project  **Designer'ın Yayımla sayfasından ayarlanır.**

> [!NOTE]
> özelliği `Installation URL` **PublishWizard kullanılarak da ayarlandırabilirsiniz.** Daha fazla bilgi için [bkz. Yayımlama Sihirbazı'nı ClickOnce uygulama yayımlama.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

### <a name="to-specify-an-installation-url"></a>Yükleme URL'si belirtmek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **Project'a** **tıklayın.**

2. Yayımla **sekmesine** tıklayın.

3. Yükleme URL'si alanına, biçimini kullanan tam URL'yi veya biçimini kullanan `https://www.contoso.com/ApplicationName` bir UNC yolunu kullanarak yükleme konumunu `\Server\ApplicationName` girin.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Dosyaların Visual Studio olduğunu belirtme](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Uygulama ClickOnce yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl ClickOnce: ClickOnce Sihirbazı'nı kullanarak bir uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)