---
title: UWP uygulamaları için uygulama özellik sayfası
description: Evrensel Platform (UWP) projesinin derleme Windows ve paket bilgilerini ve hedef Windows 10 belirtmek için Uygulama sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/26/2021
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- uwp
ms.openlocfilehash: bb77479468c10e55eb15986caf6c402a80fdeff4
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131127617"
---
# <a name="application-property-page-uwp-projects"></a>Uygulama özellik sayfası (UWP projeleri)

Evrensel **Platform** (UWP) projesinin derleme ve paket bilgilerini belirtmek ve uygulama ve Windows ve sonrakini hedeflemek için Uygulama Windows 10 sayfasını kullanın.

![Uygulama özellik sayfası](media/application-page-uwp.png)

Uygulama sayfasına **erişmek** için uygulama sayfasındaki proje **Çözüm Gezgini.** Ardından menü **Project**  >  **Özellikler'i** seçin. Özellik sayfaları Uygulama **sekmesinde** açılır.

## <a name="general-section"></a>Genel bölümü

**Derleme adı** &mdash; Derleme bildirimini tutacak çıkış dosyasının adını belirtir.

Bu özelle program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.AssemblyName%2A> .

**Varsayılan ad alanı** &mdash; Projeye eklenen dosyalar için temel ad alanını belirtir. Ad alanları hakkında daha fazla bilgi için bkz. Ad Alanları [(C# programlama kılavuzu)](/dotnet/csharp/programming-guide/namespaces/), [Ad Alanları (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces)veya [Ad Alanları (C++)](/cpp/cpp/namespaces-cpp).

Bu özelle program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.RootNamespace%2A> .

**Derleme Bilgileri** &mdash; Bu düğmeyi seçerek [Derleme Bilgileri iletişim kutusu görüntülenir.](../../ide/reference/assembly-information-dialog-box.md)

**Paket Bildirimi** &mdash; Bu düğmeyi seçmek bildirim tasarımcısını açar. Bildirim tasarımcısına, içinde _Package.appxmanifest_ dosyası seçerek de **Çözüm Gezgini.** Daha fazla bilgi için [bkz. Bildirim tasarımcısı ile paket yapılandırma.](/windows/msix/package/packaging-uwp-apps#configure-your-project)

## <a name="targeting-section"></a>Hedefleme bölümü

Bu bölümdeki açılan listeleri kullanarak uygulamanıza yönelik Windows 10 sürümünü ve en düşük sürümünü ayarlayın. Windows 10'nin en son sürümünü hedeflemeniz ve bir kurumsal uygulama geliştiriyorsanız eski bir en düşük sürümü de desteklemeniz önerilir. Hangi sürümler ve sonraki Windows 10 hakkında daha fazla bilgi için [bkz. UWP sürümü seçme.](/windows/uwp/updates-and-versions/choose-a-uwp-version)

::: moniker range="vs-2017"

Platform hedefleme hakkında daha fazla bilgi Visual Studio bkz. [Platform hedefleme.](/visualstudio/releases/2017/vs2017-compatibility-vs#platform-targeting)

::: moniker-end

::: moniker range="vs-2019"

Platform hedefleme hakkında daha fazla bilgi Visual Studio bkz. [Platform hedefleme.](/visualstudio/releases/2019/compatibility#platform-targeting)

::: moniker-end

::: moniker range="vs-2022"

Platform hedefleme hakkında daha fazla bilgi Visual Studio bkz. [Platform hedefleme.](/visualstudio/releases/2022/compatibility#platform-targeting)

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [İlk UWP uygulamanızı oluşturma](/windows/uwp/get-started/your-first-app)
- [UWP sürümü seçme](/windows/uwp/updates-and-versions/choose-a-uwp-version)
