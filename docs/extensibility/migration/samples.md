---
title: Visual Studio uzantılarını güncelleştirmek için ımageiyileştirici örneği
description: Visual Studio uzantısının Visual Studio 2022 önizleme ile çalışacak şekilde nasıl güncelleştireceğinizi öğrenmek için bir örneği izleyin.
ms.date: 06/08/2021
ms.topic: sample
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
monikerRange: vs-2022
ms.workload:
- vssdk
feedback_system: GitHub
ms.openlocfilehash: 4fbb0da22d8fc4b627a21ec3285450559be9210632949c71abe9850d638106a8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401024"
---
# <a name="imageoptimizer---update-a-visual-studio-extension-step-by-step"></a>ımageiyileştirici-adım adım Visual Studio uzantısı güncelleştirme

[!INCLUDE [preview-note](../includes/preview-note.md)]

bu kılavuz, örnek olay incelemesi olarak görüntü iyileştirici uzantısını kullanarak Visual Studio 2019 desteğini koruyarak Visual Studio 2022 desteği eklemek için gereken tüm adımları gösterir.  
Bu, her adımın git COMMIT bağlantıları ile ilgili kapsamlı bir kılavuz olması anlamına gelir, ancak son PR 'yi buradan görebilirsiniz: [https://github.com/madskristensen/ImageOptimizer/pull/46](https://github.com/madskristensen/ImageOptimizer/pull/46) .

