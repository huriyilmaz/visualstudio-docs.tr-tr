---
title: Hedeflenen .NET çerçeveleri
description: Uygulamanın yalnızca belirtilen .NET Framework işlevselliği kullanamalarını sağlamak için projenizin hedeflemesini istediğiniz uygulama sürümünü belirtmeyi öğrenin.
ms.date: 11/19/2021
ms.topic: overview
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 306617c158f6bdfbcb8236dc1661a93f9e9c92e5
ms.sourcegitcommit: ebd651e00fe3bae5914c211c4828219bf7d1fc70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137798554"
---
# <a name="framework-targeting-overview"></a>Çerçeve hedeflemeye genel bakış

Bu Visual Studio projenizin hedeflemesini istediğiniz .NET sürümünü belirterek. Çerçeve hedefleme, uygulamanın yalnızca belirtilen çerçeve sürümünde kullanılabilen işlevleri kullanması garantisini sağlar. Diğer .NET Framework başka bir bilgisayarda çalışması için, uygulamanın hedeflene framework sürümü bilgisayarda yüklü çerçeve sürümüyle uyumlu olmalıdır.

Bir Visual Studio çözümü, .NET'in farklı sürümlerini hedef alan projeler içerebilir.  Ancak, tek bir derleme için başvuru koşullularını kullanarak veya her sürüm için ayrı ikili dosyalar oluşturmak için yalnızca tek bir .NET sürümüne göre derleme yapılsa da dikkat edin.  Hedef çerçeveler hakkında daha fazla bilgi için [bkz. Hedef çerçeveler.](/dotnet/standard/frameworks)

> [!TIP]
> Uygulamaları farklı platformlar için de hedefleyebiliyorsunuz. Daha fazla bilgi için [bkz. Çoklu Hedef.](../msbuild/msbuild-multitargeting-overview.md)

## <a name="framework-targeting-features"></a>Çerçeve hedefleme özellikleri

Çerçeve hedefleme aşağıdaki özellikleri içerir:

- Önceki bir çerçeve sürümünü hedef alan bir projeyi Visual Studio projeyi otomatik olarak yükseltebilirsiniz veya hedefte olduğu gibi bırakabilirsiniz.

- Yeni bir .NET Framework oluşturdukta, hedefley istediğiniz .NET Framework sürümünü belirtsiniz.

