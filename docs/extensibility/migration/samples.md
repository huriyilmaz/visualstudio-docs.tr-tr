---
title: Yeni uzantılarını güncelleştirmek için ImageOptimizer Visual Studio örneği
description: Visual Studio uzantısını Visual Studio 2022 Preview ile çalışacak şekilde güncelleştirme hakkında bilgi edinmek için bir örneği izleyin.
ms.date: 06/08/2021
ms.topic: sample
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 12bbc159884c16ea89849e5c97a4b87292f7089d
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602226"
---
# <a name="imageoptimizer---update-a-visual-studio-extension-step-by-step"></a>ImageOptimizer - Bir Visual Studio uzantısını adım adım güncelleştirme

[!INCLUDE [preview-note](../includes/preview-note.md)]

Bu kılavuzda, örnek olay incelemesinde Görüntü İyileştirici uzantısını kullanarak Visual Studio 2019 Visual Studio 2022 desteği eklemek için gereken tüm adımlar açıklanacak.  
Bu, her bir adıma git işleme bağlantıları içeren kapsamlı bir kılavuz olması gerekir, ancak burada son pr'yi görmekte serbestsiniz: [https://github.com/madskristensen/ImageOptimizer/pull/46](https://github.com/madskristensen/ImageOptimizer/pull/46) .

