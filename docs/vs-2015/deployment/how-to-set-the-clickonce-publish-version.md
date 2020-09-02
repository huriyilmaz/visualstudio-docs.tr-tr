---
title: 'Nasıl yapılır: ClickOnce Publish sürümünü ayarlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ec5d5d742b5a0749d1d5d52cee0a0545dd8570f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64858801"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Nasıl yapılır: ClickOnce Yayım Sürümü'nü Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version` Özelliği, yayımlamakta olduğunuz uygulamanın güncelleştirme olarak değerlendirilip değerlendirilmeyeceğini belirler. Sürüm her artışında, uygulama bir güncelleştirme olarak yayımlanır.  
  
 `Publish Version`Özelliği, **Proje Tasarımcısı**' nın **Yayımla** sayfasında ayarlanabilir.  
  
> [!NOTE]
> Uygulamanın her yayımlanışında özelliği otomatik olarak arttacak bir proje seçeneği vardır `Publish Version` ; Bu seçenek varsayılan olarak etkindir. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce Yayım sürümünü otomatik olarak artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Yayımla sürümünü değiştirmek için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** sekmesine tıklayın.  
  
3. **Sürümü Yayımla** alanında, **ana**, **İkincil**, **derleme**veya **Düzeltme** sürüm numaralarını artırın.  
  
    > [!NOTE]
    > Sürüm numarasını hiçbir şekilde azaltmamanız gerekir; Bunun yapılması öngörülemeyen güncelleştirme davranışına neden olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güncelleştirme stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Nasıl yapılır: ClickOnce Yayım sürümünü otomatik olarak artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
