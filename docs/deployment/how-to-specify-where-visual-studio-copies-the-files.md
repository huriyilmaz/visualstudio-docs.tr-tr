---
title: Dosyaların kopyalanacağı yeri belirtin | Microsoft Docs
description: uygulama dosyalarının ve bildiriminin bulunacağı konumu belirten ClickOnce bir uygulama için yayımlama konumu özelliğini ayarlamayı öğrenin.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 2425f428f5252c574eacb17c1c404bf06f80279e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080448"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>nasıl yapılır: dosyaları Visual Studio nereye kopyaladığını belirtme
ClickOnce kullanarak bir uygulamayı yayımladığınızda, `Publish Location` özelliği uygulama dosyalarının ve bildiriminin bulunduğu konumu belirtir. Bu bir dosya yolu veya bir FTP sunucusunun yolu olabilir.

 `Publish Location`özelliği, **Project tasarımcısının** **yayımla** sayfasında veya yayımla sihirbazı ' nı kullanarak belirtebilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> ClickOnce kullanarak bir uygulamanın birden fazla sürümünü yüklediğinizde yükleme, uygulamanın önceki sürümlerini belirttiğiniz yayımla konumundaki arşiv adlı bir klasöre taşır. Önceki sürümlerin bu şekilde arşivlenmesi, yükleme dizinini önceki sürümden klasörlerin temizlenmesini önler.

### <a name="to-specify-a-publishing-location"></a>Yayımlama konumu belirtmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Yayımlama konumu** alanına, aşağıdaki biçimlerden birini kullanarak yayımlama konumu girin:

   - Bir dosya paylaşımında veya disk yolunda yayımlamak için, yolu bir UNC yolu (*\\ \server\applicationname*) veya bir dosya yolu (*c:\Deploy\ApplicationName*) kullanarak girin.

   - Bir FTP sunucusuna yayımlamak için, <em>FTP://FTP.Microsoft.com/ \<ApplicationName> </em>biçimini kullanarak yolu girin.

     Göz at (**...**) düğmesinin çalışması Için **Yayımlama konumu** kutusunda metnin mevcut olması gerektiğini unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)