Bu kılavuzun sonunda da [ek örneklere](#other-samples) ihtiyacımız var.

## <a name="step-1---modernize-the-project"></a>1. adım-projeyi modernleştirin

Bkz. [modernleştirin](update-visual-studio-extension.md#modernize-your-vsix-project).

[Git COMMIT e052465](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e052465f30e6bed37e6d76eac016047095e8e18b)

İlk olarak, VSıX ve birim testi projesini, projelerin Özellikler sayfasında .NET 4.7.2 'a çarptık:

   ![Framework sürüm darbesi](media/samples/framework-bump.png)

görüntü iyileştirici, bazı eski özel 14. * ve 15. * paketlerine başvurdu, bunun yerine tüm gerekli başvurularımızı birleştiren [ `Microsoft.VisualStudio.Sdk` NuGet paketini](https://www.nuget.org/packages/microsoft.visualstudio.sdk) yükleyeceğiz.

```Diff
-  <ItemGroup>
-    <PackageReference Include="Madskristensen.VisualStudio.SDK">
-      <Version>14.0.0-beta4</Version>
-    </PackageReference>
-    <PackageReference Include="Microsoft.VSSDK.BuildTools">
-      <Version>15.8.3247</Version>
-      <IncludeAssets>runtime; build; native; contentfiles; analyzers</IncludeAssets>
-      <PrivateAssets>all</PrivateAssets>
-    </PackageReference>
-  </ItemGroup>

+  <ItemGroup>
+    <PackageReference Include="Microsoft.VisualStudio.SDK">
+      <Version>16.9.31025.194</Version>
+    </PackageReference>
+  </ItemGroup>
```

Projenin oluşturulması başarılı olur ve birkaç iş parçacığı uyarısı alırız. `ctrl` `.` Eksik iş parçacığı değiştirme satırlarını eklemek için ve ' ye tıklayıp IntelliSense 'i kullanarak bu uyarıları düzeltireceğiz.

## <a name="step-2---refactor-source-code-into-a-shared-project"></a>2. adım-kaynak kodunu paylaşılan bir projeye yeniden düzenleme

Bkz. [Paylaşılan projeler](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting).

Visual Studio 2022 ' nin desteklenmesi, uzantının kaynak kodunu içeren, Visual Studio 2019 ve Visual Studio 2022 vsıx projeleri arasında paylaşılacak yeni bir paylaşılan proje eklenmesini gerektirir.

1. Çözümünüze yeni bir paylaşılan proje ekleyin

   [Git COMMIT abf249d](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/abf249d5a4bed9010652f3f3fc4753c7c771c892)

   ![Paylaşılan proje Ekle](media/samples/add-shared-project.png)

1. VSıX projenize paylaşılan projeye bir başvuru ekleyin.

   [Git COMMIT e8e941e](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e8e941e5a5482cc15f5b9e7e4f1727f5cab5b12c)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Paylaşılan proje başvurusu Ekle" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Kaynak kod dosyalarınızı (CS, XAML, resx) aşağıdakiler **hariç** yeni paylaşılan projeye taşıyın:
    - `source.extension.vsixmanifest`
    - Uzantı meta verileri dosyaları (simgeler, lisanslar, sürüm notları vb.)
    - VSCT dosyaları
    - Bağlı dosyalar
    - VSıX 'e dahil olması gereken dış araçlar veya kitaplıklar

   [Git COMMIT f31f051](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/f31f0515305623988f2c355ed3bf5952fc8f1d9e)

   ![Dosyaları paylaşılan projeye taşı](media/samples/move-to-shared-project.png)

1. Şimdi tüm meta verileri, VSCT dosyalarını, bağlantılı dosyaları ve dış araçları/kitaplıkları paylaşılan bir konuma taşıyın ve VSıX projesine bağlı öğeler olarak geri ekleyin.  ' İ kaldırmayın `source.extension.vsixmanifest` .

   [Git COMMIT 73ba920-dosyalar taşınıyor](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/73ba920b7db0bdb7c4d66aa9bc932c268efd49cb)

   [Git COMMIT d5e36b2-dış araçlar/kitaplıklar ekleme](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d5e36b2d047290d38ffc977511510bc03e257f13)

   1. Bu proje için uzantı simgesini, VSCT dosyasını ve dış araçları yeni klasörünüze taşımamız gerekiyor `ImageOptimizer\Resources` . Onları paylaşılan klasöre kopyalayın ve VSıX projesinden kaldırın.
   1. Bunları bağlantılı öğeler olarak geri eklediniz ve öğeler zaten bağlı öğeler oldukları gibi kalabilir (örneğin, lisans).
   1. Derleme eyleminin ve diğer özelliklerin, eklenen bağlı dosyalarda her birini seçerek ve Özellikler araç penceresini işaretleyerek doğru şekilde ayarlandığını doğrulayın. Projemiz için aşağıdakileri ayarlaması gerekiyordu:
       - `icon.png`Derleme EYLEMINI VSIX 'e `Content` Ekle olarak ayarlayın ve`true`
       - `ImageOptimizer.vsct`Derleme eylemini öğesine ayarla `VSCTComplile` ve VSIX 'e Ekle`false`
       - İçindeki dosyaların tüm yapı eylemini `Resources\Tools` `Content` ve VSIX 'e Ekle dahil olarak belirleyin `true`

           ![VSıX projesine bağlı dosyalar ekleme](media/samples/add-linked-files.png)

       - Buna ek olarak,, bu `ImageOptimizer.cs` `ImageOptimizer.vsct` bağımlılığı csproj dosyasına el ile eklememiz gerekir:

          ```diff  
          - <Content Include="..\SharedFiles\ImageOptimizer.vsct">
          -   <Link>ImageOptimizer.vsct</Link>
          - </Content>
          - <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          -   <Link>ImageOptimizer.cs</Link>
          - </Compile>

          + <VSCTCompile Include="..\SharedFiles\ImageOptimizer.vsct">
          +   <ResourceName>Menus.ctmenu</ResourceName>
          +   <Generator>VsctGenerator</Generator>
          +   <LastGenOutput>..\SharedFiles\ImageOptimizer.cs</LastGenOutput>
          + </VSCTCompile>
          + <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          +   <AutoGen>True</AutoGen>
          +   <DesignTime>True</DesignTime>
          +   <DependentUpon>..\SharedFiles\ImageOptimizer.vsct</DependentUpon>
          + </Compile>
          ```

       - Özellikler araç penceresi belirli bir yapı eylemini ayarlamanıza engel olursa, csproj 'u yukarıda yapılan şekilde el ile değiştirebilir ve derleme eylemini gerektiği şekilde ayarlayabilirsiniz.

1. Değişikliklerinizi doğrulamak ve hata/sorunları gidermek için projenizi derleyin. Yaygın sorunlar için [sık sorulan sorular](update-visual-studio-extension.md#q--a) bölümüne bakın.

## <a name="step-3---add-a-visual-studio-2022-vsix-project"></a>3. adım-Visual Studio 2022 vsıx projesi ekleme

bkz. [Add Visual Studio 2022 target](update-visual-studio-extension.md#add-a-visual-studio-2022-target).

1. Çözümünüze yeni bir VSıX projesi ekleyin.
1. Yeni projede aşağıdakiler hariç tüm ek kaynak kodlarını kaldır `source.extension.vsixmanifest.`

   ![Yeni bir VSıX projesi oluştur](media/samples/visual-studio-2022-vsix-initial.png)

1. Paylaşılan projenize bir başvuru ekleyin.

   [Git COMMIT dd49cb2](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/dd49cb227b52c46206bf4be5c25790ac0377568d)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Paylaşılan projeye başvuru Ekle" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Visual Studio 2019 vsıx projenizden bağlantılı dosyaları ekleyin ve "derleme eylemi" ve "vsıx içinde içer" özelliklerinin eşleştiğini doğrulayın. dosyanızı da kopyalayın `source.extension.vsixmanifest` , daha sonra Visual Studio 2022 ' i destekleyecek şekilde değişiklik yapacağız.

   [Git tamamlama 98c43ee](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/98c43ee6fbe912c38a1275542c44c65e11d7dbd9)

   ![VSıX projesine bağlı dosyalar ekleme](media/samples/visual-studio-2022-add-linked-files.png)

1. Denenen bir derleme, için bir başvuru eksik olduğunu gösterir `System.Windows.Forms` . bunu Visual Studio 2022 projenize eklemeniz ve yeniden oluşturmanız yeterlidir.

   [Git COMMIT de71ccd](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/de71ccd9baff703aa6679392ad41a2cfe7bd7d72)

   ```Diff
   + <Reference Include="System.Windows.Forms" />
   ```

1. `Microsoft.VisualStudio.SDK` `Microsoft.VSSDK.BuildTools` Visual Studio 2022 sürümlerine yükseltin ve paket başvuruları yapın.

   [Git COMMIT d581fc3](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d581fc3c954974124dc7e31e5ecc85f78f7828ab)

   > [!NOTE]
   > Bunlar, bu kılavuz oluşturulduğunda kullanılabilen en son sürümlerdir. En son sürümleri kullanıma almanız önerilir.
   >
   > ```diff
   > -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
   > +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview-1-31216-1036" />
   > -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
   > +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-Visual Studio 2022-g3f11f5ab" />
   > ```

1. `source.extension.vsixmanifest`dosyanızı Visual Studio 2022 hedeflemesini yansıtacak şekilde düzenleyin.

   [Git COMMIT 9d393c7](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/9d393c708c04ac4af48d1eb9ce3da4470db5d5cc)
   1. `<InstallationTarget>`etiketi Visual Studio 2022 yansıtacak şekilde ayarlayın ve amd64 yükünü belirtin:

      ```xml
      <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
          <ProductArchitecture>amd64</ProductArchitecture>
      </InstallationTarget>
      ```

   1. önkoşulları yalnızca Visual Studio 2022 ve üstünü içerecek şekilde değiştirin:

      ```Diff
      - <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,)" DisplayName="Visual Studio core editor" />
      + <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,)" DisplayName="Visual Studio core editor" />
      ```

Tebrikler!

bu şekilde, derleme artık Visual Studio 2019 ve Visual Studio 2022 sanal parçalar üretir.

## <a name="other-samples"></a>Diğer örnekler

- [Progüç araçları](https://github.com/microsoft/VS-PPT/pull/244)
  - PeekF1
    - Seçili sınıf/nesne hakkındaki yardım bilgileriyle bir Web tarayıcısına göz atmayı sağlar.
  - Fixmixedsekmeleri
    - Belgelerinizi tarar ve sekmeleri boşluklarla veya tam tersi şekilde değiştirir

## <a name="next-steps"></a>Sonraki adımlar

Bu [Başlangıç-bitiş kılavuzunu](update-visual-studio-extension.md)okuyarak uzantınızı güncelleştirmeye hazırlanın.
