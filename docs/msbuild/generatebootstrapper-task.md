---
title: GenerateBootstrapper Görev | Microsoft Docs
description: Bir uygulamayı MSBuild ve önkoşullarını algılamanın, indirmenin ve yüklemenin otomatik bir yolu olarak GenerateBootstrapper görevini kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b198b62a7931d2bb88e3194cc8f159d67602c98d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069257"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper görevi

Bir uygulamayı ve bunun önkoşullarını algılamak, indirmek ve yüklemek için otomatik bir yol sağlar. Uygulamanın tüm bileşenleri için ayrı yükleyicileri tümleştiren tek bir yükleyici olarak görev yapıyor.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıda görevin parametreleri açık `GenerateBootstrapper` almaktadır.

- `ApplicationFile`

   İsteğe `String` bağlı parametre.

   Önkoşullar yüklendikten sonra önyükleyicinin uygulama yüklemesini başlatmaya başlamak için kullanabileceği dosyayı belirtir. ne parametresi ne de parametresi `BootstrapperItems` belirtilmezse bir `ApplicationFile` derleme hatasıyla sonuçlandır.

- `ApplicationName`

   İsteğe `String` bağlı parametre.

   Önyükleyicinin yükleyecek olduğu uygulamanın adını belirtir. Bu ad, önyükleyicinin yükleme sırasında kullandığı kullanıcı arabiriminde görünür.

- `ApplicationRequiresElevation`

   İsteğe `Boolean` bağlı parametre.

   ise, `true` bileşen hedef bilgisayara yüklenirken yükseltilmiş izinlerle çalışır.

- `ApplicationUrl`

   İsteğe `String` bağlı parametre.

   Uygulamanın yükleyicisini barındıran Web konumunu belirtir.

- `BootstrapperComponentFiles`

   İsteğe `String[]` bağlı çıkış parametresi.

   Önyükleyici paket dosyalarının yerleşik konumunu belirtir.

- `BootstrapperItems`

   İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.

   Önyükleyicide derlemek için ürünleri belirtir. Bu parametreye geçirilen öğelerin söz dizimi aşağıdaki olmalıdır:

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   özniteliği, `Include` yüklü olması gereken bir önkolun adını temsil eder. Öğe meta verileri isteğe bağlıdır ve paket bulunamazsa derleme altyapısı tarafından `ProductName` kolay bir ad olarak kullanılır. Bu öğeler, giriş MSBuild belirtilmezse gerekli `ApplicationFile` değildir. Uygulamanıza yüklenmiş olması gereken her önkoşul için bir öğe dahil etmek gerekir.

   ne parametresi ne de parametresi `BootstrapperItems` belirtilmezse bir `ApplicationFile` derleme hatasıyla sonuçlandır.

- `BootstrapperKeyFile`

   İsteğe `String` bağlı çıkış parametresi.

   Uygulamanın yerleşik konumunu *setup.exe*

- `ComponentsLocation`

   İsteğe `String` bağlı parametre.

   Önyükleyicinin yükleme önkoşullarını araması için bir konum belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:

  - `HomeSite`: Önkoşulların bileşen satıcısı tarafından barındırıldı olduğunu gösterir.

  - `Relative`: Önkolun uygulamanın aynı konumda olduğunu gösterir.

  - `Absolute`: Tüm bileşenlerin merkezi bir URL'de bulun olacağını gösterir. Bu değer, giriş parametresiyle birlikte `ComponentsUrl` kullanılmalıdır.

    `ComponentsLocation`belirtilmezse, `HomeSite` varsayılan olarak kullanılır.

- `ComponentsUrl`

   İsteğe `String` bağlı parametre.

   Yükleme önkoşullarını içeren URL'yi belirtir.

- `CopyComponents`

   İsteğe `Boolean` bağlı parametre.

   ise, `true` önyükleyici tüm çıkış dosyalarını parametresinde belirtilen yola `OutputPath` kopyalar. Parametre değerlerinin `BootstrapperComponentFiles` hepsi bu yolu temel alarak olmalıdır. `false`ise, dosyalar kopyalanmaz ve `BootstrapperComponentFiles` değerler parametresinin değerine `Path` dayalıdır.  Bu parametrenin varsayılan değeri: `true` .

- `Culture`

   İsteğe `String` bağlı parametre.

   Önyükleyici kullanıcı arabirimi ve yükleme önkoşulları için kullanmak üzere kültürü belirtir. Belirtilen kültür kullanılamıyorsa, görev parametresinin değerini `FallbackCulture` kullanır.

- `FallbackCulture`

   İsteğe `String` bağlı parametre.

   Önyükleyici kullanıcı arabirimi ve yükleme önkoşulları için kullanmak üzere ikincil kültürü belirtir.

- `OutputPath`

   İsteğe `String` bağlı parametre.

   Tüm paket dosyalarını *setup.exe* konumunu belirtir.

- `Path`

   İsteğe `String` bağlı parametre.

   Kullanılabilir tüm önkoşul paketlerinin konumunu belirtir.

- `SupportUrl`

   İsteğe `String` bağlı parametre.

   Önyükleyici yüklemesi başarısız olursa sağ url'yi belirtir.

- `Validate`

   İsteğe `Boolean` bağlı parametre.

   ise, `true` önyükleyici belirtilen giriş önyükleyici öğelerinde XSD doğrulaması gerçekleştirir. Bu parametrenin varsayılan değeri: `false` .

## <a name="remarks"></a>Açıklamalar

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, `GenerateBootstrapper` önkoşul olarak .NET Framework 2.0'ın yüklü olması gereken bir uygulamayı yüklemek için görevini kullanır.

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
