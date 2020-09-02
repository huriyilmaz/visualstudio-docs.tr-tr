---
title: Windows Vista 'da ClickOnce dağıtımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e25f9da960b1de8acb1950b2bdd3ab7e61409f17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675470"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista'da ClickOnce Dağıtımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Vista 'da Kullanıcı hesabı denetimi (UAC) için Visual Studio 'da uygulamalar derleme, normalde, uygulamanın yürütülebilir dosyasında ikili XML verileri olarak kodlanmış bir katıştırılmış bildirim oluşturur. ClickOnce ve kayıtsız COM uygulamaları için bir dış bildirim gerektiğinden, Visual Studio katıştırılmış bir bildirim yerine UAC verilerini içeren bu proje türleri için bir dosya oluşturur. Varsayılan olarak, Visual Studio, dış UAC bildirim bilgileri (ClickOnce ve kayıtsız COM dağıtımı için) oluşturmak veya uygulamayı uygulamanın yürütülebilir dosyasına eklemek için (diğer tüm durumlarda) App. manifest adlı bir dosyadaki bilgileri kullanır. Visual Studio, bildirim oluşturma için aşağıdaki seçenekleri sağlar:  
  
- Gömülü bir bildirim kullanın. UAC verilerini uygulamanın yürütülebilir dosyasına ekleyin ve normal kullanıcı olarak çalıştırın.  
  
   Bu, varsayılan ayardır (ClickOnce kullanmadığınız durumlar dışında). Bu ayar, Visual Studio 'Nun Windows Vista 'da çalıştığı her zamanki şekilde destekleyecektir. diğer bir deyişle, bir iç ve dış bildirimin oluşturulması, her ikisi de ile `AsInvoker` .  
  
- Dış bildirim kullanın. App. manifest kullanarak bir dış bildirim oluşturun.  
  
   Bu, App. manifest 'teki bilgileri kullanarak yalnızca dış bildirimi oluşturur. Bir uygulamayı ClickOnce veya kayıtsız COM kullanarak yayımladığınızda, Visual Studio projeye App. manifest ekler ve bu seçeneği ekler.  
  
- Bildirim yok ' u kullanın. Bildirimi olmayan uygulamayı oluşturun.  
  
   Bu yaklaşım *sanallaştırma*olarak da bilinir. Visual Studio 'nun önceki sürümlerindeki mevcut uygulamalarla uyumluluk için bu seçeneği kullanın.  
  
  Yeni özellikler, proje Tasarımcısı 'nın **uygulama** sayfasında (yalnızca Visual C# projeleri için) ve MSBuild proje dosyası biçiminde bulunur.  
  
  Visual Studio IDE 'de UAC bildirim oluşturmayı yapılandırma yönteminin proje türüne göre (Visual C# ve Visual Basic) farklı olduğunu unutmayın.  
  
  Visual C# projelerini bildirim üretimi için yapılandırma hakkında bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Bildirim üretimi için Visual Basic projeleri yapılandırma hakkında daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [Kullanıcı Izinleri ve Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Uygulama sayfası, proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
