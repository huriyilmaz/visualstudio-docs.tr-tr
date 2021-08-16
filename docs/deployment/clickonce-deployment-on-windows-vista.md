---
title: ClickOnce Windows Vista 'da dağıtım | Microsoft Docs
description: Visual Studio, dış bildirim gerektiren ClickOnce ve Registration-Free COM uygulamaları için dış UAC bildirimi oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 0da4733f77f9f4d2b896d93f4aba9ec6d05bcadd411f2d2269e2d67ff8e1f016
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452998"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista'da ClickOnce dağıtımı

Windows Vista 'daki kullanıcı hesabı denetimi (UAC) için Visual Studio uygulama oluşturmak, normalde uygulamanın yürütülebilir dosyasında ikili XML verileri olarak kodlanmış bir katıştırılmış bildirim oluşturur.  ClickOnce ve Registration-Free COM uygulamaları bir dış bildirim gerektirir, bu nedenle Visual Studio katıştırılmış bir bildirim yerine bu projeler için UAC verilerini içeren bir dosya oluşturur. ClickOnce ve Registration-Free COM dağıtımları için Visual Studio, dış UAC bildirim bilgileri oluşturmak için *app. manifest* adlı bir dosyadaki bilgileri kullanır. diğer tüm durumlarda, Visual Studio UAC verilerini uygulamanın yürütülebilir dosyasına katıştırır.

Visual Studio, bildirim oluşturma için aşağıdaki seçenekleri sağlar:

- Gömülü bir bildirim kullanın. UAC verilerini uygulamanın yürütülebilir dosyasına ekleyin ve normal bir kullanıcı olarak çalıştırın.

   Bu, varsayılan ayardır (ClickOnce kullanmadığınız durumlar dışında). bu ayar, kullanarak hem iç hem de dış bildirim oluşturma ile Windows Vista 'da Visual Studio çalıştığı olağan şekilde destekler `AsInvoker` .

- Dış bildirim kullanın. *App. manifest* kullanarak bir dış bildirim oluşturun.

   Bu, *app. manifest*'teki bilgileri kullanarak yalnızca dış bildirimi oluşturur. ClickOnce veya Registration-Free COM kullanarak bir uygulamayı yayımladığınızda Visual Studio projeye *app. manifest* ekler ve sonra bu seçeneği ekler.

- Bildirim yok ' u kullanın. Bildirimi olmayan uygulamayı oluşturun.

   Bu yaklaşım *sanallaştırma* olarak da bilinir. Visual Studio eski sürümlerinden mevcut uygulamalarla uyumluluk için bu seçeneği kullanın.

  yeni özellikler, Project tasarımcısının **uygulama** sayfasında (yalnızca Visual C# projeleri için) ve MSBuild proje dosya biçiminde bulunur.

  Visual Studio ıde 'de UAC bildirim oluşturmayı yapılandırma yöntemi, proje türüne (Visual C# veya Visual Basic) göre farklılık gösterir.

  * Visual C# projelerini bildirim üretimi için yapılandırma hakkında bilgi için bkz. [uygulama sayfası, Project tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * bildirim üretimi için Visual Basic projeleri yapılandırma hakkında daha fazla bilgi için bkz. [uygulama sayfası, Project tasarımcı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [Kullanıcı izinleri ve Visual Studio](/previous-versions/ms165100(v=vs.100))
- [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)