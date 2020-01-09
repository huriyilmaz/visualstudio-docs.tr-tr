---
title: GenerateBootstrapper görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 660f63f68435f4c4eba8d1c3dfb2438541da4841
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589298"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper görevi
Bir uygulamayı ve önkoşullarını tespit etmek, indirmek ve yüklemek için otomatikleştirilmiş bir yol sağlar. Bir uygulamayı oluşturan tüm bileşenlerin ayrı yükleyicilerini tümleştiren tek bir yükleyici olarak görev yapar.

## <a name="task-parameters"></a>Görev parametreleri
Aşağıda `GenerateBootstrapper` görevinin parametreleri açıklanır.

- `ApplicationFile`

   İsteğe bağlı `String` parametresi.

   Tüm Önkoşullar yüklendikten sonra önyükleyicinin uygulamayı yüklemeye başlamak için kullanacağı dosyayı belirtir. `BootstrapperItems` ne de `ApplicationFile` parametresi belirtilmemişse, derleme hatası ortaya kalır.

- `ApplicationName`

   İsteğe bağlı `String` parametresi.

   Önyükleyici tarafından yüklenecek uygulamanın adını belirtir. Bu ad, önyükleyicinin yükleme sırasında kullandığı kullanıcı arabiriminde görüntülenir.

- `ApplicationRequiresElevation`

   İsteğe bağlı `Boolean` parametresi.

   `true`, bileşen hedef bilgisayara yüklendiğinde yükseltilmiş izinlerle çalışır.

- `ApplicationUrl`

   İsteğe bağlı `String` parametresi.

   Uygulamanın yükleyicisini barındıran Web konumunu belirtir.

- `BootstrapperComponentFiles`

   İsteğe bağlı `String[]` çıkış parametresi.

   Önyükleyici paket dosyalarının oluşturulan konumunu belirtir.

- `BootstrapperItems`

   İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.

   Önyükleyici içine derlenecek ürünleri belirtir. Bu parametreye geçirilen öğelerin aşağıdaki sözdizimi olmalıdır:

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   `Include` öznitelik, yüklenmesi gereken bir önkoşulun adını temsil eder. `ProductName` öğesi meta verileri isteğe bağlıdır ve paket bulunamazsa derleme altyapısı tarafından Kullanıcı dostu bir ad olarak kullanılır. Hiçbir `ApplicationFile` belirtilmediği takdirde bu öğeler giriş parametreleri [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] gerekli değildir. Uygulamanız için yüklenmesi gereken her önkoşul için bir öğe eklemelisiniz.

   `BootstrapperItems` ne de `ApplicationFile` parametresi belirtilmemişse, derleme hatası ortaya kalır.

- `BootstrapperKeyFile`

   İsteğe bağlı `String` çıkış parametresi.

   *Setup. exe* ' nin oluşturulan konumunu belirtir

- `ComponentsLocation`

   İsteğe bağlı `String` parametresi.

   Önyükleyici için yüklenecek yükleme önkoşullarını aramak için bir konum belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:

  - `HomeSite`: ön koşulun bileşen satıcısı tarafından barındırıldığını gösterir.

  - `Relative`: ön koşulun uygulamanın aynı konumda olduğunu gösterir.

  - `Absolute`: tüm bileşenlerin merkezi bir URL 'de bulunduğunu gösterir. Bu değer, `ComponentsUrl` giriş parametresiyle birlikte kullanılmalıdır.

    `ComponentsLocation` belirtilmemişse, varsayılan olarak `HomeSite` kullanılır.

- `ComponentsUrl`

   İsteğe bağlı `String` parametresi.

   Yükleme önkoşullarını içeren URL 'YI belirtir.

- `CopyComponents`

   İsteğe bağlı `Boolean` parametresi.

   `true`, önyükleyici tüm çıktı dosyalarını `OutputPath` parametresinde belirtilen yola kopyalar. `BootstrapperComponentFiles` parametresinin değerlerinin hepsi bu yolu temel almalıdır. `false`, dosyalar kopyalanmaz ve `BootstrapperComponentFiles` değerleri `Path` parametresinin değerini temel alır.  Bu parametrenin varsayılan değeri `true`.

- `Culture`

   İsteğe bağlı `String` parametresi.

   Önyükleyici Kullanıcı arabirimi ve yükleme önkoşulları için kullanılacak kültürü belirtir. Belirtilen kültür kullanılamıyorsa, görev `FallbackCulture` parametresinin değerini kullanır.

- `FallbackCulture`

   İsteğe bağlı `String` parametresi.

   Önyükleyici Kullanıcı arabirimi ve yükleme önkoşulları için kullanılacak ikincil kültürü belirtir.

- `OutputPath`

   İsteğe bağlı `String` parametresi.

   *Setup. exe* ' nin ve tüm paket dosyalarının kopyalanacağı konumu belirtir.

- `Path`

   İsteğe bağlı `String` parametresi.

   Kullanılabilir tüm önkoşul paketlerinin konumunu belirtir.

- `SupportUrl`

   İsteğe bağlı `String` parametresi.

   Önyükleyici yüklemesi başarısız olursa, sağlanacak URL 'YI belirtir.

- `Validate`

   İsteğe bağlı `Boolean` parametresi.

   `true`, önyükleyici belirtilen giriş önyükleyici öğelerinde XSD doğrulaması gerçekleştirir. Bu parametrenin varsayılan değeri `false`.

## <a name="remarks"></a>Açıklamalar
Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek
Aşağıdaki örnek, önkoşul olarak yüklenen .NET Framework 2,0 ' i yüklemiş olması gereken bir uygulamayı yüklemek için `GenerateBootstrapper` görevini kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">
            <ProductName>Microsoft .NET Framework 2.0</ProductName>
        </BootstrapperFile>
    </ItemGroup>

    <Target Name="BuildBootstrapper">
        <GenerateBootstrapper
            ApplicationFile="WindowsApplication1.application"
            ApplicationName="WindowsApplication1"
            ApplicationUrl="http://mycomputer"
            BootstrapperItems="@(BootstrapperFile)"
            OutputPath="C:\output" />
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
