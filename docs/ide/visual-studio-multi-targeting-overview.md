---
title: Hedeflenen .NET çerçeveleri
ms.date: 02/06/2018
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
ms.openlocfilehash: ec81b38ab68c327f25c9f94b6329a700e2662383
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594129"
---
# <a name="framework-targeting-overview"></a>Çerçeve hedefleme genel bakış

Visual Studio 'da, projenizin hedeflemesini istediğiniz .NET sürümünü belirtebilirsiniz. Framework hedefleme, uygulamanın yalnızca belirtilen Framework sürümünde kullanılabilen işlevselliği kullanmasını garantilemeye yardımcı olur. .NET Framework uygulamaların başka bir bilgisayarda çalışması için, uygulamanın hedeflediği çerçeve sürümü, bilgisayarda yüklü olan Framework sürümüyle uyumlu olmalıdır.

Visual Studio çözümü, .NET 'in farklı sürümlerini hedefleyen projeler içerebilir.

Hedef çerçeveler hakkında daha fazla bilgi için bkz. [hedef çerçeveler](/dotnet/standard/frameworks).

> [!TIP]
> Ayrıca, farklı platformlar için uygulamaları hedefleyebilirsiniz. Daha fazla bilgi için [çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Çerçeve hedefleme özellikleri

Çerçeve hedefleme şu özellikleri içerir:

- Önceki bir Framework sürümünü hedefleyen bir projeyi açtığınızda, Visual Studio projeyi otomatik olarak yükseltebilir veya hedefi olduğu gibi bırakabilir.

- Bir .NET Framework projesi oluşturduğunuzda, hedeflemek istediğiniz .NET Framework sürümünü belirtebilirsiniz.

- Çoklu çerçeveleri tek bir projede [hedefleyebilirsiniz](/dotnet/standard/frameworks#how-to-specify-target-frameworks) .

- Aynı çözümdeki birçok projenin her birinde .NET 'in farklı bir sürümünü hedefleyebilirsiniz.

- Mevcut projenin hedeflediği .NET sürümünü değiştirebilirsiniz.

   Bir projenin hedeflediği .NET sürümünü değiştirdiğinizde, Visual Studio başvuru ve yapılandırma dosyalarında gerekli tüm değişiklikleri yapar.

Önceki bir Framework sürümünü hedefleyen bir projede çalışırken, Visual Studio geliştirme ortamını dinamik olarak aşağıdaki gibi değiştirir:

- Öğelere **Yeni Öğe Ekle** iletişim kutusu, **Yeni Başvuru Ekle** iletişim kutusu ve **hizmet Başvurusu Ekle** kullanılabilir olmayan seçenekleri atlamak için iletişim kutusu hedeflenen sürümü.

- Özel denetimlerinde filtreler **araç kutusu** hedeflenen sürümde olmayanları kaldırın ve yalnızca göstermek için birden çok denetim uygun olduğunda en güncel kontrol eder.

- Hedeflenen sürümde kullanılamayan dil özelliklerini atlamak için **IntelliSense** 'e filtre uygular.

- **Özellikler** penceresindeki özellikleri, hedeflenen sürümde mevcut olmayan olanları atlamak için filtreler.

- Hedeflenen sürümde kullanılamayan seçenekleri atlamak için menü seçeneklerini filtreler.

- Derlemeler için derleyici ve derleyici seçenekleri hedeflenen sürüm için uygun sürümünü kullanır.

> [!NOTE]
> - Çerçeve hedefleme, uygulamanızın doğru şekilde çalışacağını garanti etmez. Hedeflenen sürümde çalışacağından çalıştığından emin olmak için uygulamanızı test etmeniz gerekir.
> - 2,0 .NET Framework aşağıdaki Framework sürümlerini hedeflenemez.

## <a name="select-a-target-framework-version"></a>Hedef framework sürümü seçin

Bir .NET Framework projesi oluşturduğunuzda, bir proje şablonu seçtikten sonra hedef .NET Framework sürümünü seçebilirsiniz. Seçili şablon türü için geçerli olan yüklü framework sürümleri kullanılabilir çerçeveleri listesini içerir. Non-.NET Framework proje şablonları için, örneğin .NET Core şablonları için, **çerçeve** açılan listesi görünmez.

::: moniker range="vs-2017"

![VS 2017 ' deki çerçeve açılan düzeyi](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![VS 2019 ' de çerçeve açılan kutusu](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="change-the-target-framework"></a>Hedef çerçeveyi değiştirme

Mevcut bir Visual Basic, C#veya F# projede, proje özellikleri iletişim kutusunda hedef .NET sürümünü değiştirirsiniz. C++ Projelerin hedef sürümünü değiştirme hakkında daha fazla bilgi için, bkz. [hedef Framework ve platform araç takımını değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset) .

1. **Çözüm Gezgini**, değiştirmek istediğiniz proje için sağ tıklama menüsünü açın ve ardından **Özellikler**' i seçin.

1. Sol sütununda **özellikleri** penceresinde seçin **uygulama** sekmesi.

   ![Proje özellikleri uygulama sekmesi](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > UWP uygulaması oluşturduktan sonra, Windows veya .NET 'in hedeflenen sürümünü değiştiremezsiniz.

1. İçinde **hedef Framework'ü** listesinde, istediğiniz sürümü seçin.

1. Görüntülenen doğrulama iletişim kutusunda seçin **Evet** düğmesi.

   Projenin yüklemesi kaldırılır. Yeniden yüklediğinde, yeni seçtiğiniz .NET sürümünü hedefler.

> [!NOTE]
> Kodunuz, hedeflenmeden farklı bir .NET sürümüne başvurular içeriyorsa, kodu derlerken veya çalıştırdığınızda hata iletileri görünebilir. Bu hataları gidermek için başvuruları değiştirin. Bkz. [.net hedefleme hatalarında sorun giderme](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

> [!TIP]
> Hedef çerçeveye bağlı olarak, proje dosyasında aşağıdaki yollarla temsil edilebilir:
>
> - .NET Core uygulaması için: `<TargetFramework>netcoreapp2.1</TargetFramework>`
> - .NET Standard bir uygulama için: `<TargetFramework>netstandard2.0</TargetFramework>`
> - .NET Framework bir uygulama için: `<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>Sistem ve kullanıcı derleme başvurularını çözümleme

.NET sürümünü hedeflemek için, önce uygun derleme başvurularını yüklemeniz gerekir. .Net [İndirmeleri](https://www.microsoft.com/net/download/windows) sayfasına farklı .NET sürümleri için geliştirici paketleri indirebilirsiniz.

.NET Framework projeleri için, **Başvuru Ekle** iletişim kutusu, hedef .NET Framework sürümüne ait olmayan sistem derlemelerini devre dışı bırakarak, bir projeye istem dışı eklenememelidir. (Sistem derlemeleri .NET Framework sürümünde yer alan *. dll* dosyalarıdır.) Hedeflenen sürümden daha yüksek bir çerçeve sürümüne ait olan başvurular çözümlenmeyecektir ve bu tür bir başvuruya bağlı olan denetimler eklenemez. Böyle bir başvuruyu etkinleştirmek istiyorsanız, projenin .NET Framework hedefini başvuruyu içeren bir tane olarak sıfırlayın.

Derleme başvuruları hakkında daha fazla bilgi için bkz: [tasarım zamanında derlemeleri çözme](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>LINQ'i etkinleştirmek

.NET Framework 3.5 veya sonraki sürümler, bir başvuru hedeflediğinizde **System.Core** ve bir proje seviyesinde içeri alma için <xref:System.Linq> (yalnızca Visual Basic'te) otomatik olarak eklenir. LINQ özelliklerini kullanmak istiyorsanız, ayrıca etkinleştirmelisiniz `Option Infer` üzerinde (yalnızca Visual Basic'te). Hedefi önceki bir .NET Framework sürümü ile değiştirirseniz başvuru ve içe aktarma otomatik olarak kaldırılır. Daha fazla bilgi için [LINQ ile çalışma](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef çerçeveler](/dotnet/standard/frameworks)
- [Çoklu sürüm desteği (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Nasıl yapılır: hedef framework ve platform araç takımını (C++) değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