- Tek bir [projede birden çok çerçeveyi](/dotnet/standard/frameworks#how-to-specify-target-frameworks) hedefleysiniz.

- Aynı çözümde yer alan birkaç projeden her biri için farklı bir .NET sürümünü hedefleysiniz.

- Mevcut bir projenin hedefley olduğu .NET sürümünü değiştirebilirsiniz.

   Bir projenin hedeflemektedir .NET sürümünü değiştirirken, Visual Studio ve yapılandırma dosyalarında gerekli değişiklikleri yapar.

Daha önceki bir çerçeve sürümünü hedef alan bir proje üzerinde Visual Studio aşağıdaki gibi geliştirme ortamını dinamik olarak değiştirir:

- Yeni Öğe Ekle **iletişim** kutusundaki öğeleri,  Yeni Başvuru Ekle iletişim  kutusunu ve Hizmet Başvurusu Ekle sürümde mevcut olan seçenekleri atlar.

- Hedeflenen sürümde **mevcut olmayanları** kaldırmak ve birden çok denetim kullanılabilir olduğunda yalnızca en güncel denetimleri göstermek için Araç Kutusu'daki özel denetimleri filtreler.

- Hedeflenen sürümde mevcut olmayan dil özelliklerini atlarken **IntelliSense'i** filtreler.

- Hedeflenen sürümde **mevcut** olmayan özellikleri atlarken Özellikler penceresindeki özellikleri filtreler.

- Hedeflenen sürümde mevcut olmayan seçenekleri at etmek için menü seçeneklerini filtreler.

- Derlemeler için, hedeflenen sürüm için uygun derleyici sürümünü ve derleyici seçeneklerini kullanır.

> [!NOTE]
> - Çerçeve hedeflemesi, uygulamanın doğru şekilde çalıştırılamayacak şekilde garanti edilemez. Hedeflenen sürümde çalıştırıldıklarına emin olmak için uygulamanızı test edin.
> - 2.0'dan .NET Framework çerçeve sürümlerini hedefleyesiniz.

## <a name="select-a-target-framework-version"></a>Hedef çerçeve sürümünü seçme

Bir proje .NET Framework proje şablonu .NET Framework hedef sürümü seçebilirsiniz. Kullanılabilir çerçeveler listesi, seçilen şablon türü için geçerli olan yüklü çerçeve sürümlerini içerir. .NET Core .NET Framework gibi diğer proje şablonları için **Framework** açılan listesi görünmez.

::: moniker range="vs-2017"

![VS 2017'de Çerçeve açılan listesinde](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range="vs-2019"

![VS 2019'da Çerçeve açılan listesinde](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

::: moniker range="vs-2022"

:::image type="content" source="media/vs-2022/configure-new-project-framework.png" alt-text="Visual Studio 2022'de Framework açılan listesinin ekran görüntüsü.":::

::: moniker-end

## <a name="change-the-target-framework"></a>Hedef çerçeveyi değiştirme

Mevcut bir Visual Basic, C# veya F# projesinde, proje özellikleri iletişim kutusunda hedef .NET sürümünü değiştirirsiniz. C++ projeleri için hedef sürümü değiştirme hakkında bilgi için bkz. Bunun yerine hedef [çerçeveyi ve platform araç kümesi değiştirme.](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)

::: moniker range="<=vs-2019"
1. Bu **Çözüm Gezgini,** değiştirmek istediğiniz projenin sağ tıklama bağlam menüsünü açın ve ardından Özellikler'i **seçin.**

1. Özellikler penceresinin sol **sütununda** Uygulama **sekmesini** seçin.

   ![Project özellikleri Uygulama sekmesi](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > Bir UWP uygulaması oluşturdukta, Windows veya .NET'in hedeflenen sürümünü değiştiremezsiniz.

1. Hedef **Çerçeve listesinde** istediğiniz sürümü seçin.

1. Görüntülenen doğrulama iletişim kutusunda Evet **düğmesini** seçin.

   Projenin yüklemesi kaldırılır. Yeniden yüklensin, az önce seçtiğiniz .NET sürümünü hedefler.
::: moniker-end

::: moniker range="vs-2022"
1. Bu **Çözüm Gezgini,** değiştirmek istediğiniz projenin sağ tıklama bağlam menüsünü açın ve ardından Özellikler'i **seçin.**

1. Özellikler penceresinin sol **sütununda** Uygulama **sekmesini** seçin.

   > [!NOTE]
   > Bir UWP uygulaması oluşturdukta, Windows veya .NET'in hedeflenen sürümünü değiştiremezsiniz.

1. Hedef **Çerçeve listesinde** istediğiniz sürümü seçin.

   :::image type="content" source="media/vs-2022/project-properties-application-tab-framework.png" alt-text=".NET Framework Project iletişim kutusunun ekran görüntüsü.":::

1. Görüntülenen doğrulama iletişim kutusunda Evet **düğmesini** seçin.

   Projenin yüklemesi kaldırılır. Yeniden yüklensin, az önce seçtiğiniz .NET sürümünü hedefler.
::: moniker-end

> [!NOTE]
> Kodunuz hedeflenenden farklı bir .NET sürümüne başvuru içeriyorsa, kodu derlerken veya çalıştırsanız hata iletileri görünebilir. Bu hataları çözmek için başvuruları değiştirebilirsiniz. Bkz. [.NET hedefleme hatalarını giderme.](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)

> [!TIP]
> Hedef çerçeveye bağlı olarak, proje dosyasında aşağıdaki yollarla temsil olabilir:
>
> - .NET Core uygulaması için: `<TargetFramework>netcoreapp2.1</TargetFramework>`
> - Bir .NET Standard için: `<TargetFramework>netstandard2.0</TargetFramework>`
> - Bir .NET Framework için:`<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>Sistem ve kullanıcı derleme başvurularını çözümleme

Bir .NET sürümünü hedeflemek için önce uygun derleme başvurularını yüklemeniz gerekir. .NET'in farklı sürümleri için geliştirici paketlerini [.NET indirmeleri sayfasından indirebilirsiniz.](https://www.microsoft.com/net/download/windows)

Daha .NET Framework projelerde,  Başvuru Ekle iletişim kutusu, hedef .NET Framework sürümüyle ilgili olan sistem derlemelerini devre dışı bırakarak yanlışlıkla bir projeye eklenmelerini sağlar. (Sistem derlemeleri *.dll* bir sürüme dahil olan .NET Framework dosyalardır.) Hedeflenen sürümden daha yüksek bir çerçeve sürümüne ait olan başvurular çözümlanmaz ve böyle bir başvuruya bağımlı denetimler ek edilemez. Böyle bir başvuru etkinleştirmek için projenin .NET Framework hedefini başvuru içeren bir başvuruya sıfırlayın.

Derleme başvuruları hakkında daha fazla bilgi için [bkz. Derlemeleri tasarım zamanında çözümleme.](../msbuild/resolving-assemblies-at-design-time.md)

## <a name="enable-linq"></a>LINQ'yi etkinleştirme

.NET Framework 3.5 veya sonraki bir sonraki bir 3.5'i hedefleyebilirsiniz. **System.Core** başvurusu ve için proje düzeyi <xref:System.Linq> içeri aktarma (yalnızca Visual Basic için) otomatik olarak eklenir. LINQ özelliklerini kullanmak için de açmalısınız `Option Infer` (yalnızca Visual Basic). Hedefi önceki bir sürüme değiştirirsiniz, başvuru ve içeri aktarma otomatik olarak .NET Framework kaldırılır. Daha fazla bilgi için [bkz. LINQ ile çalışma.](/dotnet/csharp/tutorials/working-with-linq)

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef çerçeveler](/dotnet/standard/frameworks)
- [Çoklu hedefleme (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Nasıl bilinir: Hedef çerçeveyi ve platform araç kümesini değiştirme (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
