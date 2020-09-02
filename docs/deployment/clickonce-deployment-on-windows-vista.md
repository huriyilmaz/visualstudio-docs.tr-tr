---
title: Windows Vista 'da ClickOnce dağıtımı | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4beefddd429384fadda71d9742e8c0fac606c38e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900508"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista'da ClickOnce dağıtımı

Windows Vista 'da Kullanıcı hesabı denetimi (UAC) için Visual Studio 'da uygulamalar derleme, normalde, uygulamanın yürütülebilir dosyasında ikili XML verileri olarak kodlanmış bir katıştırılmış bildirim oluşturur.  ClickOnce ve kayıtsız COM uygulamaları için bir dış bildirim gerekir, bu nedenle Visual Studio bu projeler için katıştırılmış bir bildirim yerine UAC verilerini içeren bir dosya oluşturur. ClickOnce ve kayıtsız COM dağıtımları için, Visual Studio dış UAC bildirim bilgileri oluşturmak için *app. manifest* adlı bir dosyadaki bilgileri kullanır. Diğer tüm durumlarda, Visual Studio UAC verilerini uygulamanın yürütülebilir dosyasına katıştırır.

Visual Studio, bildirim oluşturma için aşağıdaki seçenekleri sağlar:

- Gömülü bir bildirim kullanın. UAC verilerini uygulamanın yürütülebilir dosyasına ekleyin ve normal bir kullanıcı olarak çalıştırın.

   Bu, varsayılan ayardır (ClickOnce kullanmadığınız durumlar dışında). Bu ayar, kullanarak Visual Studio 'nun Windows Vista 'da çalıştığı olağan şekilde, hem iç hem de dış bildirim oluşturma ile birlikte desteklenir `AsInvoker` .

- Dış bildirim kullanın. *App. manifest*kullanarak bir dış bildirim oluşturun.

   Bu, *app. manifest*'teki bilgileri kullanarak yalnızca dış bildirimi oluşturur. Bir uygulamayı ClickOnce veya kayıtsız COM kullanarak yayımladığınızda, Visual Studio projeye *app. manifest* ekler ve sonra bu seçeneği ekler.

- Bildirim yok ' u kullanın. Bildirimi olmayan uygulamayı oluşturun.

   Bu yaklaşım *sanallaştırma*olarak da bilinir. Visual Studio 'nun önceki sürümlerindeki mevcut uygulamalarla uyumluluk için bu seçeneği kullanın.

  Yeni özellikler, proje Tasarımcısı 'nın **uygulama** sayfasında (yalnızca Visual C# projeleri için) ve MSBuild proje dosyası biçiminde bulunur.

  Visual Studio IDE 'de UAC bildirim oluşturmayı yapılandırma yöntemi, proje türüne (Visual C# veya Visual Basic) göre farklılık gösterir.

  * Visual C# projelerini bildirim üretimi için yapılandırma hakkında bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Bildirim üretimi için Visual Basic projeleri yapılandırma hakkında daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [Kullanıcı izinleri ve Visual Studio](https://msdn.microsoft.com/library/d5c55084-1e7b-4b61-b478-137db01c0fc0)
- [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)