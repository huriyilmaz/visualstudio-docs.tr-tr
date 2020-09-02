---
title: 'Nasıl yapılır: Visual Studio 2015 dosyaları kopyaladığını belirtme | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8759145dd4a7647cad6e9964ae1f1c97d333b626
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65226166"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Nasıl yapılır: Visual Studio'nun Dosyaları Nereye Kopyalayacağını Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce kullanarak bir uygulamayı yayımladığınızda, `Publish Location` özelliği uygulama dosyalarının ve bildiriminin bulunduğu konumu belirtir. Bu bir dosya yolu veya bir FTP sunucusunun yolu olabilir.

 `Publish Location`Özelliği **Proje Tasarımcısı**' nın **Yayımla** sayfasında veya Yayımla Sihirbazı ' nı kullanarak belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> ClickOnce kullanarak bir uygulamanın birden fazla sürümünü yüklediğinizde yükleme, uygulamanın önceki sürümlerini belirttiğiniz Yayımla konumundaki arşiv adlı bir klasöre taşır. Önceki sürümlerin bu şekilde arşivlenmesi, yükleme dizinini önceki sürümden klasörlerin temizlenmesini önler.

### <a name="to-specify-a-publishing-location"></a>Yayımlama konumu belirtmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Yayımlama konumu** alanına, aşağıdaki biçimlerden birini kullanarak yayımlama konumu girin:

   - Bir dosya paylaşımında veya disk yolunda yayımlamak için, yolu bir UNC yolu ( \\ \Server\applicationname) veya bir dosya yolu (C:\Deploy\ApplicationName) kullanarak girin.

   - Bir FTP sunucusuna yayımlamak için FTP:/ftp.microsoft.com/ApplicationName biçimini kullanarak yolu girin \/ .

     Göz at (**...**) düğmesinin çalışması Için **Yayımlama konumu** kutusunda metnin mevcut olması gerektiğini unutmayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md) [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) yayımlama
