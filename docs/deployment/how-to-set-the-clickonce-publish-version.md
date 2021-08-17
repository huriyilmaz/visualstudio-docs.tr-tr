---
title: ClickOnce Yayımlama Sürümü | Microsoft Docs
description: Uygulamanın bir güncelleştirme ClickOnce sürüm yayımlama özelliğini ayarlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 39c126a1e2758bbbbc24c0f6ef5fa9b6310669eb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089907"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Nasıl ClickOnce: ClickOnce ayarlama
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` özelliği, yayımlamakta olan uygulamanın bir güncelleştirme olarak kabul edilir olup olmadığını belirler. Sürüm her artırılırsa, uygulama bir güncelleştirme olarak yayımlanır.

 özelliği, `Publish Version` Project  **Designer'ın Yayımla sayfasından ayarlanır.**

> [!NOTE]
> Uygulama her yayım olduğunda özelliği otomatik olarak artıran bir proje `Publish Version` seçeneği vardır; bu seçenek varsayılan olarak etkindir. Daha fazla bilgi için [bkz. Nasıl yapılır: Sürümü Yayımlamak için ClickOnce Artırma.](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)

### <a name="to-change-the-publish-version"></a>Yayımlama sürümünü değiştirmek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **özellikler'Project'a** **tıklayın.**

2. Yayımla **sekmesine** tıklayın.

3. Sürümü **Yayımla alanında** Ana, **Küçük,** **Derleme** **veya** Düzeltme sürüm **numaralarını** artırarak.

    > [!NOTE]
    > Bir sürüm numarasını hiçbir zaman azalmamanız gerekir; bunu yapmak öngörülemeyen güncelleştirme davranışına neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)
- [Nasıl yapılır: Yayımlama sürümünü ClickOnce olarak artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl ClickOnce: ClickOnce Sihirbazı'nı kullanarak bir uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)