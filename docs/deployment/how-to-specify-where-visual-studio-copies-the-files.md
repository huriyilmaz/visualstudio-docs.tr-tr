---
title: Dosyaların kopyalanacağı yeri belirtin | Microsoft Docs
description: Uygulama dosyalarının ve bildiriminin yer aldığı konumu belirten bir ClickOnce uygulaması için yayımlama konumu özelliğini ayarlamayı öğrenin.
ms.custom:
- SEO-VS-2020
- seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cb659b2191e156aac303678374fe726856d9a77
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349600"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Nasıl yapılır: Visual Studio 'Nun dosyaları nereye kopyaladığını belirtme
ClickOnce kullanarak bir uygulamayı yayımladığınızda, `Publish Location` özelliği uygulama dosyalarının ve bildiriminin bulunduğu konumu belirtir. Bu bir dosya yolu veya bir FTP sunucusunun yolu olabilir.

 `Publish Location`Özelliği **Proje Tasarımcısı** ' nın **Yayımla** sayfasında veya Yayımla Sihirbazı ' nı kullanarak belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> ClickOnce kullanarak bir uygulamanın birden fazla sürümünü yüklediğinizde yükleme, uygulamanın önceki sürümlerini belirttiğiniz Yayımla konumundaki arşiv adlı bir klasöre taşır. Önceki sürümlerin bu şekilde arşivlenmesi, yükleme dizinini önceki sürümden klasörlerin temizlenmesini önler.

### <a name="to-specify-a-publishing-location"></a>Yayımlama konumu belirtmek için

1. **Çözüm Gezgini** ' de bir proje seçiliyken, **Proje** menüsünde **Özellikler** ' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Yayımlama konumu** alanına, aşağıdaki biçimlerden birini kullanarak yayımlama konumu girin:

   - Bir dosya paylaşımında veya disk yolunda yayımlamak için, yolu bir UNC yolu ( *\\ \server\applicationname* ) veya bir dosya yolu ( *c:\Deploy\ApplicationName* ) kullanarak girin.

   - Bir FTP sunucusuna yayımlamak için, <em>FTP://FTP.Microsoft.com/ \<ApplicationName> </em>biçimini kullanarak yolu girin.

     Göz at ( **...** ) düğmesinin çalışması Için **Yayımlama konumu** kutusunda metnin mevcut olması gerektiğini unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)