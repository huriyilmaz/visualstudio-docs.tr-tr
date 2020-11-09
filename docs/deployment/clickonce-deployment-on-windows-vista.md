---
title: Windows Vista 'da ClickOnce dağıtımı | Microsoft Docs
description: Visual Studio 'Nun, bir dış bildirim gerektiren ClickOnce ve Registration-Free COM uygulamaları için dış UAC bildirimi nasıl oluşturduğu hakkında bilgi edinin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e09225339a87c55c31d27d26b129e199385e99
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383085"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista'da ClickOnce dağıtımı

Windows Vista 'da Kullanıcı hesabı denetimi (UAC) için Visual Studio 'da uygulamalar derleme, normalde, uygulamanın yürütülebilir dosyasında ikili XML verileri olarak kodlanmış bir katıştırılmış bildirim oluşturur.  ClickOnce ve Registration-Free COM uygulamaları için bir dış bildirim gerekir, bu nedenle Visual Studio bu projeler için katıştırılmış bir bildirim yerine UAC verilerini içeren bir dosya oluşturur. ClickOnce ve Registration-Free COM dağıtımları için, Visual Studio dış UAC bildirim bilgileri oluşturmak için *app. manifest* adlı bir dosyadaki bilgileri kullanır. Diğer tüm durumlarda, Visual Studio UAC verilerini uygulamanın yürütülebilir dosyasına katıştırır.

Visual Studio, bildirim oluşturma için aşağıdaki seçenekleri sağlar:

- Gömülü bir bildirim kullanın. UAC verilerini uygulamanın yürütülebilir dosyasına ekleyin ve normal bir kullanıcı olarak çalıştırın.

   Bu, varsayılan ayardır (ClickOnce kullanmadığınız durumlar dışında). Bu ayar, kullanarak Visual Studio 'nun Windows Vista 'da çalıştığı olağan şekilde, hem iç hem de dış bildirim oluşturma ile birlikte desteklenir `AsInvoker` .

- Dış bildirim kullanın. *App. manifest* kullanarak bir dış bildirim oluşturun.

   Bu, *app. manifest* 'teki bilgileri kullanarak yalnızca dış bildirimi oluşturur. ClickOnce veya Registration-Free COM kullanarak bir uygulamayı yayımladığınızda, Visual Studio projeye *app. manifest* ekler ve sonra bu seçeneği ekler.

- Bildirim yok ' u kullanın. Bildirimi olmayan uygulamayı oluşturun.

   Bu yaklaşım *sanallaştırma* olarak da bilinir. Visual Studio 'nun önceki sürümlerindeki mevcut uygulamalarla uyumluluk için bu seçeneği kullanın.

  Yeni özellikler, proje Tasarımcısı 'nın **uygulama** sayfasında (yalnızca Visual C# projeleri için) ve MSBuild proje dosyası biçiminde bulunur.

  Visual Studio IDE 'de UAC bildirim oluşturmayı yapılandırma yöntemi, proje türüne (Visual C# veya Visual Basic) göre farklılık gösterir.

  * Visual C# projelerini bildirim üretimi için yapılandırma hakkında bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Bildirim üretimi için Visual Basic projeleri yapılandırma hakkında daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [Kullanıcı izinleri ve Visual Studio](/previous-versions/ms165100(v=vs.100))
- [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)