---
title: Dosyaların nereye kopyalayıp kopyalan | Microsoft Docs
description: Uygulama dosyalarının ve bildirimin bulunduğu konumu belirten ClickOnce Yayımlama Konumu özelliğini ayarlamayı öğrenin.
ms.custom:
- SEO-VS-2020
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
ms.openlocfilehash: aa2e67f29c087b33a9614fab7b851de884034e9e
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970886"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Nasıl kullanılır: Dosyaların Visual Studio nerede kopyalay olduğunu belirtme
Uygulama yayımlamak için ClickOnce `Publish Location` özelliği, uygulama dosyalarının ve bildirimin bulunduğu konumu belirtir. Bu bir dosya yolu veya FTP sunucusunun yolu olabilir.

 Özelliğini, Project `Publish Location` **Tasarımcısı'nın** **Yayımla sayfasında veya** Yayımlama Sihirbazı'nı kullanarak belirtebilirsiniz. Daha fazla bilgi için [bkz. Yayımlama Sihirbazı'nı ClickOnce Uygulama Yayımlama.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

> [!NOTE]
> ClickOnce kullanarak bir uygulamanın birden fazla sürümünü yükleyebilirsiniz. Yükleme, uygulamanın önceki sürümlerini belirttiğiniz yayımlama konumu olan Arşiv adlı bir klasöre taşır. Önceki sürümlerin bu şekilde arşivlenmesi, yükleme dizinini önceki sürümden klasörlerden uzak tutar.

### <a name="to-specify-a-publishing-location"></a>Yayımlama konumu belirtmek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **Project'a** **tıklayın.**

2. Yayımla **sekmesine** tıklayın.

3. Yayımlama **Konumu alanına** aşağıdaki biçimlerden birini kullanarak yayımlama konumunu girin:

   - Bir dosya paylaşımına veya disk yoluna yayımlamak için unc yolu (*\\ \Server\ApplicationName*) veya bir dosya yolu (*C:\Deploy\ApplicationName*) kullanarak yolu girin.

   - Bir FTP sunucusunda yayımlamak için, ftp://ftp.microsoft.com/ <em>biçimini kullanarak \<ApplicationName> yolu girin.</em>

     Gözat ( ... ) düğmesinin **çalışması için** Yayımlama Konumu kutusunda **metin** olması gerektiğini unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uygulama ClickOnce yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl ClickOnce: ClickOnce Sihirbazı'nı kullanarak bir uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)