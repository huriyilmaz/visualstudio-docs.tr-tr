---
title: ClickOnce Windows Vista | üzerinde dağıtım Microsoft Docs
description: Visual Studio com uygulamaları ve ClickOnce için Registration-Free UAC bildirimi oluşturma hakkında bilgi edinebilirsiniz.
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

Windows Vista'Visual Studio Kullanıcı Hesabı Denetimi (UAC) için Visual Studio'de uygulama oluşturmak normalde uygulamanın yürütülebilir dosyasında ikili XML verileri olarak kodlanmış bir ekli bildirim üretir.  ClickOnce ve Registration-Free COM uygulamaları için bir dış bildirim gerekir, bu nedenle Visual Studio ekli bildirim yerine UAC verilerini içeren bu projeler için bir dosya üretir. COM ClickOnce Registration-Free için, Visual Studio *app.manifest* adlı bir dosyadan bilgileri kullanarak dış UAC bildirim bilgileri oluşturulur. Diğer tüm durumlarda Visual Studio UAC verilerini uygulamanın yürütülebilir dosyasına katıştırır.

Visual Studio bildirim oluşturma için aşağıdaki seçenekleri sağlar:

- Ekli bir bildirim kullanın. UAC verilerini uygulamanın yürütülebilir dosyasına ekleme ve normal bir kullanıcı olarak çalıştırma.

   Bu varsayılan ayardır (ClickOnce). Bu ayar, hem iç hem de dış Visual Studio kullanılarak Windows Vista üzerinde çalışan her zamanki şekilde `AsInvoker` destekler.

- Dış bildirim kullanın. *app.manifest* kullanarak bir dış bildirim oluşturma.

   Bu, *app.manifest'daki* bilgileri kullanarak yalnızca dış bildirimi üretir. ClickOnce veya Registration-Free COM kullanarak bir Visual Studio yayımlarsanız, *Visual Studio app.manifest'ı* projeye ekler ve ardından bu seçeneği ekler.

- Bildirim kullanma. Bildirim olmadan uygulamayı oluşturun.

   Bu yaklaşım sanallaştırma olarak da *bilinir.* Önceki sürümlerden gelen mevcut uygulamalarla uyumluluk için bu seçeneği Visual Studio.

  Yeni özellikler, Project  Tasarımcısı'nın Uygulama sayfasında (yalnızca Visual C# projeleri için) ve MSBuild proje dosyası biçiminde kullanılabilir.

  IDE'de UAC bildirim oluşturma Visual Studio yöntemi, proje türüne (Visual C# veya Visual Basic) bağlı olarak farklılık gösterir.

  * Visual C# projelerini bildirim oluşturma için yapılandırma hakkında bilgi için bkz. Uygulama [Sayfası, Project Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Bildirim oluşturma için Visual Basic hakkında bilgi için bkz. Uygulama [Sayfası, Project Tasarımcısı (Visual Basic).](../ide/reference/application-page-project-designer-visual-basic.md)

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [Kullanıcı izinleri ve Visual Studio](/previous-versions/ms165100(v=vs.100))
- [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)