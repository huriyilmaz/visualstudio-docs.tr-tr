---
title: Hedeflenen .NET çerçeveleri
ms.date: 03/31/2020
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 48d770f5d88e19c749c1a1e657c369089d4c7afb
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472726"
---
# <a name="framework-targeting-overview"></a>Çerçeve hedeflemegenel bakış

Visual Studio'da,.NET'in projenizin hedeflemesini istediğiniz sürümünü belirtebilirsiniz. Çerçeve hedefleme, uygulamanın yalnızca belirtilen çerçeve sürümünde kullanılabilen işlevselliği kullandığını garanti eder. .NET Framework uygulamalarının başka bir bilgisayarda çalıştırAbilmesi için, uygulama nın hedeflenen çerçeve sürümünün bilgisayarda yüklenen çerçeve sürümüyle uyumlu olması gerekir.

Visual Studio çözümü,.NET'in farklı sürümlerini hedefleyen projeler içerebilir.  Ancak, .NET'in yalnızca tek bir sürümüne karşı tek bir yapı için başvuru koşullu larını kullanarak veya her sürüm için özyinelemeli olarak farklı ikililer oluşturabileceğinizi unutmayın.  Hedef çerçeveler hakkında daha fazla bilgi için [Hedef çerçevelerine](/dotnet/standard/frameworks)bakın.