Bu [kılavuzun sonunda](#other-samples) ek örnekler de vardır.

## <a name="step-1---modernize-the-project"></a>1. Adım - Projeyi modernleştirme

Bkz. [Projeyi modernleştirme.](update-visual-studio-extension.md#modernize-your-vsix-project)

[git commit e052465](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e052465f30e6bed37e6d76eac016047095e8e18b)

İlk olarak, projelerin özellikler sayfasının altında VSIX ve birim testi projesini .NET 4.7.2'ye iletiriz:

   ![Framework sürümüne yapılan tümsekler](media/samples/framework-bump.png)

Görüntü İyileştirici bazı eski özel 14.* ve 15.* paketlerine başvurmuş, bunun yerine tüm gerekli başvurularımızı birleştirici [ `Microsoft.VisualStudio.Sdk` NuGet](https://www.nuget.org/packages/microsoft.visualstudio.sdk) paketini yükleyeceğiz.

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

Proje başarılı olur ve birkaç iş parçacığı uyarısı alırsınız. Eksik iş parçacığı değiştirme çizgilerini `ctrl` eklemek `.` için IntelliSense'e tıklayarak ve kullanarak bu uyarıları düzelteceğiz.

## <a name="step-2---refactor-source-code-into-a-shared-project"></a>2. Adım: Kaynak kodunu paylaşılan bir projede yeniden düzenleme

Bkz. [Paylaşılan projeler.](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting)

Visual Studio 2022 desteği için, uzantının kaynak kodunu içeren ve Visual Studio 2019 ile Visual Studio 2022 VSIX projeleri arasında paylaşılacak yeni bir paylaşılan proje eklemek gerekir.

1. Çözümünüze yeni bir paylaşılan proje ekleme

   [git commit abf249d](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/abf249d5a4bed9010652f3f3fc4753c7c771c892)

   ![Paylaşılan proje ekleme](media/samples/add-shared-project.png)

1. VSIX projenize paylaşılan projeye bir başvuru ekleyin.

   [git commit e8e941e](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e8e941e5a5482cc15f5b9e7e4f1727f5cab5b12c)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Paylaşılan proje başvurusu ekleme" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Kaynak kod dosyalarınızı (cs, xaml, resx) aşağıdakiler dışında yeni paylaşılan **projeye** taşıma:
    - `source.extension.vsixmanifest`
    - Uzantı meta veri dosyaları (simgeler, lisanslar, sürüm notları vb.)
    - VSCT dosyaları
    - Bağlantılı dosyalar
    - VSIX'e dahil olması gereken dış araçlar veya kitaplıklar

   [git commit f31f051](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/f31f0515305623988f2c355ed3bf5952fc8f1d9e)

   ![Dosyaları paylaşılan projeye taşıma](media/samples/move-to-shared-project.png)

1. Şimdi tüm meta verileri, VSCT dosyalarını, bağlı dosyaları ve dış araçları/kitaplıkları paylaşılan bir konuma taşıma ve bunları VSIX projesine bağlantılı öğeler olarak geri ekleme. **kaldırmayın.** `source.extension.vsixmanifest`

   [git commit 73ba920 - Dosyaları taşıma](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/73ba920b7db0bdb7c4d66aa9bc932c268efd49cb)

   [git commit d5e36b2 - Dış araçlar/kitaplıklar ekleme](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d5e36b2d047290d38ffc977511510bc03e257f13)

   1. Bu proje için uzantı simgesini, VSCT dosyasını ve dış araçları yeni klasöre taşımamız `ImageOptimizer\Resources` gerekir. Bunları paylaşılan klasöre kopyalayın ve VSIX projesinden kaldırın.
   1. Bunları bağlantılı öğeler olarak geri ekledik ve öğeler zaten bağlantılı ise olduğu gibi kalabilir (örneğin, lisans).
   1. Her birini seçerek ve özellikler araç penceresini kontrol ederek Derleme Eylemi ve diğer özelliklerin eklenen bağlı dosyalarda doğru şekilde ayarlandıktan emin olun. Projemiz için şunları ayarlamamız gerekirdi:
       - Derleme `icon.png` Eylem'i olarak ayarlayın `Content` ve VSIX'te Dahil Edin olarak işaretlendi `true`
       - Derleme `ImageOptimizer.vsct` Eylemlerini olarak ayarlayın `VSCTComplile` ve VSIX'e dahil edin `false`
       - altındaki dosyaların tüm Derleme Eylemlerini olarak ayarlayın `Resources\Tools` ve `Content` VSIX'te Dahil Edin olarak işaretlendi `true`

           ![VSIX projesine bağlı dosyalar ekleme](media/samples/add-linked-files.png)

       - Ayrıca, `ImageOptimizer.cs` bir `ImageOptimizer.vsct` bağımlılığıdır, bunun için bu bağımlılığı csproj dosyasına el ile eklememiz gerekir:

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

       - Özellikler araç penceresi belirli bir Derleme Eylemi ayarlamayı önlese de csproj'ı yukarıda olduğu gibi el ile değiştirebilir ve Derleme Eylemlerini gereken şekilde ayarlayabilirsiniz.

1. Değişikliklerinizi doğrulamak ve tüm hata/sorunları düzeltmek için projenizi derleme. Yaygın sorunlar [için Sık Sorulan Sorular](update-visual-studio-extension.md#q--a) bölümüne bakın.

## <a name="step-3---add-a-visual-studio-2022-vsix-project"></a>3. Adım - Visual Studio 2022 VSIX projesi ekleme

Bkz. [Visual Studio 2022 hedefi ekleme.](update-visual-studio-extension.md#add-a-visual-studio-2022-target)

1. Çözümünüze yeni bir VSIX projesi ekleyin.
1. yeni projesinde aşağıdakiler dışında tüm ek kaynak kodunu kaldırın: `source.extension.vsixmanifest.`

   ![Yeni VSIX projesi oluşturma](media/samples/visual-studio-2022-vsix-initial.png)

1. Paylaşılan projenize bir başvuru ekleyin.

   [git commit dd49cb2](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/dd49cb227b52c46206bf4be5c25790ac0377568d)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Paylaşılan projeye başvuru ekleme" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Visual Studio 2019 VSIX projenize bağlı dosyaları ekleyin ve "Derleme Eylemi" ve "VSIX'e Ekle" özelliklerinin eş olduğunu onaylar. Ayrıca dosyanızı `source.extension.vsixmanifest` kopyalayıp daha sonra 2022'de Visual Studio değiştireceğiz.

   [git commit 98c43ee](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/98c43ee6fbe912c38a1275542c44c65e11d7dbd9)

   ![VSIX projesine Bağlı dosyalar ekleme](media/samples/visual-studio-2022-add-linked-files.png)

1. Denenen derleme, için bir başvuru eksik olduğunu `System.Windows.Forms` gösterir. Bunu Visual Studio 2022 projemize eklemeniz ve yeniden oluşturmanız gerekir.

   [git commit de71ccd](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/de71ccd9baff703aa6679392ad41a2cfe7bd7d72)

   ```Diff
   + <Reference Include="System.Windows.Forms" />
   ```

1. `Microsoft.VisualStudio.SDK`Visual Studio `Microsoft.VSSDK.BuildTools` 2022 sürümlerine yükseltme ve paket başvuruları.

   [git commit d581fc3](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d581fc3c954974124dc7e31e5ecc85f78f7828ab)

   > [!NOTE]
   > Bunlar, bu kılavuz oluşturulduğunda kullanılabilen en son sürümlerdir. En son sürümlerin kullanılabilir olduğu önerilir.
   >
   > ```diff
   > -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
   > +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview-1-31216-1036" />
   > -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
   > +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-Visual Studio 2022-g3f11f5ab" />
   > ```

1. Dosyanızı `source.extension.vsixmanifest` 2022'Visual Studio yansıtacak şekilde düzenleyin.

   [git commit 9d393c7](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/9d393c708c04ac4af48d1eb9ce3da4470db5d5cc)
   1. Etiketi `<InstallationTarget>` 2022'Visual Studio yansıtacak şekilde ayarlayın ve amd64 yükünü işaret edin:

      ```xml
      <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
          <ProductArchitecture>amd64</ProductArchitecture>
      </InstallationTarget>
      ```

   1. Önkoşul'Visual Studio 2022 ve üzerini içerecek şekilde değiştirme:

      ```Diff
      - <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,)" DisplayName="Visual Studio core editor" />
      + <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,)" DisplayName="Visual Studio core editor" />
      ```

Artık bitti!

Bu nedenle, artık bina 2019 Visual Studio 2022 VSIXes Visual Studio üretir.

## <a name="other-samples"></a>Diğer örnekler

- [ProPower Araçları](https://github.com/microsoft/VS-PPT/pull/244)
  - PeekF1
    - Seçilen sınıf/nesne hakkında yardım bilgileriyle bir web tarayıcısına göz atmanıza izin verir.
  - FixMixedTabs
    - Belgelerinizi tarar ve sekmeleri boşluklarla değiştirir veya tam tersi

## <a name="next-steps"></a>Sonraki adımlar

Bu başlangıç ve bitiş kılavuzunu [okuyarak uzantınızı güncelleştirmeye hazırlanma.](update-visual-studio-extension.md)
