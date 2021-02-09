---
title: ClickOnce Publish sürümünü ayarla | Microsoft Docs
description: Uygulamanın bir güncelleştirme olup olmadığını belirleyen ClickOnce Publish Version özelliğini ayarlamayı öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: 71d74d8b16e058b150187a231a1f3a7323c0c612
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885033"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Nasıl yapılır: ClickOnce yayımlama sürümünü ayarlama
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Özelliği, yayımlamakta olduğunuz uygulamanın güncelleştirme olarak değerlendirilip değerlendirilmeyeceğini belirler. Sürüm her artışında, uygulama bir güncelleştirme olarak yayımlanır.

 `Publish Version`Özelliği, **Proje Tasarımcısı**' nın **Yayımla** sayfasında ayarlanabilir.

> [!NOTE]
> Uygulamanın her yayımlanışında özelliği otomatik olarak arttacak bir proje seçeneği vardır `Publish Version` ; Bu seçenek varsayılan olarak etkindir. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce Yayım sürümünü otomatik olarak artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Yayımla sürümünü değiştirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Sürümü Yayımla** alanında, **ana**, **İkincil**, **derleme** veya **Düzeltme** sürüm numaralarını artırın.

    > [!NOTE]
    > Sürüm numarasını hiçbir şekilde azaltmamanız gerekir; Bunun yapılması öngörülemeyen güncelleştirme davranışına neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)
- [Nasıl yapılır: ClickOnce Yayım sürümünü otomatik olarak artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)