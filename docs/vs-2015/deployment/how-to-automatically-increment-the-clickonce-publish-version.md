---
title: 'Nasıl yapılır: ClickOnce Yayım sürümünü otomatik olarak artırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 50faf70e8eda6ef7ab01201102540729497eb87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683918"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Nasıl yapılır: ClickOnce Yayım Sürümünü Otomatik Olarak Artırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir uygulamayı yayımlarken [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , `Publish Version` özelliği değiştirmek uygulamanın bir güncelleştirme olarak yayımlanmasına neden olur. Varsayılan olarak, Visual Studio `Revision` `Publish Version` uygulamayı her yayımlaışınızda otomatik olarak sayısını artırır.  
  
 Bu davranışı **Proje Tasarımcısı**' nın **Yayımla** sayfasında devre dışı bırakabilirsiniz.  
  
> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Yayımlama sürümünü otomatik olarak arttırmadan devre dışı bırakmak için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** sekmesine tıklayın.  
  
3. **Sürümü Yayımla** bölümünde, **her sürüm Için düzeltmeyi otomatik olarak artır** onay kutusunu temizleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ClickOnce yayımlama sürümünü ayarlama](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
