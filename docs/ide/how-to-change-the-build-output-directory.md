---
title: 'Nasıl kullanılır: Derleme çıkış dizinini değiştirme'
description: Projeniz tarafından oluşturulan çıkışın konumunu yapılandırma temelinde (hata ayıklama, sürüm veya her ikisi için) nasıl belirtebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 09/10/2021
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 21175eedafb9fe5d75c3a1d844098db4190a7aa9
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804733"
---
# <a name="how-to-change-the-build-output-directory"></a>Nasıl kullanılır: Derleme çıkış dizinini değiştirme

Projeniz tarafından oluşturulan çıkışın konumunu yapılandırma temelinde (hata ayıklama, sürüm veya her ikisi için) belirtebilirsiniz.

## <a name="change-the-build-output-directory"></a>Derleme çıkış dizinini değiştirme

1. Projenin özellik sayfalarını açmak için, projedeki proje düğümüne sağ tıklayın **ve Çözüm Gezgini'yi** **seçin.**

2. Proje türünüz temel alarak uygun sekmeyi seçin:

   - C# için Derleme **sekmesini** seçin.
   - Daha Visual Basic Için Derle **sekmesini** seçin.
   - C++ veya JavaScript için Genel **sekmesini** seçin.

3. En üstte bulunan yapılandırma açılan listesinde, çıktı dosyası konumunu değiştirmek istediğiniz yapılandırmayı seçin (**Hata** Ayıklama, **Sürüm** veya Tüm **Yapılandırmalar).**

4. Proje türünüze bağlı olarak &mdash; farklılık gösterir sayfasında çıkış yolu girişini bulun:

   - C# **ve** JavaScript projeleri için çıkış yolu
   - **Proje oluşturma projeleri** için Visual Basic yolu
   - **Projelerin** çıkış Visual C++ dizini

   Çıkış oluşturmak için yolu yazın (mutlak veya kök proje dizinine göre) veya gözat'ı seçen bu klasöre göz atabilirsiniz. 

   ::: moniker range="<=vs-2019"
   ![Visual Studio C# projesi için çıkış yolu özelliği](media/output-path.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Visual Studio C# projesi için çıkış yolu özelliği](media/vs-2022/output-path.png)
   ::: moniker-end

   > [!NOTE]
   > Bazı projeler varsayılan olarak derleme yolunda çerçeve ve çalışma zamanı içerir. Bunu değiştirmek için, Çözüm Gezgini'daki proje düğümüne sağ **tıklayın,** Project **Dosyasını Düzenle'yi seçin** ve şunları ekleyin:

   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Çıkış belirttiğiniz konumda oluşturulamaıyorsa, ilgili yapılandırmayı (örneğin, Hata Ayıklama veya  **Sürüm)** oluşturmak için ilgili yapılandırmayı, ilgili yapılandırmanın menü çubuğundan seçerek Visual Studio.
>
> ::: moniker range="<=vs-2019"
> ![Visual Studio 2019'da yapılandırma seçici oluşturma](media/build-configuration-chooser.png)
> ::: moniker-end
> ::: moniker range=">=vs-2022"
> ![Visual Studio 2019'da yapılandırma seçici oluşturma](media/vs-2022/build-configuration-chooser.png)
> ::: moniker-end

## <a name="build-to-a-common-output-directory"></a>Ortak çıkış dizinine derleme

Varsayılan olarak, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] her projeyi çözümün içindeki kendi klasöründeki bir çözümde oluşturur. Tüm çıkışların aynı klasöre yerleştirillerini zorlamak için projenizin derleme çıkış yollarını değiştirebilirsiniz.

### <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Tüm çözüm çıkışlarını ortak bir dizine yer alan

1. Çözümde bir projeye tıklayın.

2. Yeni **Project** Özellikler'e **tıklayın.**

3. Projenin türüne bağlı olarak, Derle sekmesine  veya Derleme sekmesine  tıklayın ve Çıkış yolunu çözümdeki tüm projeler için kullanmak üzere bir klasör olarak ayarlayın. 

4. Projenin proje dosyasını açın ve aşağıdaki özellik bildirimini ilk özellik grubuna ekleyin.

   ```xml
   <PropertyGroup>
     <!-- existing property declarations are here -->
     <UseCommonOutputDirectory>true</UseCommonOutputDirectory>
   </PropertyGroup>
   ```

   olarak ayarı, Visual Studio ve temel `UseCommonOutputDirectory` derleme altyapısına (MSBuild) birden çok proje çıktısını aynı klasöre koyarak söyler ve MSBuild normalde projeler diğer projelere bağımlı olduğunda olan kopyalama adımını `true` atlar.

5. Çözümde yer alan tüm projeler için 1-4 adımlarını yineler. Ortak çıkış dizinini kullanması gereken bazı olağanüstü projeleriniz varsa bazı projeleri atlayabilirsiniz.

### <a name="to-set-the-intermediate-output-directory-for-a-project-net-projects"></a>Bir projenin ara çıkış dizinini ayarlamak için (.NET projeleri)

1. Proje dosyasını açın.

1. Aşağıdaki özellik bildirimini ilk özellik grubuna ekleyin.

   ```xml
   <PropertyGroup>
     <!-- existing property declarations are here -->
     <IntermediateOutputPath>path</IntermediateOutputPath>
   <PropertyGroup>
   ```

   Yol, proje dosyasıyla görelidir veya mutlak bir yol kullanabilirsiniz. Proje adını yola koymak için , MSBuild kullanarak `$(MSBuildProjectName)` `$(MSBuildProjectDirectory)` başvurabilirsiniz. Kullanabileceğiniz diğer özellikler için [bkz. MSBuild iyi bilinen özellikler.](../msbuild/msbuild-reserved-and-well-known-properties.md)

1. Visual Studio proje klasörünün altında yine de obj klasörünü oluşturur, ancak boştur. Derleme işleminin bir parçası olarak silebilirsiniz. Bunu yapma yollarından biri, aşağıdaki komutu çalıştırmak için derleme sonrası olay eklemektir:

   ```cmd
   rd "$(ProjectDir)obj" /s /q
   ```

   Bkz. [Özel derleme olaylarını belirtme.](specifying-custom-build-events-in-visual-studio.md)

   MSBuild komut satırı ile derleme oluşturulduğunda obj klasörü oluşturulmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme sayfası, Project Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Genel Özellik sayfası (proje)](/cpp/build/reference/general-property-page-project)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