> [!TIP]
> Ayrıca farklı platformlar için uygulamaları hedefleyebilirsiniz. Daha fazla bilgi için [Multitargeting'e](../msbuild/msbuild-multitargeting-overview.md)bakın.

## <a name="framework-targeting-features"></a>Çerçeve hedefleme özellikleri

Çerçeve hedeflemesi aşağıdaki özellikleri içerir:

- Daha önceki bir çerçeve sürümünü hedefleyen bir proje yi açtığınızda, Visual Studio projeyi otomatik olarak yükseltebilir veya hedefi olduğu gibi bırakabilir.

- Bir .NET Framework projesi oluşturduğunuzda, hedeflemek istediğiniz .NET Framework sürümünü belirtebilirsiniz.

- Tek bir projede [birden çok çerçeveyi hedefleyebilirsiniz.](/dotnet/standard/frameworks#how-to-specify-target-frameworks)

- Aynı çözümdeki birkaç projenin her birinde .NET'in farklı bir sürümünü hedefleyebilirsiniz.

- Varolan bir projenin hedeflediğiniz .NET sürümünü değiştirebilirsiniz.

   Bir projenin hedeflediğiniz .NET sürümünü değiştirdiğinizde, Visual Studio başvurularda ve yapılandırma dosyalarında gerekli değişiklikleri yapar.

Daha önceki bir çerçeve sürümünü hedefleyen bir proje üzerinde çalışırken, Visual Studio geliştirme ortamını aşağıdaki gibi dinamik olarak değiştirir:

- **Yeni Öğe Ekle** iletişim kutusundaki öğeleri, **Yeni Başvuru Ekle** iletişim kutusunu ve Hedefsürüm'te bulunmayan seçenekleri atlayan **Hizmet Başvurusu Ekle** iletişim kutusunu filtreler.

- Hedeflenen sürümde bulunmayandenetimleri kaldırmak ve birden çok denetim kullanılabilir olduğunda yalnızca en güncel denetimleri göstermek için **Araç Kutusu'ndaki** özel denetimleri filtreler.

- **Hedeflenen** sürümde bulunmayan dil özelliklerini atlatır.

- Hedeflenen sürümde bulunmayanözellikleri atlamak için **Özellikler** penceresindeki özellikleri filtreler.

- Hedeflenen sürümde bulunmayan seçenekleri atlamak için menü seçeneklerini filtreler.

- Yapılar için derleyicinin sürümünü ve hedeflenen sürüme uygun derleyici seçeneklerini kullanır.

> [!NOTE]
> - Çerçeve hedefleme, uygulamanızın doğru çalışacağına dair garanti vermez. Uygulamanızın hedeflenen sürüme karşı çalıştığından emin olmak için uygulamanızı test etmeniz gerekir.
> - .NET Framework 2.0'ın altındaki çerçeve sürümlerini hedefleyemezsiniz.

## <a name="select-a-target-framework-version"></a>Hedef çerçeve sürümü seçin

Bir .NET Framework projesi oluşturduğunuzda, proje şablonu seçtikten sonra hedef .NET Framework sürümünü seçebilirsiniz. Kullanılabilir çerçeveler listesi, seçili şablon türü için geçerli olan yüklü çerçeve sürümlerini içerir. Çerçeve proje şablonları non-.NET için ,örneğin .NET Core şablonları, **Framework** açılır listesi görünmez.

::: moniker range="vs-2017"

![VS 2017'de çerçeve düşüşü](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![VS 2019'da çerçeve düşüşü](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="change-the-target-framework"></a>Hedef çerçeveyi değiştirme

Varolan bir Visual Basic, C#veya F# projesinde, proje özellikleri iletişim kutusundaki hedef .NET sürümünü değiştirirsiniz. C++ projeleri için hedef sürümü nasıl değiştireceğiniz hakkında bilgi için, bunun yerine [hedef çerçeve ve platform araç kümesini nasıl değiştireceğiniz](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset) e bakın.

1. **Çözüm Gezgini'nde,** değiştirmek istediğiniz proje için sağ tıklatın menüsünü açın ve ardından **Özellikler'i**seçin.

1. **Özellikler** penceresinin sol sütununda **Uygulama** sekmesini seçin.

   ![Proje özellikleri Uygulama sekmesi](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > Bir UWP uygulaması oluşturduktan sonra, Windows veya .NET'in hedeflenen sürümünü değiştiremezsiniz.

1. Hedef **Çerçeve** listesinde istediğiniz sürümü seçin.

1. Görünen doğrulama iletişim kutusunda **Evet** düğmesini seçin.

   Projenin yüklemesi kaldırılır. Yeniden yüklendiğinde, az önce seçtiğiniz .NET sürümünü hedefler.

> [!NOTE]
> Kodunuz .NET'in hedeflediğiniz farklı bir sürümüne başvurular içeriyorsa, kodu derlediğinizde veya çalıştırdığınızda hata iletileri görünebilir. Bu hataları gidermek için başvuruları değiştirin. [Bkz. Sorun Giderme .NET hedefleme hataları.](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)

> [!TIP]
> Hedef çerçeveye bağlı olarak, proje dosyasında aşağıdaki şekillerde temsil edilebilir:
>
> - Bir .NET Core uygulaması için:`<TargetFramework>netcoreapp2.1</TargetFramework>`
> - Bir .NET Standart uygulaması için:`<TargetFramework>netstandard2.0</TargetFramework>`
> - Bir .NET Framework uygulaması için:`<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>Sistem ve kullanıcı derleme başvurularını çözme

Bir .NET sürümünü hedeflemek için öncelikle uygun montaj başvurularını yüklemeniz gerekir. [.NET'in](https://www.microsoft.com/net/download/windows) farklı sürümleri için geliştirici paketlerini .NET indirmeler sayfasından indirebilirsiniz.

.NET Framework projeleri için, **Başvuru Ekle** iletişim kutusu, projeye yanlışlıkla eklenememesi için hedef .NET Framework sürümüyle ilgili olmayan sistem derlemelerini devre dışı kılabilir. (Sistem derlemeleri .NET Framework sürümünde yer alan *.dll* dosyalarıdır.) Hedeflenen sürümden daha yüksek bir çerçeve sürümüne ait başvurular çözülmez ve böyle bir başvuruya bağlı denetimler eklenemez. Böyle bir başvuruyu etkinleştirmek istiyorsanız, projenin .NET Framework hedefini başvuruyu içeren bir hedefe sıfırlayın.

Derleme başvuruları hakkında daha fazla bilgi için tasarım [zamanında derlemeleri](../msbuild/resolving-assemblies-at-design-time.md)çözümle'ye bakın.

## <a name="enable-linq"></a>LINQ'yi etkinleştir

.NET Framework 3.5 veya sonraki hedefiniyaptığınızda, **System.Core'a** bir <xref:System.Linq> başvuru ve (yalnızca Visual Basic'te) için proje düzeyinde bir alma işlemi otomatik olarak eklenir. LINQ özelliklerini kullanmak istiyorsanız, (yalnızca `Option Infer` Visual Basic'te) açmanız gerekir. Hedefi daha önceki bir .NET Framework sürümüne değiştirirseniz, başvuru ve alma işlemi otomatik olarak kaldırılır. Daha fazla bilgi için [LINQ ile çalışma 'ya](/dotnet/csharp/tutorials/working-with-linq)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef çerçeveler](/dotnet/standard/frameworks)
- [Çok hedefleme (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Nasıl yapılır: Hedef çerçeveyi ve platform araç kümesini değiştirme (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
