---
title: ClickOnce Publish sürümünü ayarla | Microsoft Docs
description: uygulamanın bir güncelleştirme olup olmadığını belirleyen ClickOnce Publish Version özelliğini ayarlamayı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627764"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>nasıl yapılır: ClickOnce publish sürümünü ayarlama
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Özelliği, yayımlamakta olduğunuz uygulamanın güncelleştirme olarak değerlendirilip değerlendirilmeyeceğini belirler. Sürüm her artışında, uygulama bir güncelleştirme olarak yayımlanır.

 `Publish Version`özelliği, **Project tasarımcısının** **yayımla** sayfasında ayarlanabilir.

> [!NOTE]
> Uygulamanın her yayımlanışında özelliği otomatik olarak arttacak bir proje seçeneği vardır `Publish Version` ; Bu seçenek varsayılan olarak etkindir. daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce yayım sürümünü otomatik olarak artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Yayımla sürümünü değiştirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Sürümü Yayımla** alanında, **ana**, **İkincil**, **derleme** veya **Düzeltme** sürüm numaralarını artırın.

    > [!NOTE]
    > Sürüm numarasını hiçbir şekilde azaltmamanız gerekir; Bunun yapılması öngörülemeyen güncelleştirme davranışına neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)
- [nasıl yapılır: ClickOnce publish sürümünü otomatik olarak artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)