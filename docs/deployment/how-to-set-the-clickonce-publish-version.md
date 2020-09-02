---
title: ClickOnce Publish sürümünü ayarlama | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df5e1d91de14e3da4f188c276ef7dd74943d8978
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382126"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Nasıl yapılır: ClickOnce yayımlama sürümünü ayarlama
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Özelliği, yayımlamakta olduğunuz uygulamanın güncelleştirme olarak değerlendirilip değerlendirilmeyeceğini belirler. Sürüm her artışında, uygulama bir güncelleştirme olarak yayımlanır.

 `Publish Version`Özelliği, **Proje Tasarımcısı**' nın **Yayımla** sayfasında ayarlanabilir.

> [!NOTE]
> Uygulamanın her yayımlanışında özelliği otomatik olarak arttacak bir proje seçeneği vardır `Publish Version` ; Bu seçenek varsayılan olarak etkindir. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce Yayım sürümünü otomatik olarak artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Yayımla sürümünü değiştirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Sürümü Yayımla** alanında, **ana**, **İkincil**, **derleme**veya **Düzeltme** sürüm numaralarını artırın.

    > [!NOTE]
    > Sürüm numarasını hiçbir şekilde azaltmamanız gerekir; Bunun yapılması öngörülemeyen güncelleştirme davranışına neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)
- [Nasıl yapılır: ClickOnce Yayım sürümünü otomatik olarak artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)