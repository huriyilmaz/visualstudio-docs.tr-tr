---
title: UWP uygulamaları için uygulama özelliği sayfası
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3c8f72d4e1d1caeacd5dfefef5310dc2cef83b92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77173084"
---
# <a name="application-property-page-uwp-projects"></a>Uygulama özelliği sayfası (UWP projeleri)

Evrensel Windows Platformu (UWP) projesinin derleme ve paket bilgilerini belirtmek ve Windows 10 sürümünü hedeflemek için **Uygulama** özelliği sayfasını kullanın.

![Uygulama özelliği sayfası](media/application-page-uwp.png)

**Uygulama** sayfasına erişmek için **Çözüm Gezgini'ndeki**proje düğümündeki bölümü seçin. Ardından menü çubuğunda **Project** > **Properties'i** seçin. Özellik sayfaları **Uygulama** sekmesinde açılır.

## <a name="general-section"></a>Genel bölüm

**Derleme adı,**&mdash;derleme bildirimini tutacak çıktı dosyasının adını belirtir.

Bu özelliğe programlı olarak <xref:VSLangProj.ProjectProperties.AssemblyName%2A>erişmek için bkz.

**Varsayılan ad alanı**&mdash;projeye eklenen dosyalar için temel ad alanını belirtir. Ad alanları hakkında daha fazla bilgi için, [Bkz. Ad Alanları (C# programlama kılavuzu),](/dotnet/csharp/programming-guide/namespaces/) [Ad Alanları (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces)veya [Namespaces (C++)](/cpp/cpp/namespaces-cpp).

Bu özelliğe programlı olarak <xref:VSLangProj.ProjectProperties.RootNamespace%2A>erişmek için bkz.

**Bu**&mdash;düğmeyi seçerken Derleme Bilgileri, [Derleme Bilgileri iletişim kutusunu](../../ide/reference/assembly-information-dialog-box.md)görüntüler.

**Paket Manifestosu**&mdash;Bu düğmeyi seçerek manifesto tasarımcısıaçılır. Manifest tasarımcı da **Solution Explorer** _Package.appxmanifest_ dosya seçerek erişilebilir. Daha fazla bilgi için [bkz.](/windows/msix/package/packaging-uwp-apps#configure-your-project)

## <a name="targeting-section"></a>Hedefleme bölümü

Bu bölümdeki açılır listeleri kullanarak uygulamanız için Windows 10'un hedef sürümünü ve minimum sürümünü ayarlayabilirsiniz. Windows 10'un en son sürümünü hedeflemeniz ve bir kurumsal uygulama geliştiriyorsanız, eski bir minimum sürümü de desteklemeniz önerilir. Hangi Windows 10 sürümünün seçeceği hakkında daha fazla bilgi için [bkz.](/windows/uwp/updates-and-versions/choose-a-uwp-version)

Visual Studio'da platform hedeflemesi hakkında bilgi için [Platform hedeflemesi'ne](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [İlk UWP uygulamanızı oluşturun](/windows/uwp/get-started/your-first-app)
- [UWP sürümü seçin](/windows/uwp/updates-and-versions/choose-a-uwp-version)
