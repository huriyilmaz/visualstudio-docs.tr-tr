---
title: UWP uygulamaları için uygulama Özellik sayfası
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 01edb1871388cdc31f6c92ff25d10c876dfebc64
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651947"
---
# <a name="application-property-page-uwp-projects"></a>Uygulama özellik sayfası (UWP projeleri)

Evrensel Windows Platformu (UWP) projesinin derleme ve paket bilgilerini belirtmek ve Windows 10 sürümünü hedeflemek için **uygulama** özelliği sayfasını kullanın.

![Uygulama özellik sayfası](media/application-page-uwp.png)

**Uygulama** sayfasına erişmek için **Çözüm Gezgini**içinde proje düğümünü seçin. Ardından, menü çubuğunda **proje**  > **Özellikler** ' i seçin. Özellik sayfaları **uygulama** sekmesinde açılır.

## <a name="general-section"></a>Genel Bölüm

**Bütünleştirilmiş kod adı** , derleme bildirimini tutacak çıkış dosyasının adını &mdash;Specifies.

Bu özelliğe program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Varsayılan ad alanı** , projeye eklenen dosyalar için temel ad alanını &mdash;Specifies. Ad alanları hakkında daha fazla bilgi için bkz. [ad alanları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/namespaces/), [ad alanları (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces)veya [ad alanları (C++)](/cpp/cpp/namespaces-cpp).

Bu özelliğe program aracılığıyla erişmek için bkz. <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Derleme bilgileri** &mdash;Choosing bu düğme, [derleme bilgileri iletişim kutusunu](../../ide/reference/assembly-information-dialog-box.md)görüntüler.

**Paket bildirimi** &mdash;Choosing bu düğme bildirim Tasarımcısını açar. Bildirim tasarımcısına Ayrıca **Çözüm Gezgini** _Package. appxmanifest_ dosyası seçilerek de erişilebilir. Daha fazla bilgi için bkz. [bildirim Tasarımcısı ile paket yapılandırma](/windows/uwp/packaging/packaging-uwp-apps#configure-an-app-package).

## <a name="targeting-section"></a>Hedefleme bölümü

Bu bölümdeki açılan listeleri kullanarak uygulamanız için Windows 10 ' un hedef sürümünü ve en düşük sürümünü ayarlayabilirsiniz. Windows 10 ' un en son sürümünü hedefliyorsanız ve bir kurumsal uygulama geliştiriyorsanız, daha eski bir sürümü çok daha destekliyorsanız önerilir. Hangi Windows 10 sürümü seçeceğiniz hakkında daha fazla bilgi için bkz. [UWP sürümü seçme](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Visual Studio 'da Platform hedefleme hakkında daha fazla bilgi için bkz. [Platform hedefleme](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Ayrıca bkz.

- [İlk UWP uygulamanızı oluşturma](/windows/uwp/get-started/your-first-app)
- [UWP sürümü seçin](/windows/uwp/updates-and-versions/choose-a-uwp-version)